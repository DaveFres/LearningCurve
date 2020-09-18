# Thoughts

### Bluebird vs async/await nodejs

[V8 promises implementation is written in JavaScript](https://github.com/v8/v8/blob/5.7.228/src/js/promise.js) not C. All JavaScript \(including V8's own\) is compiled to native code. Additionally user written JavaScript is optimized, if possible \(and worth it\), before compiled to native code. Promises implementation is something that would not benefit much or at all from being written in C, in fact it would only make it slower because all you are doing is manipulating JavaScript objects and communication.

The V8 implementation simply isn't as optimized as bluebird, it for instances [allocates arrays for promises' handlers](https://github.com/v8/v8-git-mirror/blob/4.3.66/src/promise.js#L79). This takes a lot of memory when each promise also has to allocate a couple of arrays \(The benchmark creates overall 80k promises so that's 160k unused arrays allocated\). In reality 99.99% of use cases never branch a promise more than once so optimizing for this common case gains huge memory usage improvements.

Even if V8 implemented the same optimizations as bluebird, it would still be hindered by specification. The benchmark has to use `new Promise` \(an anti-pattern in bluebird\) as there is no other way to create a root promise in ES6. `new Promise` is an extremely slow way of creating a promise, first the executor function allocates a closure, secondly it is passed 2 separate closures as arguments. That's 3 closures allocated per promise but a closure is already a more expensive object than an optimized promise.

Bluebird can use `promisify` which enables lots of optimizations and is a much more convenient way of consuming callback APIs and it enables conversion of whole modules into promise based modules in one line \(`promisifyAll(require('redis'));`\).

Source: [https://softwareengineering.stackexchange.com/questions/278778/why-are-native-es6-promises-slower-and-more-memory-intensive-than-bluebird](https://softwareengineering.stackexchange.com/questions/278778/why-are-native-es6-promises-slower-and-more-memory-intensive-than-bluebird)




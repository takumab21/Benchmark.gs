# Benchmark.gs
Benchmark.js on Google Apps Script

# Library's Script ID (Rhino / V8)
`1KXGd2vVC3tf565J1jkcnmcXYGfchdBim08HWRtYCK7kDSy7Mh1pCX8A6`

It is same ID to run each runtime (Rhino/V8).
Because running with which runtime depends on the setting of your GAS project.

# Sample
```js
function sample() {
    var suite = new Benchmark.Suite;

    // add tests
    suite.add('RegExp#test', function() {
            /o/.test('Hello World!');
        })
        .add('String#indexOf', function() {
            'Hello World!'.indexOf('o') > -1;
        })
        .add('String#match', function() {
            !!'Hello World!'.match(/o/);
        })
        // add listeners
        .on('cycle', function(event) {
            Logger.log(String(event.target));
        })
        .on('complete', function() {
            Logger.log('Fastest is ' + this.filter('fastest').map('name'));
        })
        // run async
        .run({
            'async': true
        });
}
```

# Notice
The performance of GAS is unstable. You may get different result.

# License
This repository is redistribution of `Benchmark.js`, `lodash.js` and `platform.js`.
So please read each LICENSE:

- [`Benchmark.js`](https://github.com/bestiejs/benchmark.js/blob/master/LICENSE)
- [`lodash.js`](https://raw.githubusercontent.com/lodash/lodash/4.17.15-npm/LICENSE)
- [`platform.js`](https://github.com/bestiejs/platform.js/blob/master/LICENSE)

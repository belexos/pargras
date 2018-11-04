Pargras
=======

`Pargras` is a minimalistic helper around function arguments for Node.js and the Browser. `Pargras` has a fluent interface and supports adding, removing and altering arguments before applying them to a function.


Getting started
---------------

### Node.js

Install `pargras` using npm.

```shell
npm install pargras --save
```

Then require it into any module.

```js
const Pargras = require('pargras');
```

### Browser
You can download the latest release from the repository
* [`pargras.js`](https://github.com/belexos/pargras/blob/master/pargras.js) unminified, including comments
* [`pargras.min.js`](https://github.com/belexos/pargras/blob/master/pargras.min.js) minified version

Use a script tag to directly add `Pargras` to the global scope.

```html
<script src="pargras.min.js"></script>
```


Usage
-----
```js
function specialMin()
{
    // Instantiate the arguments helper.
    const args = new Pargras(arguments);

    // Remove first and last parameter, then call Math.min() with the resulting arguments.
    var min = args.shift().pop().applyTo(Math.min);
}

specialMin(0, 2, 3, 4, 1);
// -> 2
```


Examples
--------

### Return the function arguments as an array.

```js
function afunc()
{
    // Instantiate the arguments helper.
    const args = new Pargras(arguments);

    // Return the function arguments as an array.
    return args.array();
}

afunc(0, 1, "two", true);
// -> [ 0, 1, "two", true ]
```

### Return the number of arguments passed to a function.

```js
function afunc()
{
    // Instantiate the arguments helper.
    const args = new Pargras(arguments);

    // Return the number of arguments passed to function.
    return args.length();
}

afunc(0, 1, "two", true);
// -> 4
```

### Alter an argument value.

```js
function afunc()
{
    // Instantiate the arguments helper.
    const args = new Pargras(arguments);

    // Check value.
    args.get(1);
    // -> "banana"

    // Alter second argument value.
    args.set(1, 'altered');

    // Check value again.
    args.get(1);
    // -> "altered"

    // Return sorted arguments.
    return args.array().sort();
}

afunc("peach", "banana", "apple");
// -> [ "altered", "apple", "peach" ]
```

### Alter arguments and apply them to another function.

```js
function afunc()
{
    // Instantiate the arguments helper.
    const args = new Pargras(arguments);

    // Alter arguments.
    // a) Remove first argument.
    // b) Remove last argument.
    // c) Prepend argument 'one'.
    // d) Append argument 'four'.
    args.shift().pop().unshift('one').push('four');

    // Apply to console.log().
    args.applyTo(console.log);
}

afunc(1, 2, 3, 4);
// -> [ "one", 2, 3, "four" ]
```


More examples
-------------
Please refer to the [test spec](https://github.com/belexos/pargras/blob/master/spec/PargrasSpec.js) for more examples.


Testing
-------
We are using [Jasmine testing framework](https://jasmine.github.io/index.html) and [Istanbul test coverage framework](https://istanbul.js.org/).

* Clone or download the repository.
* Change into project directory.
* Use `npm install` to install all development dependencies.
* Use `npm test` to run the tests. 
* The output should display successful execution results and a code coverage map.


Build
-----
* Clone or download the repository.
* Change into project directory.
* Use `grunt` in project directory to build `pargras.min.js` from `pargras.js`.


Contribution
------------
Please use [Github issues](https://github.com/belexos/pargras/issues) for requests.

Pull requests are welcome.


Issues
------
We use GitHub issues to track bugs. Please ensure your bug description is clear and has sufficient instructions to be able to reproduce the issue.

The absolute best way to report a bug is to submit a pull request including a new failing test which describes the bug. When the bug is fixed, your pull request can then be merged.

The next best way to report a bug is to provide a reduced test case on jsFiddle or jsBin or produce exact code inline in the issue which will reproduce the bug.


Support
-------
* Send us an email: [support@belexos.com](mailto:support@belexos.com)
* Follow us on Twitter: [@belexos](http://twitter.com/belexos)


Changelog
---------
v1.0.0
* Initial public release


License
-------
Copyright (c) 2016-present, Belexos GmbH. `Pargras` is licensed under the [MIT License](https://github.com/belexos/pargras/blob/master/LICENSE).

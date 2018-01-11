[![Build Status](https://travis-ci.org/on3iro/functionstein.svg?branch=master)](https://travis-ci.org/on3iro/functionstein)
[![Coverage Status](https://coveralls.io/repos/github/on3iro/functionstein/badge.svg?branch=master)](https://coveralls.io/github/on3iro/functionstein?branch=master)
[![Maintainability](https://api.codeclimate.com/v1/badges/704d27c79031519e33cb/maintainability)](https://codeclimate.com/github/on3iro/functionstein/maintainability)
[![npm version](https://badge.fury.io/js/functionstein.svg)](https://badge.fury.io/js/functionstein)

[![JavaScript Style Guide](https://cdn.rawgit.com/standard/standard/master/badge.svg)](https://github.com/standard/standard)

<!-- vim-markdown-toc GFM -->
* [functionstein](#functionstein)
    * [Installation](#installation)
    * [Usage](#usage)
    * [API](#api)
    * [FAQ](#faq)
        * [What is functionstein?](#what-is-functionstein)
        * [Should I use this?](#should-i-use-this)
        * [Isn't there anything better that we could do with this name?](#isnt-there-anything-better-that-we-could-do-with-this-name)

<!-- vim-markdown-toc -->

# functionstein

Small toolbelt of functions (personal alternative for lodash/ramda inside small projects)


## Installation

`npm i --save functionstein`


## Usage

Simply import the functions you need like this:

```js
import { first } from 'functionstein'
```


## API

[API](https://on3iro.github.io/functionstein)

[GitHub](https://github.com/on3iro/functionstein)

## FAQ

### What is functionstein?

Functionstein is a collection of functions tailored to my needs. I use it
inside quite a few projects, where I need some helper functions, but don't want
to add the footprint of _lodash_ or similar libraries.


### Should I use this?

**Short Answer:** Probably not!

**Long Answer:** You technically could, but it is pretty likely that _functionstein_
wont fit your needs and you are better off with another library like [Lodash](https://lodash.com/)
or [Ramda](http://ramdajs.com/). **functionsteins** collection of functions might seem rather random at
times and I don't give any guarantees about the implementation of each function.

However if you are working on a small project and _functionstein_ fits you can use it ofcourse.
For anything that goes to production I would recommend one of the aforementioned libraries or
to create a personal fork of _functionstein_.


### Isn't there anything better that we could do with this name?

Absolutely. I really liked the name when it came to my mind and it still seems to fit
the purpose of this library. Nothing is set in stone, though. If you have a great library idea that would fit the name
better and would be more useful to others I would definitely be open to switch the purpose of the lib.
Just hit me up and open an issue where we could discuss this.

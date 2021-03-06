# ember-deep-set ![Download count all time](https://img.shields.io/npm/dt/ember-deep-set.svg) [![Build Status](https://travis-ci.org/poteto/ember-deep-set.svg?branch=master)](https://travis-ci.org/poteto/ember-deep-set) [![npm version](https://badge.fury.io/js/ember-deep-set.svg)](https://badge.fury.io/js/ember-deep-set)

`ember-deep-set` is a simple utility function to deeply set a value on an Ember Object or POJO. Note that this mutates the object.

To install:

```
ember install ember-deep-set
```

## Why this addon exists

`Ember.set` will throw an error if you try to set a value on a non-existent object. For example:

```js
Ember.set({}, 'foo.bar.baz', 123); // Property set failed: object in path "foo.bar" could not be found or was destroyed.
```

With `ember-deep-set`, you can safely and deeply set values on POJOs as well as Ember.Objects without having to first create the empty intermediate objects.

## Usage

```js
import Ember from 'ember';
import deepSet from 'ember-deep-set';

const { get } = Ember;

let company = {};
deepSet(company, 'region.department.director.name', 'Jim Bob');
deepSet(company, 'region.department.name', 'Accounting');
deepSet(company, 'region.name', 'North America');

get(company, 'region.department.name'); // "Accounting"
get(company, 'region.department.director'); // { name: "Jim Bob" }
```

## API

`deepSet` is designed to be a drop-in replacement to [`Ember.set`](http://emberjs.com/api/classes/Ember.html#method_set):

### `deepSet( object, key, value )`

#### Parameters:

- `object`: `{Ember.Object|Object}` The object to set values on
- `key`: `{String}` The key to set
- `value`: `{Any}` Value to set

#### Returns:

- `value`: `{Any}` Value that was passed in

## Installation

* `git clone <repository-url>` this repository
* `cd ember-deep-set`
* `npm install`
* `bower install`

## Running

* `ember serve`
* Visit your app at [http://localhost:4200](http://localhost:4200).

## Running Tests

* `npm test` (Runs `ember try:each` to test your addon against multiple Ember versions)
* `ember test`
* `ember test --server`

## Building

* `ember build`

For more information on using ember-cli, visit [https://ember-cli.com/](https://ember-cli.com/).

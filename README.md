karma-sinon-chai
================

  * [Sinon](http://sinonjs.org/)
  * [Chai](http://chaijs.com)
  * [Sinon-Chai](https://github.com/domenic/sinon-chai)

for [Karma](http://karma-runner.github.io)

Requirements
------------

This module currently requires the `canary` version of Karma:

```sh
$ npm install 'karma@canary' --save-dev
```

Note that the Karma configuration file format has changed since `v0.8`. Use 
`karma init` to generate a fresh config.

### Grunt

When using [grunt-karma](https://github.com/karma-runner/grunt-karma) to run Karma,
you need to use a version `>= 0.5.0` because earlier versions of `grunt-karma` use `karma < 0.9`
which does not support custom plugins.
At the time of this writing, `grunt-karma >= 0.5` is not yet available on npm, so you have
to install it directly from the git repo, i.e.
```sh
npm install --save-dev git+https://github.com/karma-runner/grunt-karma.git
```

Installation
------------

Install the module from Github:

```sh
$ npm install 'git+https://github.com/xdissent/karma-chai.git' --save-dev
```

Add `chai` to the `frameworks` key in your Karma configuration:

```coffee
module.exports = (karma) ->
  karma.configure

    # frameworks to use
    frameworks: ['mocha', 'chai']

    # ...
```


Usage
-----

Each of the different Chai assertion suites is available in the tests:

```coffee
describe 'karma tests with chai', ->

  it 'should expose the Chai assert method', ->
    assert.ok('everything', 'everything is ok');

  it 'should expose the Chai expect method', ->
    expect('foo').to.not.equal 'bar'

  it 'should expose the Chai should property', ->
    1.should.not.equal 2
    should.exist 123
```

Sinon and Chai matchers for Sinon are also available:

```coffee
describe 'karma tests with sinon', ->

  it 'can spy on objects', ->
    foo = bar: ->
    sinon.spy foo, 'bar'

    foo.bar 'baz'

    foo.bar.should.have.been.calledWith 'baz'
```


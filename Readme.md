*This repository is a mirror of the [component](http://component.io) module [timoxley/scriptloader](http://github.com/timoxley/scriptloader). It has been modified to work with NPM+Browserify. You can install it using the command `npm install npmcomponent/timoxley-scriptloader`. Please do not open issues or send pull requests against this repo. If you have issues with this repo, report it to [npmcomponent](https://github.com/airportyh/npmcomponent).*
# scriptloader

  Absurdly simple on-demand script loader.

## Installation

### component

  $ component install timoxley/scriptloader

### npm/browserify

  $ npm install scriptloader

## API

```js
var load = require('scriptloader')
load('//my-widget.js') // load js from current domain
load('//remote.com/their-widget.js') // load js from remote domain

// returns the script. you can listen for load/error on this directly
load('//cdnjs.cloudflare.com/ajax/libs/json3/3.2.4/json3.min.js').addEventListener('load', function() {
  console.log('it is loaded')
})

// or just supply a callback
load('//cdnjs.cloudflare.com/ajax/libs/json3/3.2.5/json3.min.js', function(err, script) {
  console.log('it is loaded')
})
```

#### What is this sorcery?

scriptloader appends a `script` tag to your `document.body` with the `src`
attribute set to the script you desire to load.

#### Why not just domify to add a script tag?

Interesting problem. [Unfortunately we can't use domify to do this]((https://github.com/component/domify/issues/14)
since `<script>` src attributes don't trigger remote loading
if they're created using `innerHTML`, which is how `domify` works.

## TODO

* Consider removing `<script>` after it loads?
* investigate script's `async` attribute.

## License

  MIT

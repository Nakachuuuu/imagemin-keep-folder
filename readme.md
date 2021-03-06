> Minify images seamlessly

## Introduction

Fork form [imagemin](https://github.com/imagemin).

> support keep and customize folder structure

## Install

```
$ npm install --save-dev imagemin-keep-folder
```

## Usage

```js
// as usual
const imagemin = require('imagemin-keep-folder');

imagemin(['images/*.{jpg,png}'], 'build/images', {
	
}).then(files => {
	console.log(files);
	//=> [{data: <Buffer 89 50 4e …>, path: 'build/images/foo.jpg'}, …]
});
```

```js
// keep folder structure as input
const imagemin = require('imagemin-keep-folder');

imagemin(['images/**/*.{jpg,png}'], {
  
});
// for example
// images/a.jpg => images/a.jpg
// images/foo/a.jpg => images/foo/a.jpg
// images/foo/bar/a.jpg => images/foo/bar/a.jpg
```

```js
// keep folder structure as input use imagemin-webp
const imagemin = require('imagemin-keep-folder');
const imageminWebp = require("imagemin-webp");

imagemin(['images/**/*.{jpg,png}'], {
  use: [
    imageminWebp({})
  ]
});
// for example
// images/a.jpg => images/a.webp
// images/foo/a.jpg => images/foo/a.webp
// images/foo/bar/a.jpg => images/foo/bar/a.webp
```

```js
// customize folder structure as input use imagemin-webp
const imagemin = require('imagemin-keep-folder');
const imageminWebp = require("imagemin-webp");

imagemin(['images/**/*.{jpg,png}'], {
  use: [
    imageminWebp({})
  ],
  replaceOutputDir: output => {
    return output.replace(/images\//, '.webp/')
  }
});
// for example
// images/a.jpg => .webp/a.webp
// images/foo/a.jpg => .webp/foo/a.webp
// images/foo/bar/a.jpg => .webp/foo/bar/a.webp
```


## API

### same as [imagemin](https://github.com/imagemin)

### imagemin(input, output, [options])

Returns `Promise<Object[]>` in the format `{data: Buffer, path: String}`.

#### input

Type: `Array`

Files to be optimized. See supported `minimatch` [patterns](https://github.com/isaacs/minimatch#usage).

#### output

Type: `string`

Set the destination folder to where your files will be written. ~~If no destination is specified no files will be written.~~  **If no destination is specified, files will be written and keep folder structure**

#### options

Type: `Object`

##### replaceOutputDir (new options)

Type: `Function`

Returns `String` (new output dir)

##### plugins

Type: `Array`

[Plugins](https://www.npmjs.com/browse/keyword/imageminplugin) to use.

### imagemin.buffer(buffer, [options])

Returns `Promise<Buffer>`.

#### buffer

Type: `Buffer`

Buffer to optimize.

#### options

Type: `Object`

##### plugins

Type: `Array`

[Plugins](https://www.npmjs.com/browse/keyword/imageminplugin) to use.


## Related

- [imagemin-cli](https://github.com/imagemin/imagemin-cli) - CLI for this module
- [imagemin-app](https://github.com/imagemin/imagemin-app) - GUI app for this module
- [gulp-imagemin](https://github.com/sindresorhus/gulp-imagemin) - Gulp plugin
- [grunt-contrib-imagemin](https://github.com/gruntjs/grunt-contrib-imagemin) - Grunt plugin


## License

MIT © [imagemin](https://github.com/imagemin)

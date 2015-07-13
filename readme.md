# grunt-sass-revisited [![Build Status](https://travis-ci.org/58bits/grunt-sass-revisited.svg?branch=master)](https://travis-ci.org/58bits/grunt-sass-revisited)

[<img src="https://rawgit.com/sass/node-sass/master/media/logo.svg" width="200" align="right">](https://github.com/sass/node-sass)

NOTE: This is a fork of [https://github.com/sindresorhus/grunt-sass](https://github.com/sindresorhus/grunt-sass), with the addition of an issue (with more detailed task configuration example) and a pull request (for output of total files processed at the end of the task) that were rejected by the current maintainer.
[https://github.com/sindresorhus/grunt-sass/pull/228](https://github.com/sindresorhus/grunt-sass/pull/228)
[https://github.com/sindresorhus/grunt-sass/issues/227](https://github.com/sindresorhus/grunt-sass/issues/227)

This version is being used in project where more detailed output from the task (total number of stylesheets processed) is helpful. I'll monitor and maintain parity with the original repo.

## Original README 
(with additional task configuration example)

> Compile Sass to CSS using [node-sass](https://github.com/sass/node-sass)

*Issues with the output should be reported on the libsass [issue tracker](https://github.com/hcatlin/libsass/issues).*

This task uses [libsass](http://libsass.org) which is a Sass compiler in C++. In contrast to the original Ruby compiler, this one is much faster, but is [missing some features](http://sass-compatibility.github.io/), though improving quickly. It also doesn't support Compass. Check out [grunt-contrib-sass](https://github.com/gruntjs/grunt-contrib-sass) if you prefer something more stable, but slower.


## Install

```
$ npm install --save-dev grunt-sass-revisited
```


## Usage

```js
grunt.initConfig({
	sass: {
		options: {
			sourceMap: true
		},
		dist: {
			files: {
				'main.css': 'main.scss'
			}
		}
	}
});
```

Or...

```js
grunt.initConfig({
	sass: {
		dev: {
			options: {
				outputStyle: 'expanded',
				sourceMap: true
			},
			files: [{
				expand: true,
				cwd: 'assets/scss',
				src: ['*.scss'],
				dest: 'public/css/',
				ext: '.css'
			}]
		},
		dist: {
			options: {
				outputStyle: 'compressed',
				sourceMap: false
			},
			files: [{
				expand: true,
				cwd: 'assets/scss',
				src: ['*.scss'],
				dest: 'public/css/',
				ext: '.css'
			}]
		}
	}
});
```

```
grunt.registerTask('default', ['sass']);
```

Files starting with `_` are ignored to match the expected [Sass partial behaviour](http://sass-lang.com/documentation/file.SASS_REFERENCE.html#partials).


## Options

See the `node-sass` [options](https://github.com/sass/node-sass#options), except for `file`, `outFile`, `success`, `error`.

The default value for the `precision` option is `10`, so you don't have to change it when using Bootstrap.


## License

MIT © [Sindre Sorhus](http://sindresorhus.com), portions © [Anthony Bouch](http://www.58bits.com)

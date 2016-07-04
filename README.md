# seed-width [![Build Status](https://travis-ci.org/helpscout/seed-width.svg?branch=master)](https://travis-ci.org/helpscout/seed-width) [![npm version](https://badge.fury.io/js/seed-width.svg)](https://badge.fury.io/js/seed-width) [![Dependency Status](https://david-dm.org/helpscout/seed-width.svg)](https://david-dm.org/helpscout/seed-width)
Width utility pack for [Seed](https://github.com/helpscout/seed)!


## Dependencies
* [Seed Breakpoints](https://github.com/helpscout/seed-breakpoints)


## Install
```
npm install seed-width --save-dev
```


## Basic Usage

### SCSS
This seed pack needs to be imported into your sass pipeline. Below is an example using Gulp:

```javascript
var gulp = require('gulp');
var sass = require('gulp-sass');
var seedWidth = require('seed-width');

gulp.task('sass', function () {
  return gulp.src('./sass/**/*.scss')
    .pipe(sass({
      includePaths: seedWidth
    }))
    .pipe(gulp.dest('./css'));
});
```

Once that is setup, simply `@import` *seed-width* as needed in your `.scss` file:

```sass
// Packs
@import "pack/seed-width";
```

**Note:** Because seed-width has dependencies, it's includePaths output will be an `array`. If you're including other paths in addition to seed-width, you will need to flatten the array. An easy way to do this is to use [sass-pathfinder](https://github.com/itsjonq/sass-pathfinder).

Example with *sass-pathfinder*:

```javascript
var gulp = require('gulp');
var sass = require('gulp-sass');
var seedWidth = require('seed-width');
var pathfinder = require('sass-pathfinder');

gulp.task('sass', function () {
  return gulp.src('./sass/**/*.scss')
    .pipe(sass({
      includePaths: pathfinder(
        './scss/vendor/example',
        './scss/plugins/super-awesome-plugin',
        seedWidth
      )
    }))
    .pipe(gulp.dest('./css'));
});
```


## Options

The following variables can be found in `_config.scss`

```sass
// Namespace
$seed-width-namespace: "u-width" !default;

// Grid
$seed-width-container-max: 1140px !default;
$seed-width-columns: 24 !default;

// Settings
$seed-width-enable-fluid: true !default;
$seed-width-enable-min: true !default;
$seed-width-enable-max: true !default;
```

**Note:** If you use `seed-width` with [`seed-grid`](https://github.com/helpscout/seed-grid), the grid configurations (above) will utilize `$seed-grid-columns` and `$seed-container-widths` instead. This ensures that the width system pairs nicely with the grid system.

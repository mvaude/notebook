+++
categories = ["Development", "golang"]
date = "2015-11-15T23:44:05+01:00"
description = ""
draft = true
image = "/img/about-bg.jpg"
tags = ["go", "golang", "templates", "themes", "development"]
title = "gulp"

+++

# Gulp

Gulp is a javascript streaming build system

# Fundamentals

## What Is A Build System ?

A build system is simply a collection of tasks (commonly called "task runners") that automate repetetive work.

## Component of a Modern Worfklow

Three different components:
* Package Managers
* Preprocessors
* Task Runners & Build Tools

### Package Managers

Automates packages and libraries used in your dev environment:
* installation
* upgrading
* removal
* dependencies

#### Package Managers Dependencies

You can use 2 different package managers:
* Bower
* NPM

##### Bower (Project Files)

Manages front-end dependencies (ex: jQuery, Backbone, AngualasJS).

##### NPM (Node.js)

Manages node environment dev dependencies (ex: Gulp, Browser-Syc, Plumber)

### Preprocessors

Preprocessors are critical to an efficient modern workflow by adding additional features and an optimized syntax that compiles into its native language.

#### CSS

Sass, Less, Stylus.

#### Javascript

CofeeScript, Typescript.

#### HTML

HAML, Jade, Markdeep, Markdown, Slim.

### Task Based Build Tools

* Gulp and Grunt
* Run on Node
* Similar anatomy

#### Structure of a Typical Gulp File

##### Required Modules

Declare requires dependencies

```
var gulp = require('gulp');
var uglify = require('gulp-uglify');
```

##### Named Tasks

* Compressing static images
* Copying files
* Deployment build

```
gulp.tasks('scripts', function() {
  \\ code
});

$ gulp scripts
`
```

##### Watch Task

Watch folder ```js``` for all files ending in .js then on change run 'script' task.

```
gulp.task('watch, function() {
  gulp.watch('app/js/**/*.js', ['scripts']);
});

$ gulp watch
```

##### Default Task

* Run both ```scripts``` and ```watch``` tasks.
* Asynchronously, run all tasks at the same time.

```
  gulp.task('default', ['scripts', 'watch']);

  $ gulp
```

### Gulp vs Grunt

#### Learning

##### Gulp

* Easier to learn and maintain
* Code over configuration

##### Curve

* Steeper learning curve
* Relies on A LOT of configuration
  - Syntax overly verbose

#### Speed

##### Gulp

* Faster
* Streams

##### Curve

* Possibility Slower
* Write to temp files

# The Gulp File

## Gulp Packages

### gulp

The streaming build system.

### gulp-plumber 

Prevents pipes from breaking caused by errors from gulp plugins.

### gulp-uglify

Minify files.

### gulp-rename

Rename files.

### gulp-sass

### gulp-autoprefixer

### gulp-smith

### del

### gulp-sourcemaps

### browser-sync

### gul-concat



Delete files/folders using globs

### guld-browser-sync

Live CSS Reload & Brower Syncing

## What is A Glob ?

In computer programming, in particular in a Unix-like environment, glob patterns specify sets of filenames with wildcard characters.

### Examples

* ```css/*.css``` -> files ending in ```.css``` in the css directory.
* ```css/**/*.css``` -> files ending in ```.css``` in the ```css``` directory and child repositories.
* ```!css/styles.css``` -> exclude style.css file.
* ```*.+(js|css)``` -> Matches all files in the ```root``` directory ending in ```.js``` or ```.css```.
*  

### Improvments



# Resources

Almost all the content from this page come from this resources:
* Joel Longie Youtube playlist ![alt][https://www.youtube.com/watch?v=LmdT2zhFmn4&list=PLv1YUP7gO_viROuRcGsDCNM-FUVgMYb_G]

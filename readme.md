# Introduction to the Yeoman `gulp-angular` Generator

## First Things First

### What is Yeoman?
* _Yeoman_ is a tool for creating and running _generators_.
* Generators are a combination of code and templates that generate a project.
* Anyone can write a _Yeoman_ generator to generate any kind of project, such as:
  - A Simple [Web App](https://github.com/yeoman/generator-webapp#readme)
  - An AngularJS Web App - [angular](https://github.com/yeoman/generator-angular#readme) and [gulp-angular](https://github.com/swiip/generator-gulp-angular#readme).
  - An [AngularJS Full-Stack (MEAN) App](https://github.com/angular-fullstack/generator-angular-fullstack)
  - A [ReactJS Full-Stack (Mean) App](https://github.com/kriasoft/react-starter-kit)
  - [Ionic](https://github.com/diegonetto/generator-ionic)
  - [Wordpress](https://github.com/wesleytodd/YeoPress)
  - [Polymer](https://github.com/yeoman/generator-polymer#readme)
  - [Backbone](https://github.com/yeoman/generator-backbone#readme)
  - [Generator](https://github.com/yeoman/generator-generator#readme) - So Meta!!!
  - For more, see [Yeoman Generators](http://yeoman.io/generators/)

### What is Grunt / Gulp?
* Grunt and Gulp are _task runners_.
* They are similar to `make`, `ant`, `rake`, etc.
* Grunt and Gulp are configured via a set of `plugins` and configuration code.
* Typical plugins include:
  - CSS autoprefixer
  - SASS compilation
  - Transpiling CoffeeScript, TypeScript, or ES6
  - Unit and Integration Test Runners
  - Linting your code
  - HTML/CSS/JS minification
  - `Rev`ing the HTML/CSS/JS file names
  - Running a lightweight server for `RAD` with `watch` and `browser-sync`

### Is Gulp > Grunt
* _Gulp_ is _much faster_ than Grunt, due to its `stream` architecture
* _Grunt_ is a little easier to learn / configure.

### What is Bower (and how is it different from `npm`)?
* Bower manages your web project's _client-side_ dependencies, such as:
  - jQuery
  - Twitter Bootstrap
  - AngularJS
  - angular-ui-router
  - animate.css
  - font-awesome
* See [Bower Stats](http://bower.io/stats/)
* How is `bower` different from `npm`?
  - `npm` is used for _server-side_ dependencies.
  - `npm` can manage multiple versions of the same library in the same project.
    * "It is much harder to avoid dependency conflicts without nesting dependencies. This is fundamental to the way that npm works, and has proven to be an extremely successful approach."
  - `bower` is used for _client-side_ dependencies.
  - `bower` requires you to resolve version conflicts.
    * "Bower is optimized for the front-end. Bower uses a flat dependency tree, requiring only one version for each package, reducing page load to a minimum."

### How `npm` manages dependencies

    project root
      [node_modules] // default directory for dependencies
        -> dependency A
        -> dependency B
          [node_modules]
        -> dependency A
        -> dependency C
          [node_modules]
        -> dependency B
          [node_modules]
            -> dependency A
        -> dependency D

### How `bower` manages dependencies

    project root
      [bower_components] // default directory for dependencies
         -> dependency A
         -> dependency B // needs A
         -> dependency C // needs B and D
         -> dependency D

### Common Bower Commands

```bash
bower help                        # print help
bower init                        # initialize a bower.json file
bower install <package>           # install a package locally
bower install -S <package>        # install a package locally and save to bower.json file
bower search <keyword>            # search for all bower packages containing keyword
bower list                        # look for updates to installed packages
```

## The `gulp-angular` Generator

### Features:
* Generates a modern _AngularJS_ web app with _Gulp_ pre-configured as the task runner.
* Supports many options, including:
  - jQuery:
    * jQuery 1.x
    * 2.x
    * Zepto
    * none
  - Angular modules:
    * animate
    * cookies
    * touch
    * sanitize
  - Resource handler:
    * ngResource
    * Restangular
    * none
  - Router:
    * ngRoute
    * UI Router
    * none
  - UI Framework:
    * Bootstrap
    * Foundation
    * Angular Material
    * Material Design Lite
    * none (depends on the chosen CSS preprocessor)
  - UI directives :
    * UI Bootstrap
    * Angular Strap
    * official Bootstrap JavaScript
    * Angular Foundation
    * official Foundation JavaScript
    * none (depends on the UI framework)
  - CSS pre-processor:
    * Less
    * Sass with Ruby and Node
    * Stylus
    * none
  - JS preprocessor:
    * CoffeeScript
    * TypeScript
    * ECMAScript 6 (Traceur and Babel)
    * none
  - HTML preprocessor:
    * Jade
    * Haml
    * Handlebars
    * none

> Pretty Amazing! You can run the `gulp-angular` generator and end up with a project pre-configured with all of these amazing technologies!

### Before Running the Generator

First let's make sure you have the tools you will need installed to your laptop. Here is a `bash` script that makes this simple (feel free to edit it as desired):

```bash
#!/bin/bash

echo "Installing latest stable version of NodeJS"
nvm install 5.6.0
nvm alias default 5.6.0
nvm use default

echo "updating npm"
npm update -g

MODULES="
jasmine-node
express
express-generator
bower
grunt-cli
gulp
yo
generator-gulp-angular
generator-angular-fullstack
"

for MODULE in $MODULES
do
  echo "#################################"
  echo "Installing or Updating $MODULE"
  echo "#################################"
  npm install -g $MODULE
done
```

### Running the Generator

Now we are ready to run the `gulp-angular` generator and kick the tires:

```bash
cd /tmp
mkdir gulp-angular-test
cd gulp-angular-test
yo gulp-angular
```

> You can select all of the generator defaults except for the question "Would you like to use a REST resource library?" - for that question choose _"None, $http is enough!"_

The generator will then do the following:

* Generate an _AngularJS_ project for you, including:
  - `gulp` configuration and plugins
  - directory structure
  - sample code
  - sample unit tests
  - a preconfigured `package.json` file
  - a preconfigured `bower.json` file
  - basically a full skeleton of your new _AngualarJS_ project!
* Run `npm install` and `bower install` to install the project dependencies (this can take a while the first time it is run).

### Tour of the Generated Project

Now we will take a quick tour of what the generator produces for us.

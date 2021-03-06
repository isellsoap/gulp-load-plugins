#gulp-load-plugins

Formally known as `gulp-load-tasks`, but renamed to be clearer.

Loads in any gulp plugins and attaches them to the global scope, or an object of your choice.

[![Build Status](https://travis-ci.org/jackfranklin/gulp-load-plugins.png)](https://travis-ci.org/jackfranklin/gulp-load-plugins)

## Usage

```
$ npm install --save-dev gulp-load-plugins
```

Given a `package.json` file that has some dependencies within:

```json
{
    "dependencies": {
        "gulp-jshint": "*",
        "gulp-concat": "*"
    }
}
```

Adding this into your `Gulpfile.js`:

```js
var gulp = require("gulp");
var gulpLoadPlugins = require("gulp-load-plugins");
var plugins = gulpLoadPlugins();
```

Or, even shorter:

```js
var plugins = require("gulp-load-plugins")();
```

Will result in the following happening:

```js
plugins.jshint = require("gulp-jshint");
plugins.concat = require("gulp-concat");
```

You can then use the plugins just like you would if you'd manually required them, but referring to them as `plugins.name()`, rather than just `name()`.

This frees you up from having to manually require each gulp plugin.

## Options

You can pass in an argument, an object of options (the shown options are the defaults):

```js
gulpLoadPlugins({
    pattern: "gulp-*", // the glob to search for
    config: "package.json", // where to find the plugins
    scope: ["dependencies", "devDependencies", "peerDependencies"], // which keys in the config to look within
    replaceString: "gulp-", // what to remove from the name of the module when adding it to the context
    camelize: true // if true, transforms hyphenated plugins names to camel case
});
```

## Credit

Credit largely goes to @sindresorhus for his [load-grunt-plugins](https://github.com/sindresorhus/load-grunt-tasks) plugin. This plugin is almost identical, just tweaked slightly to work with Gulp and to expose the required plugins.

## Changelog

#####0.3.0
- turn the `camelize` option on by default

#####0.2.0
- added `camelize` option, thanks @kombucha.
- renamed to `gulp-load-plugins`.

#####0.1.1
- add link to this repository into `package.json` (thanks @ben-eb).

#####0.1.0
- move to `gulpLoadplugins` returning an object with the tasks define.

#####0.0.5
- added `replaceString` option to configure exactly what gets replace when the plugin adds the module to the context

#####0.0.4
- fixed keyword typo so plugin appears in search for gulp plugins

#####0.0.3
- removed accidental console.log I'd left in

#####0.0.2
- fixed accidentally missing a dependency out of package.json

#####0.0.1
- initial release




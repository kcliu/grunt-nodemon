# grunt-nodemon

> Run [nodemon](https://github.com/remy/nodemon) as a grunt task for easy configuration and integration with the rest of your workflow.

## Getting Started
If you haven't used grunt before, be sure to check out the [Getting Started](http://gruntjs.com/getting-started) guide, as it explains how to create a gruntfile as well as install and use grunt plugins. Once you're familiar with that process, install this plugin with this command:
```shell
npm install grunt-nodemon --save-dev
```

Then add this line to your project's `Gruntfile.js` gruntfile:

```javascript
grunt.loadNpmTasks('grunt-nodemon');
```

## Documentation

### Dependencies
The only non-grunt dependency of grunt-nodemon is the nodemon module. If you don't have nodemon installed, install it globally with this command:

```shell
npm install nodemon -g
```

### Usage
The minimal usage of nodemon runs with no options:
```js
nodemon: {
  dev: {}
}
```
When this is run, nodemon will look at the `package.json` file for the `main` property and run its value as a command in node.

Here is a config that uses all of the available options for nodemon:

```js
nodemon: {
  prod: {
    options: {
      file: 'test/server.js',
      args: ['production'],
      ignoredFiles: ['README.md', 'node_modules/**'],
      watchedExtensions: ['js', 'coffee'],
      watchedFolders: ['test', 'tasks'],
      debug: true,
      delayTime: 1
    }
  },
  exec: {
    options: {
      exec: 'less'
    }
  }
}
```
### Options

#### file
Type: `string`

This is file that nodemon runs and restarts when changes are detected.

### args
Type: `Array` of `strings`

This is the list of arguments to be passed to your file.

### ignoredFiles
Type: `Array` of `string globs`

This is a list of ignored files specified by a glob pattern. [Here](https://github.com/remy/nodemon#ignoring-files) is an explanation of how to use the patterns to ignore files. This task will create a `.nodemonignore` file in your repo based on these settings which nodemon reads when it starts.

### watchedExtensions
Type: `Array` of `strings` Default: `'js'`

This is a list of file extensions to watch for changes. By default nodemon only watches JavaScript files.

### watchedFolders
Type: `Array` of `strings` Default: `'.'`

List of folders to watch for changes if you don't want to watch the root folder and its subdirectories.

### debug
Type: `Boolean`

Optionally launch the node.js debug server.

### delayTime
Type: `Number`

Delay the restart of nodemon by a number of seconds when compiling a large amount of files so that the app doesn't needlessly restart after each file.

### exec
Type: `string`

You can use nodemon to execute a command outside of node. Use this option to specify a command as a string with the argument being the file parameter above. You can read more on exec [here](https://github.com/remy/nodemon#running-non-node-scripts).

# Changelog

**0.0.0** - Initial release

**0.0.1** - Added warning if `nodemon` isn't installed as a global module

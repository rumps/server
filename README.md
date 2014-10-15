# Rump Server
[![NPM](http://img.shields.io/npm/v/rump-server.svg?style=flat-square)](https://www.npmjs.org/package/rump-server)
![License](http://img.shields.io/npm/l/rump-server.svg?style=flat-square)
[![Dependencies](http://img.shields.io/david/rumps/rump-server.svg?style=flat-square)](https://david-dm.org/rumps/rump-server)
[![Peer Dependencies](http://img.shields.io/david/peer/rumps/rump-server.svg?style=flat-square)](https://david-dm.org/rumps/rump-server#info=peerDependencies)


## About
Rump Server is a Rump module that starts up a local development server that
serves built assets using [BrowserSync](http://www.browsersync.io/). For more
information, visit the [Rump repository](https://github.com/rumps/rump).


## API
The following is appended to the core Rump API:

### `rump.addGulpTasks()`
This module adds the following tasks:
- `rump:server` will start up the `rump:watch` task, then start up BrowserSync
  on the destination path.
- `rump:info:server` will display information on what this specific module
  does, specifically the port number the local server is started at. This task
  is also added to the `rump:info` task.

### `rump.configure(options)`
Redefine options for Rump and Rump modules to follow. In addition to what
options Rump and other Rump modules offer, the following options are
available alongside default values:

#### `options.globs.watch.server` (`'**/*'`)
This specifies which files to monitor for auto refresh by BrowserSync. By
default it monitors all built files, including those in subdirectories.

#### `options.server.port` (`process.env.PORT` or `3000`)
This specifies which port to run BrowserSync under.

#### `options.server.watch` (`options.environment === 'development'`)
This specifies whether BrowserSync monitors files for file changes and inject
changes or perform full-page refreshes. By default monitoring is set up if the
environment is set to development. (visit the main Rump repository for more
information on environment)

#### `options.server.browserSync`
This specifies any options you want to override in BrowserSync. If the
environment is set to `development`, notifications and ghost mode is enabled.
If the environment is set to `production`, notifications and ghost mode is
disabled. Visit the [options page](http://www.browsersync.io/docs/options/) for
specific options available.

### `rump.configs.browserSync`
This contains the generated options that are passed to BrowserSync in the Gulp
task. This is a good way to see what options are generated based on defaults
and overrides.

# Node API for Adobe ExtendScript

ExtendScript api compatible with [node.js](http://nodejs.org "Node.js").

ExtendScript has no `setTimeout`, so all functions are synchronous.
Main difference between `func` and `funcSync` is that `funcSync`
throw exeption, when error occures.

Anyway if you decide to use `func` insteed of `funcSync` do not use at as
synchronous, when `setTimeout` would be added to `ExtendScript` it would be
added to `func` to improve responsiveness of `jsx` scripts.

## API

### Require

Described modules could be loaded with [es-require](https://github.com/coderaiser/es-require "ES Reqiure") as well.

```js
var fs = require('lib/fs');
```

### File System

Use `#include lib/fs.js` to use this module. The following methods are provided:

#### fs.mkdir(path, callback)#
Asynchronous mkdir(2). No arguments other than a possible exception are given to the completion callback. mode defaults to 0777.

#### fs.mkdirSync(path)#
Synchronous `fs.mkdir`.

#### fs.rename(oldPath, newPath, callback)#
Asynchronous rename. No arguments other than a possible exception are given to the completion callback.

#### fs.renameSync(oldPath, newPath)#
Synchronous `fs.rename`.

#### fs.writeFile(name, data, callback)

Writes data to a file.

```js
fs.writeFile('hello.html', '<html></html>', function(error) {
    if (error)
        alert(error);
});

```

#### fs.writeFileSync(name, data)

Synchronous version of `fs.writeFile`.

```js
try {
    fs.writeFileSync('hello.html', '<html></html>');
} catch(error) {
    alert(error);
}
```

#### fs.readFile(name, callback)

Reads data from a file.

```js
fs.readFile('hello.html', function(error, data) {
    if (error)
        alert(error);
    else
        alert(data);
});

```

#### fs.readFileSync(name)

Synchronous version of `fs.readFile`.

```js
try {
    var data = fs.readFileSync('hello.html');
    alert(data);
} catch(error) {
    alert(error);
}
```

### Path
Use `#include lib/path.js` to use this module. The following methods are provided:

#### path.dirname(p)#
Return the directory name of a path. Similar to the Unix dirname command.

```js
path.dirname('/foo/bar/baz/asdf/quux')
// returns
'/foo/bar/baz/asdf'
```

#### path.basename(p[, ext])#
Return the last portion of a path. Similar to the Unix basename command.

Example:

```js
path.basename('/foo/bar/baz/asdf/quux.html')
// returns
'quux.html'

path.basename('/foo/bar/baz/asdf/quux.html', '.html')
// returns
'quux'
```

#### path.normalize(name)
Normalize a string path, taking care of '..', '.' and '~' parts.

```js
    var name = path.normalize('~/tmp/index.html');
    // returns
    '/Users/username/tmp/index.html'
```

## License

MIT

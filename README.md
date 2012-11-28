# node-tar

Tar for Node.js.

The only difference between this and [isaacs](https://github.com/isaacs/node-tar) repo is that a new property `prefix` is added to the packer so that we can decide the prefix directory of the files in the tar file.

## Quick start

``` coffeescript
fstream = require 'fstream'
tar     = require 'tar'
zlib    = require 'zlib'

fstream.Reader({ 'path': '.', 'type': 'Directory' })
.pipe(tar.Pack({ 'noProprietary': true, 'prefix': '.' }))
.pipe(zlib.Gzip())
.pipe(fstream.Writer({ 'path': 'app.tar.gz', 'type': 'File' }))
```
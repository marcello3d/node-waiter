node-waiter
===========
Waiter is an extremely simple way to handle parallel asynchronous calls in Node.js.

Introduction
------------
Just a little utility class for dealing with parallel classes. For comparison, this readme is longer
than the source code itself.

Examples
--------

    var waiter = new Waiter
    var aFile = waiter(function(done) {
        fs.readFile('a.txt', done)
    })
    var bFile = waiter(function(done) {
        fs.readFile('b.txt', done)
    })
    waiter.waitForAll(function(error) {
        if (error) throw "the revolution!"
        // do something with aFile.value and bFile.value
    })

    var files = [ ... ]
    var waiter = new Waiter
    var filesContent = files.map(function(file) {
        return waiter(function(done) {
            fs.readFile(file,done)
        })
    })
    waiter.waitForAll(function(error) {
        if (error) throw "the revolution!"
        // do something with fileContents[x].value
    })

License
-------
Waiter is open source software under the [zlib license][1].

[1]: https://github.com/marcello3d/node-mongolian/blob/master/LICENSE
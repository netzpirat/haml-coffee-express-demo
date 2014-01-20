# Haml Coffee & Express.js Demo App

This is a simple example Express.js application that shows how to set up
[Haml Coffee](https://github.com/netzpirat/haml-coffee).

## Setup

### 1. Install packages

Add the following packages to your `package.json`:

```JavaScript
{
  "name": "haml-coffee-express",
  "description": "hello world test app",
  "version": "0.0.1",
  "private": true,
  "dependencies": {
      "express": "3.0.1",
      "express-partials": "0.0.6"
  }
}
```

and install them with `npm install`.

### 2. Set up the server

Define your initial Express 3 app in `server.js`:
 
```JavaScript
var express = require('express');
var partials = require('express-partials');
var app = express();

app.engine('hamlc', require('haml-coffee').__express);
app.use(partials());

app.configure(function() {
  app.set('view engine', 'hamlc');
  app.set('layout', 'layout');
})

app.get('/', function(req, res) {
  res.render('index', { name: 'Express user' });
})

app.listen(3000);
console.log('App started on port 3000');
```

### 3. Write your templates

For this showcase only one simple template `views/index.hamlc` exists:

```Haml
%h1= "Welcome #{ @name }"
%p You've rendered your first Haml Coffee view.
```

and a layout file `views/layout.hamlc`:

```Haml
!!!
%head
  %title Express App
  %body
    != @body
```

### 4. Start the app

Load the template in your app and render it:

```JavaScript
node server.js
```

## Author

Developed by Michael Kessler, [FlinkFinger](http://www.flinkfinger.com).

If you like Haml Coffee Assets, you can watch the repository at [GitHub](https://github.com/netzpirat/haml_coffee_assets) and
follow [@netzpirat](https://twitter.com/#!/netzpirat) on Twitter for project updates.

## License

(The MIT License)

Copyright (c) 2012 Michael Kessler

Permission is hereby granted, free of charge, to any person obtaining
a copy of this software and associated documentation files (the
'Software'), to deal in the Software without restriction, including
without limitation the rights to use, copy, modify, merge, publish,
distribute, sublicense, and/or sell copies of the Software, and to
permit persons to whom the Software is furnished to do so, subject to
the following conditions:

The above copyright notice and this permission notice shall be
included in all copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED 'AS IS', WITHOUT WARRANTY OF ANY KIND,
EXPRESS OR IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF
MERCHANTABILITY, FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT.
IN NO EVENT SHALL THE AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY
CLAIM, DAMAGES OR OTHER LIABILITY, WHETHER IN AN ACTION OF CONTRACT,
TORT OR OTHERWISE, ARISING FROM, OUT OF OR IN CONNECTION WITH THE
SOFTWARE OR THE USE OR OTHER DEALINGS IN THE SOFTWARE.




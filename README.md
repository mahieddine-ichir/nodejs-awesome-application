# nodejs-awesome-application
An Express JS / NodeJS startup application.

# Application startup
To start application, run
```
npm install && npm start
```
The application listens to port 3000 by default (see bin/www).

_The startup command is configured in the package.json file._

# Views template engine
The application is configured to use "jade" engine (see app.js). To set another template engine (ejs for example), modify (in app.js) to the following
```
app.set('view engine', 'ejs');
```
Do not forget to save the 'ejs' dependency in npm using
```
npm install --save ejs
```

Express is configured to load view templates from the _./views/_ directory (see app.js)
```
app.set('views', path.join(__dirname, 'views'));
```

## Public resources (stylesheets, javascripts, images, ...)
Also denoted as _static_ resources, configured in app.js to be loaded from the './public' directory
```
app.use(express.static(path.join(__dirname, 'public')));
```
Hence, in any view template, just refer to these static resources using for example '/stylesheets/app.css' to refer to './public/stylesheets/app.css' (see '/views/layout.js' for an example).

# Routes
All routes are declared in './routes' directory.
By default, the application is configured with two routes (in app.js):

1. views routes (see './routes/index.js')
```
var routes = require('./routes/index'); // index.js namely
// ...
app.use('/', routes);
```
A view is rendered using
```
res.render('my-view'); // namely ./views/my-view.js
```
or
```
res.render('my-view', {'key': 'value'});
```
to inject any dynamic data to the view.

2. resources routes (see './routes/users.js')
```
var users = require('./routes/users'); // users.js namely
// ...
app.use('/users', users);
```
Use
```
res.json({'key0': 'value0', 'key0': 'value0'});
```
to return json formatted data for example.

# Application packages (see package.json)
- express: node.js web application framework (routing framework)
- path: a set of utilities to work with files
- serve-favicon: Node.js middleware for serving a favicon (optional)
- morgan: request logger middleware (optional)
- cookie-parser: Cookies header parser (req.cookies)
- body-parser: for parsing body data (json or urlencoded in the application)
- http (in bin/www): standard node.js http interfacing

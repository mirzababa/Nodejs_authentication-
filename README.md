# Nodejs_authentication-


Video 1:
1- Create a folder every Vere
2- Right click and select "Git Bash Here"
3- $ npm install -g express
4- $ npm install -g express-generator
5- $ express
6- Open json folder in every Vere
7- Add this command in package.json:
	"mongodb":"*",
	"mongoose":"*",
	"connect-flash":"*",
	"express-messages":"*",
	"express-validator":"*",
	"passport":"*",
	"passport-local":"*",
	"passport-http":"*",
	"multer":"*"
8- $ npm install
9- In app.js add:
var express = require('express');
var path = require('path');
var favicon = require('serve-favicon');
var logger = require('morgan');
var cookieParser = require('cookie-parser');
var bodyParser = require('body-parser');
var session = require('express-session');
var passport = require("passport");
var expressValidator = require('express-validator');
var LocalStrategy = require('passport-local').Strategy;
var multer = require('multer');
var upload = multer({dest:'./uploads'});
var flash = require('connect-flash');
var mongo = require('mongodb');
var mongoose = require('mongoose');
var db = mongoose.connection;

var index = require('./routes/index');
var users = require('./routes/users');

var app = express();

// view engine setup
app.set('views', path.join(__dirname, 'views'));
app.set('view engine', 'jade');

// uncomment after placing your favicon in /public
//app.use(favicon(path.join(__dirname, 'public', 'favicon.ico')));
app.use(logger('dev'));
app.use(bodyParser.json());
app.use(bodyParser.urlencoded({ extended: false }));
app.use(cookieParser());
app.use(express.static(path.join(__dirname, 'public')));

//Handle Session
app.use(session({
	secret:'secret',
	saveUnitialized: true,
	resave: true
}));

//passport
app.use(passport.initialize());
app.use(passport.session());

//validator
//const expressValidator = require('express-validator');
app.use(expressValidator({
  errorFormatter: function(param,msg,value){
    var namespace = param.split('.')
    , root = namespace.shift()
    , formParam = root;
    while (namespace.length) {
        formParam +='[' + namespace.shift()
    }
    return {
      param: formParam,
      msg :msg,
      value : value
    };
  }
}));

//express message
app.use(flash());
app.use(function (req, res, next) {
  res.locals.messages = require('express-messages')(req, res);
  next();
});

app.use('/', index);
app.use('/users', users);

// catch 404 and forward to error handler
app.use(function(req, res, next) {
  var err = new Error('Not Found');
  err.status = 404;
  next(err);
});

// error handler
app.use(function(err, req, res, next) {
  // set locals, only providing error in development
  res.locals.message = err.message;
  res.locals.error = req.app.get('env') === 'development' ? err : {};

  // render the error page
  res.status(err.status || 500);
  res.render('error');
});
module.exports = app;

Unfortunately modules not be install by var --- = require ('---'); and I install them on GIT bash by command 
"$npm install ---"
10- $npm start 
	The middleware created 

 


What is middleware? In a complex enterprise environment, there are a number of challenges when you need to integrate two or more enterprise systems together to talk to each other. Normally these systems do not understand each other’s language as they are developed on different platforms using different languages (like C++, Java, COBOL, etc.).
So here comes middleware software in picture which provides services like
•	transformation of messages formats from one app to other,
•	routing and enriching messages besides taking care of security,
•	encryption,
•	validation and
•	Applying different business rules to these messages.

Video 2:
Install mongoDB in drive C in a new folder. Call new folder “mongodb”

1-	Create   “data” folder in “C:\”
2-	Create “db” folder in “C:\data”
3-	Create “log” folder in “C:\”
4-	Run the cmd as administrator
5-	$ cd/     (takes you to the top of the directory tree)
6-	$ cd mongodb
7-	$ ls(get all directory)
8-	$bin
9-	$mongod --directoryperdb --dbpath C:\mongodb\data\db --logpath C:\mongodb\log\mongodb.log --logappend --rest –install
10-	Start service by this command: $net start mongDB
11-	Run mongo shell with command $mongo (in shell can do things like create data base, create document, update or delete data base, manage collections(similar to data base tables, …)
12-	$db (show the data base that we are in)
13-	If we want a new one: $use customers
14-	Show all available data base: $show dbs
15-	If a data base was empty we cannot see it
16-	Create a new collection: $db.createCollection(‘collection name’);
17-	db.collection name.insert({name:’name’, email: ‘email’, …}); (insert the  collection with json object)
18-	db. collection name.find(); (see the record in data base) or db. collection name.find().pretty();
19-	db. collection name.update({username: ‘username’} , {$set:{email:’email2’}}); (update username’s email to email2)
20-	db.users.remove({username: ‘username’}); (remove the table)

Video4:
Download ‘bootstrap’
Go to project folder -> public
Go to ‘\bootstrap-3.3.7\dist -> css
Copy ‘bootstrap.css’ to ‘public\stylesheets’
Go to ‘\bootstrap-3.3.7\dist -> js
Copy ‘bootstrap.js to ‘public\javascript’
Open node project
Change view->layout.jade html code
Start the npm
 






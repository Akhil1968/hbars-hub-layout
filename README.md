# handlebars template engine with bootstrap
a node.js application using express.js, handlebars template engine and bootstrap
it explains the following
   Middleware- body-parser
   Middleware- static
   Middleware- express-session
   Middleare-  Template Engine handlebars
   using handlebars for creating dynamic HTML 
   decorating html FORM using bootstrap

##############################################
###### Summary of Node+Express Learning ######
##############################################
# Retrieving HTTP GET Request Parameters  
	req.query.nm 
	req.params.nm
# Retrieving HTTP POST Request Parameters
    configure body-parser 
    req.body.nm

# Middleware in Express
    static contents Middleware-
	    app.use(express.static(__dirname + "/public"));

	body-parser middleware for Http POST requests
        var bodyparser = require('body-parser');
	    app.use(bodyparser.json());
	    app.use(bodyparser.urlencoded({extended:false}));
	    req.body.nm

	Http session  middleware
        var session = require('express-session'); 
        app.use(session({secret: "secret",  resave : true,  saveUninitialized : false}));

# EJS template engine
    No need to ‘require’
    app.set('view engine', 'ejs');
    keep template files in views folder. Template files should have .ejs extension.
    Partials should be kept in the folder views/partials
    <%include partials/includeHead.ejs %>
    <%= person%>
    res.render('landingpage.ejs', {welcomeMessage:person});

# JADE Template Engine
    No need to ‘require’
    app.set('view engine', 'jade');
    keep template files in views folder. Template files should have .jade extension.
    Partials should be kept in the folder views/partials
    include partials/includeHead.jade
    Referring to variables
        h2= person
        #{person}
    res.render('landingpage.jade', {welcomeMessage:person});

# Handlebars template engine
    var handlebars = require('express-handlebars');
    app.set('view engine', 'handlebars');
    app.engine('handlebars', handlebars({}));
    keep template files in views folder. Template files should have .handlebars extension.
    Partials should be kept in the folder views/partials
    {{>includeHead}} – No path, no extension
    {{cityName}}
    res.render('landingpage.handlebars', {welcomeMessage:person});

# Handling HTTP 400 errors (Client Errors) in express applications
    app.use("*", function(req, res) {
        res.status(404);
        res.render('404.handlebars', {});
    });

# Handling HTTP 500 errors (Server errors) in express applications
    app.use(function(error, req, res, next) {
        console.log(chalk.red('Error : 500::' + error))
        res.status(500);
        res.render('500.handlebars', {err:error});  // good for knowledge but don't do it
    });

    






# Session-management-in-Express

  - Since Http is stateless, we need a way to store user data if we are
  willing to associate a request to another.

  - Cookies and URL parameters are both suitable ways to store user data. However,
  they are both accessible on the client side. Here, sessions come in handy.

  - Express provides a module that solves this problem.

  - We can assign the client an ID and the all further requests are processed
  using that ID.

  - We can install the module by typing into the terminal :
  

  > npm install --save express-session



  Here is a simple example of using session management in your code :

      >var express = require('express');
 
      >var cookieParser = require('cookie-parser');

      >var session = require('express-session');

      >var app = express();

          >app.use(cookieParser());

       >app.use(session({secret: "Shh, its a secret!"}));

          >app.get('/', function(req, res){

            >if(req.session.page_views){
   
      >req.session.page_views++;
      
      >res.send("You visited this page " + req.session.page_views + " times");
      
       >} else {
   
      >req.session.page_views = 1;
      
      >res.send("Welcome to this page for the first time!");
       >}
   
       >});

   >app.listen(3000);

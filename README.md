# reverseEngineer
Google Drive Link : https://docs.google.com/document/d/1d0i1ppp8OPw8bIi1Z2hEZQ5ulfLaUCO7lAF7OI6kHpk/edit#heading=h.8pe1cnl60wip


Reverse Engineering CODE! 

(Middleware)
isAuthenticated.js

This file is exporting a function that redirects user once they have input their log in info, this file is exported to html-routes.. If user is not logged in, they get redirected to the log in page. 
var isAuthenticated = require("../config/middleware/isAuthenticated");
This is an especially good program for keeping passwords safe. 

Config.Json
User is going to install all of the packages required and then will have a config.json file to insert the correct db name.
Passport.js
Passport JS is going to handle the email and password, and decide if the information is usable. The user will enter an email address instead of a username. This takes care of issues such as a user inputting the correct email and incorrect password. 

Server.js 
Server.js is setting up the server connection. In order to do so, it requires express, express session and passport! The server should always be set to 8080. It then requires the html and api routes. This is the file that connects everything pretty much. We also have the database connected at the bottom of this file. 
(models)
Index.js
Index.js is requiring files like fs, path, sequelize, basename, env, config and db. 
Let’s start with sequelize!
This is our orm, we are using it to transfer data to and from the database. Using ENV we have a connection between our database and server. ‘New Sequelize’ is basically setting us up to have multiple variables pass through. FS is sending the information. 
This file is being exported as db, for other files to access.

User.js
User.js is going to use sequelize and export a function. 
It is basically laying out the rules for SQL to use. Email can only be a string, cannot be null, is unique and validate email: true. 
Password is allowed to only be a string, and cannot be null. The ‘bcrypt’ which was required in the first line of the file, is going to work with the hashed/unhashed password through the database. 


(public)
Login.html 
Login html is using a form with submit buttons, 
The email input has an id of email-input which links the submission for the login.js to use for example. The password input has an id of password-input, which is also form controlled so the characters typed in are hidden. 
Once the submit button is hit, this sends the login.js file to work. 
There is also a grid system on all html files, which make mobile responsiveness easy to handle! 
Login.js
Email and password are set as a value and trimmed, incase user adds spaces at end of submission. If the data is invalid, the user is sent back to the return form. 
Once user hits submit, the loginUser function is called which is assigning the input to a value.
If the information/variables are correct, the user is routed to the members page, which was done using POST, if not, an error is thrown. 




Members.html
Members.html has a navbar, containing a logout function. 
After the navbar, there is a container/row/column that contains class ‘member-name’
The members.js file has sent data to display in that section.

Members.js
Members.js is a simple file, that GETS the user data and displays it to .member-name which is a jquery command, it is adding the text to the .member-name class in members.html! This is all happening ONCE the document has fully loaded, which was done using the document.ready jquery command. 




Signup.html
The signup.html page has a form that collects the data of email and password and also hides the password just like the login page! There is an alert ID incase there is an issue with the email and password route designation. There is also a link that takes you to the login page, incase you want to log in! (/login is the route.)
Signup.js
Once submit button is pressed the data inside email and password is trimmed and assigned to a value. If the information provided registers, the user is sent to the members page if NOT you have to resubmit your information. If an error happens the function handleLoginErr will send an alert via jqeury.


(stylesheets) 
Style.css
The signup and login form both have a margin TOP of 50px which is linked and assigned in this css file! 



(Routes)

Api-routes.js
API routes starts by acquiring the models and passport files. 
The passport.authenticate is handling the password, and validates login credentials, if everything checks out, the user is sent to the login page via app.post with the credentials passed in. The signup route secures the information with help from Sequelize User Model.. 
If information cannot get passed through, the user is redirected to the err 401. 
The logout option (which can be accessed through the nav bar) redirects you to (/) which sends you back to the beginning. 
USERDATA for the members page, is GETTING  the users ID and EMAIL(never the password) and parsed via j.son. 




Html-routes.js

The middleware is going to check and see if user is signed in. The next step, IF user is signed in, they are sent to the members page, if not they will be sent to the sign up page. 
IF a user is not logged in and tries to access the members page, they will be redirected to the signup page. The html route file accesses the middleware a lot.
‘../public/login.html’ points to the html file that needs to be accessed which is in the public folder, same for the signup page. 


Node_modules 
All of your node_modules are the files that are attached to anything that was required, so - path, express, sequelize. All of these files are working from node modules, it's how they work. 






Package.json/Lock
Is a list of the dependencies needed for the application to work.







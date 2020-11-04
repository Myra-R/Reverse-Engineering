# Reverse-Engineering
AS A developer

I WANT a walk-through of the codebase

SO THAT I can use it as a starting point for a new project

The purpose of this app is:
Create sign up and log in 
Must sign up to get access to members page
Session only expires once logout is hit then you can login as member
Password is encrypted and stored with sequelize passport 

Server.js
Express and express session keeps track of when logged in 
Session ended when logged out

Sequelize 

User.js uses sequelize 
Before create function takes password, hash’s it and stores in database
Valid Password takes in specific users password decrypts it and compares against each other, if true will allow access to site else, false and will not allow access to site
Bcrypt is used to hash and unhash password – functions will not work unless this is ran 

Js file
Sign up.js
User enteres email and password with on click function, if empty will do nothing else it will 

User.js 
Calls api routes
	Api-routes.js 
		Makes sure user input is valid and directs to members page if valid 
		isAuthenticated checks if user is a valid user 
	once page is loaded and authenticated if valid it will send back email and id and display email on members page

if users clicks on “logout” app.get/logout which removed you out of express session with req.logout() then redirects you to sign up page 

html-route
app.get(“/”,  checks if you are a member, then redirect to member. Else redirect to sign up page
app.get(“/login”,  checks if you are a member, then redirect to member. Else redirect to login page

login.js 
user passes in email/password selcets login 
validates user has put in input and is vaild
calls the login user function which calls the /api/login for the post 
then calls the passport.authenticate function 

passport.js 

passport and passportlocal creates new instance that passes in email and password  and makes communication to usermodel and tries to find users info 
if email does not exist in passport.js api route it will return “incorrect email”
if email does exist then it will check is password is valid with validPassword()
Once entered it will check database to make sure password matches else it will say “incorrect password” if all is true then send back users data 

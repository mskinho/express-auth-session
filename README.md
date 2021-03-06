# Express Auth - Session
Inspired by [Hackathon Starter](https://github.com/sahat/hackathon-starter), this project is a more simplified boilerplate application with some basic examples of user authentication with [Passport](https://github.com/jaredhanson/passport) and authorization via an [ACL](https://github.com/OptimalBits/node_acl).  Authenticated user data is persisted in session cookies and on a MongoDB instance.

This project was originally presented at the [Front End PDX meetup](http://www.meetup.com/Front-End-PDX/events/231046123/).  If you'd like to view the slides presented at the meetup, they're available on [slides.com](http://slides.com/ajmueller/authentication-and-authorization-in-an-express-app).

## Services
This application has been designed to use the free tiers of these services to get a live development environment up and running with minimal effort.  In order to deploy this application as-is, you will need accounts from these services:

* [Heroku](https://signup.heroku.com/) - hosts the application.
* [SendGrid](https://sendgrid.com/pricing/) - used for email notifications.  Look for the free tier towards the bottom of the signup page.
* [mLab](https://mlab.com/signup/) - hosts the Mongo database.  This one is **optional** as you can add an mLab database directly to your Heroku instance without an mLab account.  However, if you'd like to have separate databases for your local development and Heroku environments, you will need to create an mLab account.

## Heroku Setup

* Fork this project to your own GitHub account.
* Sign up for or log into a Heroku account and create a new app.
* On your app, change the Deployment Method on the Deploy tab to "GitHub."
* Search for your forked project and connect your repository.
* On the Resources tab, search for "mLab" under Add-ons.  Add the mLab add-on, choosing the free sandbox plan.  This will automatically add the environment variable for `MONGODB_URI`.
* [Create an API key for your SendGrid account](https://sendgrid.com/docs/User_Guide/Settings/api_keys.html#-Create-an-API-Key).  Make sure it has full email send capabilities; it doesn't need anything else.
* On the Settings tab, add [the necessary environment variables](#environment-variables).
* On the Deploy tab, perform a manual deployment of the master branch.  Once the deployment is complete, you should be able to open your app.

## Local Setup

* Clone the repository locally.
* If you don't have Node installed, [install it](https://nodejs.org/en/download/).
* In a console window, navigate to the repository directory and install the dependencies with `npm install`.
* Create a new file at the root of the repository directory with the name `.env`.  Add [the necessary environment variables](#environment-variables).
* In your console window, execute `npm start` to launch the application.  It will be viewable in your browser at [http://localhost:3000/](http://localhost:3000/).

## Environment Variables
The below environment variables are needed to get the application up and running.

* `MONGODB_URI` - this only needs to be added manually if you are A) working locally or B) using your own mLab instance that you didn't provision through Heroku.
* `SENDGRID_API_KEY` - the API key you just created for your SendGrid account.
* `SEND_EMAILS_FROM` - the email address from which you will send notification emails.
* `SESSION_SECRET` - the secret key used to encode session data.
* `ACL_COLLECTION_PREFIX` - the prefix for the ACL data collection in the Mongo database.
* `MAX_LOGIN_ATTEMPTS` - the maximum number of login attempts a user can perform before being locked out.
* `LOGIN_ATTEMPTS_LOCKOUT_HOURS` - the amount of time, in hours, that a user is locked out of their account due to exceeding the maximum number of login attempts.
* `MINIMUM_PASSWORD_LENGTH` - the minimum length of user passwords.
* `PASSWORD_HASH_ROUNDS` - the number of rounds for bcrypt to apply its hashing algorithm.  The higher the rounds, the more secure the password is, but the more computing power is needed to hash passwords.  [Choose a number that best balances security and performance](http://security.stackexchange.com/questions/3959/recommended-of-iterations-when-using-pkbdf2-sha256/3993#3993).
* `PASSWORD_RESET_TIME_LIMIT_IN_HOURS` - the amount of time a user has to reset their password if they go through the "Forgot Password" process.
* `TZ` - the timezone of the server.  This is used to calculate times that are sent to users in emails regarding login activity.  Use [this list on Wikipedia](https://en.wikipedia.org/wiki/List_of_tz_database_time_zones) for reference using the TZ column.

## License

(The MIT License)

Copyright (c) Alex Mueller

Permission is hereby granted, free of charge, to any person obtaining a copy of this software and associated documentation files (the "Software"), to deal in the Software without restriction, including without limitation the rights to use, copy, modify, merge, publish, distribute, sublicense, and/or sell copies of the Software, and to permit persons to whom the Software is furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY, FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM, OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE SOFTWARE.

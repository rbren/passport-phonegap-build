# Passport-PhoneGap-Build

[Passport](http://passportjs.org/) strategy for authenticating with [PhoneGap Build](https://build.phonegap.com/)
using the OAuth 2.0 API.

This module lets you authenticate using GitHub in your Node.js applications.
By plugging into Passport, GitHub authentication can be easily and
unobtrusively integrated into any application or framework that supports
[Connect](http://www.senchalabs.org/connect/)-style middleware, including
[Express](http://expressjs.com/).

## Install

    $ npm install passport-phonegap-build

## Usage

#### Configure Strategy

    passport.use(new PhonegapBuildStrategy({
        clientID: CLIENT_ID,
        clientSecret: CLIENT_SECRET,
        callbackURL: "http://127.0.0.1:3000/auth/phonegap/callback"
      },
      function(accessToken, refreshToken, profile, done) {
        User.findOrCreate({ id: profile.id }, function (err, user) {
          return done(err, user);
        });
      }
    ));

#### Authenticate Requests

Use `passport.authenticate()`, specifying the `'phonegap-build'` strategy, to
authenticate requests.

For example, as route middleware in an [Express](http://expressjs.com/)
application:

    app.get('/auth/phonegap-build',
      passport.authenticate('phonegap-build'));

    app.get('/auth/phonegap-build/callback', 
      passport.authenticate('phonegap-build', { failureRedirect: '/login' }),
      function(req, res) {
        // Successful authentication, redirect home.
        res.redirect('/');
      });

## Credits
  Inspired by Jared Hanson's Github Strategy:
  - [Jared Hanson](http://github.com/jaredhanson)

## License

[The MIT License](http://opensource.org/licenses/MIT)



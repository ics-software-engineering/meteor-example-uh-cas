![](https://raw.githubusercontent.com/ics-software-engineering/meteor-example-uh-cas/master/doc/home-login.png)

## Installation

Download the system, cd in the app directory, then execute:

```
meteor --settings ../config/settings.development.json
```

The settings file is needed to provide CAS parameter information. Note that you won't be able to successfully login until you edit the [settings.development.json](https://github.com/ics-software-engineering/meteor-example-uh-cas/blob/master/config/settings.development.json) file to indicate that your UH account should be one of those allowed to login.

## Packages

You must invoke 'meteor add' to add the following packages:
 
  1. [atoy40:meteor-accounts-cas](https://github.com/atoy40/meteor-accounts-cas). 
  2. 'random' (from the meteor core)

## Walkthrough

Meteor-example-uh-cas is a fork of [meteor-application-template](http://ics-software-engineering.github.io/meteor-application-template/) that illustrates how to perform [University of Hawaii CAS authentication](https://www.hawaii.edu/bwiki/display/UHIAM/UH+Web+Login+Service+-+CAS+v3).

It defines a template called Cas_Login in [cas-login.html](https://github.com/ics-software-engineering/meteor-example-uh-cas/blob/master/app/imports/ui/layouts/cas-login.html) and [cas-login.js](https://github.com/ics-software-engineering/meteor-example-uh-cas/blob/master/app/imports/ui/layouts/cas-login.js).  
The Cas_Login template is invoked in  [header.html](https://github.com/ics-software-engineering/meteor-example-uh-cas/blob/master/app/imports/ui/layouts/header.html) to put the menu item in the navbar for logging in and out.

The [settings.development.json](https://github.com/ics-software-engineering/meteor-example-uh-cas/blob/master/config/settings.development.json) file provides the configuration parameters to the meteor-accounts-cas package. Note that only two users are allowed to sign in; you will want to edit this setting before adapting this code to your own application. 

Checking to see that only the users specified in the settings.development.json file are allowed is implemented in [accounts.js](https://github.com/ics-software-engineering/meteor-example-uh-cas/blob/master/app/imports/startup/server/accounts.js). This file defines a function for validating new users that checks the user-supplied account name against the list of authorized account names in the settings file.

After successful authentication, the home page shows the name of the logged in user and the menu changes to provide a logout link:

![](https://raw.githubusercontent.com/ics-software-engineering/meteor-example-uh-cas/master/doc/home-logout.png)

Note that UH CAS authentication saves a cookie that persists after logout. This means that after you logout, if you click the login button again, you will be immediately logged in without needing to re-enter your credentials. This, I guess, is a feature, not a bug.

## Credits

Thanks to [Yongwen Xu](https://github.com/yongwen) for the sample code.



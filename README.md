# Restaurant Menus Directory App #
This web based application stores and displays the catalog of restaurants and their corresponding menu items with detailed desription of each. The app is built with the help of Python's Flask MVC Framework together with SQLAlchemy ORM. The website allows users to login using OAuth 2.0 Facebook and Google authentication providers. Also, users can perform CRUD operations on their own restaurants and menu items, and they can get API enpoints for JSON represantation of menus and restaurants.

## Consists of ##
* `/static` folder with all images and stylesheets
* `/templates` folder with all the views or front-end code
* `client_secrets.json` for storing Google settings and `fb_client_secrets.json` for storing Facebook OAuth settings.
* `database_setup.py` to create a database
* `lotsofmenus.py` to add records to a database
* `project.py` - main backend controller
* `restaurantmenu.db` - database itself

## Running locally using Vagrant ##
* For the purposes of running this app locally, we would need to clone the Vagrant application from: https://github.com/WhiteHatJoker/fullstack-nanodegree-vm.git. Vagrant machine should have all the necessary settings and dependencies to be able to start our app, however if not, we would only need to install Flask and SQLAlchemy additionally. As soon as we get the Vagrant folder in our directory, please clone all of the code from the current repository to subfolder of the vagrant folder.

* As our project uses OAuth 2, we would need to register our app with Google and Facebook authentication providers. 
  * For that, go to `console.google.developers.com` and create a new project. Go to the Manage Apis and under Credentials, edit the OAuth Consent Screen with the information about your app and save it. Now, press Create Credentials and choose OAuth Client ID, further choose Web Application, give it a proper name. Under Authorized Javascript Origins puth `http://localhost:5000` as we will be running our app from that port. Under Authorized redirect URIs, put `http://localhost:5000/gconnect` and `http://localhost:5000/login`, press Create and you get the client ID and client secrets. Press download JSON file and save it as `client_secrets.json` in the app folder.
  * Let's also get the Facebook credentials by going to `https://developers.facebook.com/`, press My Apps, Create a New App and Choose Website option. Give the proper naming and as soon as you get the App ID and Client Secrets, open the `fb_client_secrets.json` file in our app folder and replace the relevant values.
  * Under our app folder go to `templates/login.html`, open it and replace the values on line 48 `data-clienid` with Google client ID and on line 118 `appId` with Facebook app ID, save the file and quit.

* Now, it is time to run the Vagrant application via terminal. I personally use git bash to get Linux command line for my Windows. Change directory `cd` to the Vagrant folder. Further, run `vagrant up`, followed by `vagrant ssh` to login to the Virtual machine. We would also need to `cd /vagrant` and go to the folder with current repository.

* Now, run `python database_setup.py` to create a database, `python lotsofmenus.py` to fill in the database with records and `python project.py` to start the app in the browser. Now open your browser and go to `http://localhost:5000` and Enjoy.
## Moving app to Heroku ##
* If you want to move this app online, follow this instructions on how to deploy this app on Heroku: https://www.udacity.com/wiki/ud330/deploy

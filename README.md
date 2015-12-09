
# Building a RESTful API

This repository contains the base code for a simple API plus instructions on how to configure and deploy it to, a cloud server provider. This will form the basis of your assignment for 305CDE.

Heroku provide a free hosting tier and make it really easy to deploy your API. Unline other material in this module you will need to be working with a separate git repository containing only a single NodeJS project, your assignment API for example. Start by creating a free [Heroku](https://www.heroku.com) account.

## Changing the Git Remote

Since you have cloned a readonly repository from GitHub you will need to create your own remote on GitLab and point this repository to this. Log into GitLab and create a private repository called **API**. Copy the git remote url and point your origin reference to point to this new remote, then push to it (substitute your new repository URL where indicated.
```
git remote -v
  origin	git@github.com:username/api.git (fetch)
  origin	git@github.com:username/api.git (push)
git remote set-url origin git@gitlab.com:username/API.git
git remote -v
  origin	git@gitlab.com:username/API.git (fetch)
  origin	git@gitlab.com:username/API.git (push)
git push origin master
```
You should now check that your new remote contains the project code.

## Updating NodeJS

Before developing your API you should ensure that Cloud9 is running the latest stable version of NodeJS (v5.2.0 at the time of writing) and set this as default.
```
nvm list-remote
nvm install 5.2.0
nvm alias default 5.2.0
node -v
```

## Understanding the Code

Lets take a look at the project files.

Open the `.jshintrc` file. This is the configuration file for the _JSHint linter_ which checks your code for issues. There are a number of options listed.

1. Make sure you understand the options by looking them up in the [JSHint Option Reference](http://jshint.com/docs/options/).

The `package.json` file is the _metadata_ associated with the _NodeJS project_.

1. Make sure you check the [documentation](https://docs.npmjs.com/files/package.json) so you understand the different fields.
  - the `scripts` field contains a `start` field. This is the command the server will run to start the app
  - the `engines` field contains a `node` field that specifies the version of node that will be installed on the remote server

## Installing and Configuring Heroku

Once you have created your **Heroku** account and logged in you need to download and install the [Heroku Toolbelt](https://toolbelt.heroku.com). Once this is installed you need to **log in**.
```
wget -O- https://toolbelt.heroku.com/install-ubuntu.sh | sh
  heroku login
  Enter your Heroku credentials.
  Email: username@email.com     
  Password (typing will be hidden):
  Authentication successful.
```
Next you need to navigate into the root of your Git repository (where this file is saved) and create a new Heroku project, replacing _project-name_ with your chosen project name. Each hosted project need to have a unique name so your first choice may not be available.
```
heroku create project-name
Creating project-name... done, stack is cedar-14
https://project-name.herokuapp.com/ | https://git.heroku.com/project-name.git
Git remote heroku added
```
This will create a new project on the Heroku servers and will also add a _heroku git remote_. You can check this has happened.
```
git remote -v
  heroku    https://git.heroku.com/project-name.git (fetch)
  heroku    https://git.heroku.com/project-name.git (push)
  origin	git@gitlab.com:username/API.git (fetch)
  origin	git@gitlab.com:username/API.git (push)
```
You can also set the new remote using `heroku git:remote -a project-name`

## Running the API through Cloud9

During the development process you should always run your API through the Cloud9 IDE and only deploy to Heroku when you have a working version.

Open the index.js file in the Cloud9 editor. Now click on the **Play** button in the top toolbar. This will open an _run window_ and attempt to start your API. If successful you will see the URL where you can access your live API. Copy this and paste into a new browser tab. You should see the text `Hello World!` in the web browser.

## Deploying to Heroku

You can deploy your app to the Heroku cloud by pushing to the heroku remote.
```
git push heroku master
```
You can now view your API by visiting the supplied url.
```
https://project-name.herokuapp.com/
```

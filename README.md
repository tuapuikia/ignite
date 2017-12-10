![Ignite Logo](https://i.imgur.com/9hUWSlu.png)

# Ignite

> Reproducible Deployment Management, Dependency and Configuration Management System

[![npm version](https://badge.fury.io/js/ignitejs.svg)](https://badge.fury.io/js/ignitejs) [![Build](https://travis-ci.org/ignitejscl/ignite.svg?branch=master)](https://travis-ci.org/ignitejscl/ignite) [![license](https://img.shields.io/github/license/mashape/apistatus.svg?maxAge=2592000)](https://opensource.org/licenses/MIT)

Ignite is a deployment and dependency management system designed to be reproducible universally. 

## Features

- Simple, easy-to-use command line interface
- One-command installation
- Easily share projects
- Manage dependencies and configuration
- Automatic dockerfile creation

## Installation

To run Ignite you will need NodeJS installed on your local machine. You can find out how to install NodeJS [here](https://nodejs.org/en/)

Once NodeJS and NPM are installed, run:

```shell
npm install ignitejs -g
```

## Usage

Let's create a simple project with ignite, first make a new directory for the project and change into that directory:

```
mkdir hello_world_project && cd hello_world_project/
```

Now, let's run ```ignite init``` and fill out some basic information...

```shell
ignite init
```

You'll be asked to fill out a few simple questions, here's the questions and sample answers:

```
? What's your name? Michael
? What is the project's name? ignite_helloworld_example
? What's the version number? 0.0.1
? What's the project about? This is a sample project for Ignite to get using Ignite
? Package dependencies? Seperated by commas (,). Ex: chalk,express chalk,express,ora
? Git Repository Link https://github.com/ignitejs/helloworld_example
? What file will be the start file? Ex. index.js index.js
? Use Docker? (y/n) n
? Create Dockerfile? (y/n) n
```

Once completed, you will get a response like this:

```
✔ Created configuration file.
✔ Saved configuration file
```

If you're interested to see how it's compiled, check the ```.ignite-config.js``` file, it should look something liket his:

```javascript
/** ------ Generated by Ignite ------ */
/**
 * @name ignite_helloworld_example
 * @version 0.0.1
 * @author Michael
 * @description This is a sample project for Ignite to get using Ignite
 */
 module.exports = {
     name: "ignite_helloworld_example",
     version: "0.0.1",
     author: "Michael",
     description: "This is a sample project for Ignite to get using Ignite",
     dependencies: ["chalk","express","ora"],
     git: "https://github.com/ignitejs/helloworld_example",
     scripts: {
         "test": "exit 0",
         "start": "node index.js"
     },
     config: {
         use_docker: false,
         create_dockerfile: false,
         dockerfile: false
     }
 }
```

Now, if we want to install this, just run:

```
ignite install
```

You should see output similar to this:

```
Ignite: Installing project dependencies for you now!

✔ Wrote package.json file
✔ Installed dependencies successfully.
Installed chalk successfully
Installed ora successfully
Installed express successfully
```

Now, if you list the contents in the directory you'll see everything is installed. 

## Sharing your project

Now that we've made a configuration file, we can create all the code we need, and then run ```ignite share```

You'll get output similar to:

```

Ignite: Let's generate a share file and readme to distribute

✔ Created tar stream, and saved as 'ignite-bundle.tar'
Now you can distribute your friends the ignite-bundle.tar and they just need to run: npm install ignitejs && ignite install to get everything started
```

Now, all your important files, including the ignite configuration file are bundled up, you can put this anywhere you want, and extract it, then run ```ignite install``` again.

## Features in development

- Creating an ignite server to host shared files securely (with authentication)

## Release Information

Saturday, December 9th, 2017 - Initial Release
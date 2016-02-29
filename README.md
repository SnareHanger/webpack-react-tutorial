# webpack-react-tutorial
Basic tutorial front to back to setup ReactJS with webpack

# Why???

> "Another tutorial?  There's so many out there already." - The Internet

Yes...there are.  My friend was talking to me one day about how every tutorial he's seen with React and Webpack assume you know some things already.  So I'm gonna go through it step by step, as if you were a complete idiot without being condescending.

# The What

1. Creating a new project
2. Installing npm
3. Initializing the project with NPM
4. Installing the packages we want (React, Webpack)
5. Basics with webpack
6. Setting up the webpack.config.js file
7. Writing some components with React in ES6!

# The New Project

This part, super simple.  Create a new folder anywhere on your computer.  I'm doing this on Windows, so I have my project sitting in C:\Users\Michael\Documents\Github\webpack-react-tutorial

# Installing NPM

First question...do you have npm installed?  

1. Of course I do
2. I think so?
3. What's NPM?

If you answered 1, skip down to Step 3.

If you answered 2, open up your command prompt (Windows) or terminal (OSX/Linux) and type `npm --version`.  If you get back a version number, skip to Step 3.  If not, you don't have it installed.

If you answered 3, NPM stands for Node Package Manager. It's an easy way to install javascript libraries through Node.js.

To install NPM, go to the [Node.js site](https://nodejs.org/en/) and install the latest version of Node.js which will include NPM.  Run through the installer as is with whatever options selected that it gives you.

# Initializing the project with NPM

Super easy, in the command prompt or terminal, navigate to your project folder, so in my case: `cd C:\Users\Michael\Documents\Github\webpack-react-tutorial`.

Then type `npm init`.  This will give you a wizard of sorts to help setup your project.  Hit enter after each step

- `name`: The name of your project (by default will be the name of the folder)
- `version`: `1.0.0` Defaults to 1.0.0, but you can be fancy and start with 0.1.0 if you like
- `description`: Description of your project.  You can leave it blank, but it probably helps to describe it.
- `entry point`: `index.js` This is the javascript file where everything will start at.  Think of it like the main trunk of a tree.  Defaults to index.js, let's stick with the default
- `test command`: `(blank)` For now we'll leave this blank, but this is to be used for testing our code.
- `git repository`: `(blank)` this can be blank, odds are if you're doing this, you don't need to put it in a git repo.
- `keywords`: `(blank)` Mostly useful for when you're creating an NPM package for other people to install.  Makes it easier to find.  Leave it blank.
- `author`: Your name.  Real, fake, github user account, whatever you want.
- `license`: `(ISC)` [So many options](https://opensource.org/licenses/alphabetical), but let's stick with the default, ISC

It will then show you the JSON content for you to confirm that it looks good.  If it looks good.  Hit enter.

# Installing npm packages

For this project, as of this moment, we're going to just need Webpack and ReactJS

In your command prompt or terminal, type `npm install webpack -g` and hit enter.

So what happened here?  `npm install webpack` is fairly obvious.  You're asking NPM to install the package called webpack.  The `-g` tells NPM to install the package globally.  Since Webpack is more of a tool than a library, this lets us use Webpack for any project in the future without needing it to be a part of the individual project. 

Next we're gonna install ReactJS.  Type in `npm install react --save`.  This installs the react library and the `--save` option adds react to the package.json file.  Go ahead and look, I'll wait.

The `--save` is good in the case that you share this project with other people or you need to delete your `node_modules` folder, where NPM installs packages, for some reason.

# Basics with Webpack

First off...what the hell is Webpack?  Webpack is a module bundler.  This means it takes all your individual javascript files and compiles them together in a smart way into a single file so when you're using this with a real website, the browser only needs to download a single javascript file instead of 10 or 100 files.

Let's do something real basic here.

Create a file called `index.html`.  If you're lazy, you can grab my index.html file.

Just set up a super basic html page, with a `<span id="name"></span>`

Also, you're going to want to add a reference to a script that currently doesn't exist, but it will soon.

So in the `<head>` tag, add `<script src="bundle.js"></script>` and save the file.

Next we're gonna create `index.js` and put some super simple javascript in there.

```javascript
document.addEventListener('DOMContentLoaded', function() {
    document.getElementById('name').textContent = 'Your name here';
});
```

Save the file.

Now, head back to the command prompt or terminal and in the root folder of your project, type `webpack index.js bundle.js`.  If everything is good you should get something like this:

```bash
Hash: b3c8fd7a7e03f5a5057b
Version: webpack 1.12.14
Time: 39ms
    Asset     Size  Chunks             Chunk Names
bundle.js  1.51 kB       0  [emitted]  main
   [0] ./index.js 121 bytes {0} [built]
```

What happened there is webpack took your code from index.js and created a module out of it, and added it to bundle.js for use in the project.

If you open up index.html in a browser, you should see your name pop up in that span tag you created.

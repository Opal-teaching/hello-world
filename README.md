# Hello World the Opal Way

## Description

This assignment will introduce you to the front-end technologies used in the Opal app. You will go through an overview of the
dependency managers, the set-up of a typical web-app and a coding example in the form of a "hello world" application.

By the end of this module, you should be a bit more familiar with the Opal application set up, the common AngularJS flow, 
OnsenUI, and ultimately how to set up a project using these technologies.

## Background

To help you follow this assignment, you should first familiarize yourself with the following topics. 
You can use the resources listed below or any others of your choice.

  - HTML introduction: [W3Schools](https://www.w3schools.com/html/default.asp).
    Please read all of this guide. It's important for you to understand the basic HTML tags, as Angular builds on top of them to 
    create its own tags which have enhanced functionality.
  - JS introduction: [W3Schools](https://www.w3schools.com/js/default.asp).
    This is a great introduction to how JavaScript interacts with the DOM (Document Object Model) natively. 
    Every year the [ECMAScript](https://en.wikipedia.org/wiki/ECMAScript) organization gets together and decides on how the 
    JavaScript standard for the web is going to evolve. This will include neat new features, or simply fixes to the previous API. 
    Their main job is to provide an API that JavaScript uses inside a browser to interact with the DOM tree, and other 
    important functions such as requests to a server via [get or post requests](https://www.w3schools.com/tags/ref_httpmethods.asp).
    Angular builds on top of this basic JavaScript API in two ways: it creates more complex functionality and it wraps 
    this functionality to offer it to the user under the Angular paradigm.
  - Git tutorial by Logan Montgomery: 
    [Git tutorial](https://docs.google.com/document/d/16PSag95XtbPKWGNi2K5PCtYNoGMo-haOJV3nsPXc2Z0/edit?usp=sharing). 
    Please go through this tutorial which covers some of the basics of Git.

## Resources

This may be a lot of new material for you to process. To help, here are some additional resources which you may refer to as needed.

  - [AngularJS Documentation](https://docs.angularjs.org/api)
  - [OnsenUI Documentation](https://onsen.io/v1/guide.html)
  - [Style Guide for AngularJS](https://github.com/johnpapa/angular-styleguide/blob/master/a1/README.md)
    <br>
    Please use this style guide when writing your AngularJS code. It makes the code clean, consistent, and easy to use 
    for the people who will follow you.
  - [Webpack Documentation](https://webpack.js.org/concepts/)

## Instructions

The instructions below will guide you through the process of creating a simple "hello world" application from scratch.
After following this mini-tutorial, you should have an idea of what the config files do in an Angular application, how you'd go 
about creating them and how to create a basic web app, i.e. Hello World the Opal front-end way :)

1.  Make sure you're comfortable using the command line terminal in your chosen operating system.
    You should also have access to an IDE of your choice, for example, [WebStorm](https://www.jetbrains.com/webstorm/), 
    which is free for students. In addition, if you're using a Mac without root access, you may need to precede all npm commands 
    with `sudo` (e.g. `sudo npm install ...`).
    
2.  Install the latest version of [NodeJS](https://nodejs.org/en/download/).
    Verify that Node and its package manager, npm, were correctly installed by running `node -v` and `npm -v` in a terminal.
    We will be using npm as our front-end dependency manager.
    
3.  Create a new directory for this assignment and navigate to it in a terminal. Also open the folder in an IDE.
    
4.  Run the following command:
    ```
    npm init
    ```
    This will initialize your project by creating a config file called `package.json`.
    It will ask you common questions relating to your project's set up, such as asking you to provide a description, 
    version number and name for your project.
    You can press enter without typing an answer to leave the default (shown in parentheses) for any given line.
    Do this for all lines except author (write your name) and description (write `The first assignment of Opal bootcamp.`).
    <br><br>
    After completing this setup, a `package.json` file will be created in your root project folder.
    Open it and see what was added. Here, you can change anything you answered during `npm init`.
    In addition to giving some background information on your project, `package.json` will be used by npm to track your project's
    dependencies. As we install dependencies, you will see them automatically added to this file.
    
5.  Install webpack, and webpack's dev server and command line, as development dependencies for your project (warnings are 
    fine, as long as there are no errors): 
    ```
    npm install webpack@4.42.1 webpack-dev-server@3.11.2 webpack-cli@3.3.11 --save-dev
    ```
    [Webpack](https://webpack.js.org/concepts/) is a static module bundler for JavaScript applications. We will be using 
    webpack-dev-server to build and serve our application in a browser.
    <br><br>
    The `--save-dev` flag instructs npm to add the installed dependencies to `package.json` under "devDependencies".
    These dependencies are needed during development, but not when building a production version of the app.
    <br><br>
    The `@` symbol is used to specify a specific version to install. When creating a new project from scratch, you 
    generally won't need to specify version numbers (for example, `npm install webpack --save-dev` will install the latest 
    version). However, this "hello world" project uses specific version of all dependencies to ensure that it still 
    runs correctly years from now (since sometimes the latest version of a dependency can introduce new requirements that aren't 
    covered in this guide).
    <br><br>
    After running this command, open `package.json`. You will see that these three new dependencies and their version numbers
    have been added. The command will also have created a `node_modules` folder, which will contain the installed dependencies, 
    and a [package-lock.json](https://docs.npmjs.com/configuring-npm/package-lock-json.html) file, which is a trace of everything 
    that was installed. Both `node_modules` and `package-lock.json` will contain many more packages than the three you installed. 
    This is because npm installs all of those packages' dependencies as well.
    
6.  Next, it's time to install our two major frameworks as front-end dependencies:
    ```
    npm install angular@1.8.2 --save
    npm install onsenui@1.3.17 --save
    ```
    Here, the `--save` flag instructs npm to add the installed dependencies to package.json as actual project dependencies 
    (under "dependencies"). Note than when installing a new dependency using npm, **you should always use the --save-dev or 
    --save flag**. If you don't, anyone who tries to install your project using `package.json` will be missing some of the 
    dependencies they need.
    <br><br>
    In the case of Angular and OnsenUI, newer versions have been released that completely change their usage and syntax. 
    Since we want to use the same older versions as Opal, we must specify which older versions to install.
    <br><br>
    OnsenUI and AngularJS are the two main JavaScript dependencies we use in the app.
     - AngularJS provides a framework for the logic of a web-app that builds on top of the **MVC** design pattern. 
       Here is a small introduction: https://docs.angularjs.org/guide/concepts.
     - OnsenUI is a CSS/JavaScript library that provides out-of-the-box components that mimic a mobile user interface. 
       This allows our web-app to look and feel like a mobile app.
       Look through the start page on OnsenUI https://onsen.io/v1/guide.html,
       Please note that we will be working with version 1 of this framework. When you're going through the documentation,
       make sure you're consulting the right version.
     
     After running this command, open package.json. You'll see that it was updated with a new dependencies section that lists both
     Angular and OnsenUI.
    
7.  Next, create a folder called `src` in the root folder of your project. In it, create an `index.html` file which will be 
    the starting point of our web application.
    Add the following code to this file:
    ```
    <!DOCTYPE html>
    <html lang="en">
    <head>
        <meta http-equiv="content-type" content="text/html; charset=utf-8" />
        <title>Opal Hello World</title>
    </head>
    <body>
        <h3>This is index.html</h3>
    </body>
    </html>
    
    ```
    
8.  Then, inside `src`, create a folder called `js`, and in it, a file `app.js` (its full path will be `src/js/app.js`). 
    Also create a folder in `src` called `views`, and create a file in it called `hello-world.html`. We will add to these later.
    
9.  Now, we'll set up webpack-dev-server to serve the application. In the root of your project folder (alongside `package.json`),
    create a file called `webpack.config.js`. This file will contain all the configurations we need to use webpack.
    Add the following content:
    ```
    const CopyPlugin = require('copy-webpack-plugin');
    const HtmlWebpackPlugin = require('html-webpack-plugin');
    const path = require('path');
    
    let entry = [
        "./src/js/app.js"
    ];
    
    module.exports = {
        entry: entry,
        devtool: 'eval-cheap-source-map',
        mode: 'development',
        devServer: {
            contentBase: './www',
            compress: true,
            hot: false,
            watchContentBase: true,
            liveReload: true,
            port: 9001
        },
        output: {
            path: path.resolve(__dirname, 'www'),
            filename: '[name].[hash].js',
        },
        module: {
            rules: [
                {
                    test: /\.html$/,
                    loader: 'raw-loader',
                },
                {
                    test: /\.js$/,
                    exclude: /node_modules/,
                    use: {
                        loader: 'babel-loader'
                    }
                },
                {
                    test: /\.css$/,
                    use: ['style-loader', 'css-loader']
                },
                {
                    test: /\.(woff(2)?|ttf|eot|svg)(\?v=\d+\.\d+\.\d+)?$/,
                    use: [
                        {
                            loader: 'file-loader',
                            options: {
                                name: '[name].[ext]'
                            },
                        }
                    ]
                },
                {
                    // Allows Onsen to compile with Webpack
                    test: /onsenui.js/,
                    loader: 'imports-loader?this=>window!exports-loader?window.Modernizr'
                },
                {
                    // Allows Onsen to compile with Webpack
                    test: /onsenui.js/,
                    loader: 'imports-loader?define=>false,module.exports=>false'
                },
            ]
        },
        plugins: [
            new CopyPlugin({
                patterns: [
                    { from: './src/views', to: './views' },
                ],
            }),
            new HtmlWebpackPlugin({
                template: './src/index.html',
            }),
        ]
    };
    
    ```
    Here's an explanation of what each part of this config file is used for:
      - `entry`: used to specify the entry point js files for our application. We'll add more to this later.
      - `devtool`: specifies which method to use to generate source maps, which allow us to debug minified code.
      - `mode`: affects webpack's optimizations. For now, we're only concerned with using `development` mode.
      - `devServer`: these are the configurations for webpack-dev-server, which we'll use to launch the app.
        Of particular interest here are `contentBase` (which should match `output.path`), `watchContentBase` and `liveReload`, 
        which allow the browser to reload changes to the source files without having to relaunch webpack-dev-server,
        and finally `port`, which can be changed to a different value if the one chosen is already in use.
      - `output`: the output folder for the application build. Webpack-dev-server only builds in memory, so you won't see 
        `www` be created, but webpack can also be used to build an app bundle to this folder directly.
      - `module.rules`: this section contains rules on how to load each type of file while serving the app.
      - `plugins`: we're using two plugins: CopyPlugin to make the views (which will be added later) accessible in
        the served app, and HtmlWebpackPlugin to serve our html files.

10. Before we can serve the app using webpack-dev-server, we'll need to install all the dependencies referenced in the 
    `webpack.config.js` file:
    ```
    npm install copy-webpack-plugin@6.4.0 html-webpack-plugin@3.2.0 --save-dev
    npm install css-loader@5.2.6 exports-loader@0.7.0 file-loader@5.1.0 imports-loader@0.8.0 raw-loader@4.0.0 style-loader@1.1.3 --save-dev
    npm install @babel/core@7.9.0 babel-loader@8.1.0 --save-dev
    ```
    The first line installs the required plugins; the second, the loaders used in `modules.rules`; and the third, babel, 
    which is used to interpret .js files.

11. In addition, to run webpack, we'll set up a short npm script that we can use as a shortcut. 
    Add the `start` script to package.json:
    ```
    "scripts": {
        "start": "webpack-dev-server --open --watch --progress --colors",
        "test": "echo \"Error: no test specified\" && exit 1"
    },
    ```

12. Next, try out your webpack setup by running `npm run start` (this will launch the script you've just added). 
    A browser window should open (this tutorial will use Chrome as an example), and you should see `This is index.html`. 
    To test for errors, check the console by inspecting the page and choosing `console` on the top bar of the browser. 
    Also disable the cache by going into the `network` tab of the debugging tools and 
    [selecting](https://www.technipages.com/google-chrome-how-to-completely-disable-cache)
    the `disable cache` box. If you get an error about `favicon.ico`, it's fine.

13. At this point, you've successfully set up a simple html page to run locally in your browser. However, this
    setup hasn't made use of Angular or OnsenUI yet. Now it's time to start building the app using Angular. An Angular app is 
    bootstrapped by the module config function. To make use of this, we need to add the following.
    First, add an angular directive (ng-app) to `index.html`'s body tag to tell Angular where to start nesting the application.
    ```
    <body ng-app="HelloWorld" ng-cloak>
        ...
    </body>
    ```
    Here, we have told Angular to start our HelloWorld application from the body tag of our html tree.
    We have also told Angular to hide placeholders while they load their values using ng-cloak.
    <br><br>
    The `index.html` page is the only page that will be loaded in the application. Angular will take care of dynamically 
    swapping dependencies in and out within that page. It will also control state via Angular directives which start with `ng`.
    <br><br>
    Second, instantiate the module, by adding the following to `app.js`:
    ```
    import angular from "angular";
    import "onsenui/js/onsenui";
    import "onsenui/css/onsen-css-components-blue-basic-theme.css";
    import "onsenui/css/onsenui.css";

    const app = angular
        .module('HelloWorld', ['onsen']); // Defines the HelloWorld module and its dependencies

    ```
    Here, we are importing four components. Two Javascript components (Angular and OnsenUI), 
    as well as two stylesheets from OnsenUI.
    Angular.module will create an Angular module with the specified name (using the same name used in the ng-app directive)
    and will declare the set of Angular dependencies for that module (`onsen` will be its only dependency).

14. Note that we have already linked app.js to `webpack.config.js` to specify that this file is the entry point to our application:
    ```
    let entry = [
        "./src/js/app.js"
    ];

    module.exports = {
        entry: entry,
    ```

15. We are now ready to add logic to the app. We will create an onsen navigator, an onsen page, and finally add 
    some logic to display "hello world".
    <br><br>
    In the `index.html` file, add an onsen navigator between the <body> tags, and remove the "This is index.html" header:
    ```
    <body ng-app="HelloWorld" ng-cloak>
        <ons-navigator var="navi" page="./views/hello-world.html"></ons-navigator>
    </body>
    ```
    This navigator instantiates the global variable `navi`, which will allow you to add and remove pages.
    The url in the page attribute points to the root page for the navigator. The navigator creates a stack from which 
    you can push and pop new pages. See [page navigation](https://onsen.io/v1/guide.html#page-navigation) for details.

16. Open the file called `hello-world.html` in the `views` folder. This will
    be the initial view displayed by the navigator. To this view, add the following code:
    ```
    <ons-page ng-controller="HelloWorldController as vm">
        <ons-toolbar>
              <div class="center">Navigation Bar</div>
        </ons-toolbar>
        <div style="text-align: center">
              <!--TODO: Add a binding from the controller to print hello world on the page.-->
        </div>
    </ons-page>
    
    ```
    Notice the TODO task which will require you to add a binding to a variable from the HelloWorldController. 
    This html page creates and ons-page component, which is the type of component that can be pushed onto an onsen navigator. 
    The ng-controller tag indicates the controller use for this view.

17. Create a new folder called `controllers` inside `js`. Create a new file called `helloWorldController.js` in this folder 
    (its full path will be `src/js/controllers/helloWorldController.js`).
    Add the following contents to this file:
    ```
    (function(){ // Wraps the controller in an Immediately Invoked Function Expression (as per the Johnpapa style guide) to limit variable scope
        'use strict';

        angular
        .module('HelloWorld') // Fetches the angular module so that the controller can access it
        .controller("HelloWorldController", HelloWorldController); // Declares the controller component in the angular module and connects it to the function below

        HelloWorldController.$inject = []; // Injects the angular dependencies for this controller (there are none)

        /* @ngInject */
        function HelloWorldController() { // Function representing this controller
          const vm = this; // vm is the equivalent of $scope
          // TODO: Create and attach a hello variable to the vm object.
        }
    })();
    
    ```
    Notice the `(function(){})();`. This will encapsulate the code as to not let variables escape from its scope.
    Declaring variables in a JavaScript file without function encapsulation risks causing collisions
    between variables in different files in the project.

18. This controller is referenced by the hello-world view, but it needs to be linked to the rest of the application
    via webpack in order to be correctly loaded on launch. To do this, create a new file `src/js/app.controllers.js`:
    ```
    import "./controllers/helloWorldController.js";
    
    ```
    In `webpack.config.js`, add the following line to specify that this file should be read on entry alongside `app.js`:
    ```
    let entry = [
        "./src/js/app.js",
        "./src/js/app.controllers.js"
    ];
    ```

19. If you've left webpack running, it will have reloaded for you every time you saved new changes. 
    However, it will not reload changes to `webpack.config.js`. Since you've made changes to this file, you'll need to 
    restart webpack. Do this by cancelling the running process and re-running `npm run start`.
    <br><br>
    Check that the app still runs correctly and there are no errors in the console. Now, you should see only the 
    navigation bar, since this is the only visual component in the hello-world view.

20. Finally, it's time to display "Hello World". In `helloWorldController.js`, replace the TODO line with the following:
    ```
    vm.hello = "Hello World!"; // Declare a controller variable than can be used in its view
    ```
    Then, to use the controller variable 'hello' in the view, in `hello-world.html`, replace the TODO line with the following:
    ```
    <h1>{{vm.hello}}</h1>
    ```
    In the view, vm refers to the controller "`as vm`", and `hello` is the variable defined in this controller. The curly brackets 
    are used to express the contents of the variable instead of printing `vm.hello` in plain text to the screen.
    <br><br>
    Since you've only made changes to project files (not to `webpack.config.js`), webpack will have updated the running instance 
    automatically. Look at your browser and check that "Hello World!" is now visible.

__Success__!!! You have now gone through the basic steps to get an AngularJS app running with Opal's front-end technology stack!

If you have any issues with the above instructions, please contact the bootcamp runner.

Web based ontology and partitioning tools
==========================================

- Architecture

![alt text](https://github.com/aalzeitoun/Web-based-ontology-partitioning-and-analysis-tool/blob/master/Architecture_img.png?raw=true)


!NEW
(23/08)

Added new field in /options called 'url' If this field is empty, then parsing will be done for a file, otherwise updates will be attempted on a URI

Added REST endpoint on /metrics which display the metrics as a result of the RDFSTORE

[{"name":"class","value":3},{"name":"individual","value":3},{"name":"blank","value":2},{"name":"literals","value":2},{"name":"dataprop","value":0},{"name":"objprop","value":1}]



Added module glob, used for searching for files in the root and then deleting them.


Added new function for initializing edges> initEdges() this one creates the metrics and updates the edges with the filter information


Refactoring of /ontology/edges, which is now using initEdges()

JAVA puts the generated JSON files the root (next to package.json ), added new function using GLOB which looks for the generated files and then deletes them (maybe better to move them?) Sometimes files like family1.json are generated and moving a file by patter file.json does not delete additional files like file1.json (that's why GLOB was used)

Modified the parser page to include the additional metrics (these are in fact only the blank node and literal count) but for now displaying all


(5/07) Added REST endpoint on /ontology/filters. Modified edge name to have also the namespace in front. Refactored code.
(14/06) Moved app.js to folder app
(7/06) Added less . All less code goes into less/layout.less using variables defined in variables.less.

To generate a new CSS, type in command line:




>>>>  lessc app/public/less/main.less > app/public/css/style.css <<<<





The application runs on port 4000. The main entry point for the application is app.js


Open app in browser at >>>>> http://localhost:4000 <<<<<<


All the frontend is served from within the public folder (index.html)

Directory structure


-app


--bin


--components


--data


--js


--public (expressJS will serve this folder--> AngularJS files are hosted here)


  --components (AngularJS components)


  --css (AngularJS css)


  --js (AngularJS everything javascript)


    --controllers (AngularJS controllers)


  --views (AngularJS views)


  --routes (ExpressJS routes - if needed )


--views (ExpressJS views - if needed)


--node_modules (self explanatory)




To run the application simply type in a command line 'npm start' - this will trigger node to run on port 4000 on your PC. You should run "git bash" (we recommend git scm download).
You might want to:

1. run >>>>>> npm install <<<<<<<<< first to install all dependencies needed (package.json)
2.  run >>>>>> bower update <<<<<<<<< first to update all bower dependencies needed (.bowerrc) (check here for more info on bower: http://bower.io/docs/api/)

Two important files that define the dependencies:

1. package.json

body-parser


express


python 2.7.3 (other versions NOT supported by node-gyp!!)



2. bower.json -> angularjs, bootstrap, angularcookies etc



To update the dependencies automatically from respositories:
1. npm update
2. bower update


1) angularjs
==================

AngularJS running on  NodeJS. Great tools are included like Bower, Bootstrap. Additional Angular goodies are added:  angular route.


1. Install nodejs

Node.js is a cross-platform runtime environment for server-side and networking applications. Node.js applications are written in JavaScript, and can be run within the Node.js runtime on OS X, Microsoft Windows and Linux with no changes.
(ref: http://stackoverflow.com/questions/1884724/what-is-node-js)
How to install:
- use a windows package manager (such as Chocolatey)
- manually install (add environment variables and run node in command line to verify)

Advisable:
- use helpers such as Underscore

2. Install npm

npm is a NodeJS package manager. As its name would imply, you can use it to install node programs. Also, if you use it in development, it makes it easier to specify and link dependencies.

npm is included in the nodejs installation

      2.1. Updating packages

      npm update

      2.2. Make a package: the package.json file

      The package.json file goes in the root of your package. It tells npm how your package is structured, and what to do to install it.
      Most of the time, you only need the "name", "version", and "main" fields (even for node-waf compiled addons).

      To interactively create a package.json file, use the npm-init command (ref: https://www.npmjs.org/doc/cli/npm-init.html )

      2.3. Create package.json file

      - Use npm-init command to generate the package.json file (ref: http://stackoverflow.com/questions/9961502/is-there-a-way-to-automatically-build-the-package-json-file-for-node-js-projects )

      Edit the package.json file:

      - specify engines  (ref:   https://www.npmjs.org/doc/files/package.json.html )
      - add scripts (run them from command line)
    "scripts": {
     "start": "node ./app/bin/www",
    "less": "lessc app/css/style.css > app/css/style.css"
  }

3. Install bower

    3.1. Run: npm install bower (or npm install -g bower to add it as dependency into package.json)
    3.2. Change bowers default components folder (ref: http://stackoverflow.com/questions/14079833/how-to-change-bowers-default-components-folder)

    Create a .bowerrc in the project root with the content

    {
      "directory" : "app/components"
    }
    3.3. Add bower to the $PATH (http://stackoverflow.com/questions/12369390/bower-command-not-found)
    3.4. Test by typing bower in command line. Do a bower init to register your packages (follow the options on screen)
    3.5. Run bower update to install components (bootstrap, angular, etc) basically whatever you have defined in bower.json
4. Install helpers with bower

- bootstrap (UI): bower install bootstrap ( + bootstrap additions )
- underscore (for arrays and others) : bower install underscore
- moment (for dates) :  bower install moment

5. Create folder structure

- app (main AngularJS folder)
  - components (bower components)
  - css (files less or css)
  - js (directives, controllers, services)
  - views (views grouped by features)
  - fonts (font files)
  - images
  - languages (internationalization)

6. Add your first controller/view
controllers/aboutCtrl.js - views/about.html
controllers/homepageCtrl.js - views/homepage.html

7. Include the controller/view and run the app

- modify app.js and include the controllers
- run the app: npm start (*please note that it's the script in the package.json file)



2) Express
==================
Install express

npm install --save express

(check your package.json file - express should then be saved as a dependency)

app.js runs a simple server; run from the root the following command


3) JS library for parsing RDF
=========================

3.1) Install Python

npm install --save python -g (global)

Set python environment variable

3.2) Install the library

npm install -- python

RDF store - https://github.com/antoniogarrote/rdfstore-js

4) vis.js for visualization  
=========================

Install via bower:

    bower install vis


5) OWL2VOWL


for ontology parsing into JSON

JAVA must be installed

https://github.com/VisualDataWeb/OWL2VOWL



java -jar owl2vowl.jar -iri "http://ontovibe.visualdataweb.org"


java -jar owl2vowl.jar -file ontologies/foaf.rdf




6) How to
=========================

5.1. Add new modules in Express

To add new node modules the app, simply add a new file in app/js/partials then include it in app.js (see the example for errors)

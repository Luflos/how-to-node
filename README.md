# How To Node

#### How to get started with node projects

- First create a new folder for a node project

```
mkdir name-of-project
```

- CD into the project folder

```
CD name-of-project
```

- Initialize the NPM inside your project folder

```
npm init
```

- At first various promps will show up and you can enter whatever values you want.
<details>
 <summary>Click to see what the prompts are</summary>
  <ul>
   <li>package name: (testing)</li>
   <li>version: (1.0.0)</li>
   <li>description:</li>
   <li>entry point: (index.js)</li>
   <li> test command:</li>
   <li> git repository:</li>
   <li> keywords:</li>
   <li> author:</li>
   <li> license: (ISC)</li>
  </ul>
</details>\\


If you would just like to accept all the defaults type 
```
npm init -y
```

- Check to make sure there is a package.json file.
The file should have the values you set up. 

- Create the index.js file (unless you specified a different file name in the package.json) by
 ```
 touch index.js
 ```

- Verify your code is running with console.log
```
console.log('Howdy do')
```

- Run the file in node with `node index.js`

### NODE MODULES
- You can create your own modules
 For example, create a js file called `myModule.js`
- `module.exports` is an object that will hold the code to be exported
- to test, inside the `myModule.js` file
```javascript
module.exports.testFunction = () => console.log ('Hello from the other side')
```
- importnat module in index.js
```javascript
const myModule = require('./myModule.js')

myModule.testFunction()
```
- run `index.js` in the command line and you should  see
'Hello from the other side'

### 3rd Party NODE MODULES  (NPM)
- NPM stands for Node Package Manager
- You can access the site by going to [NPM](https://npmjs.com/)
- Find a package you want to use.
- To install globally ` npm i -g nameofnpm`
- To install locally `npm i -nameofnpm` 
- You should also make a `.gitignore` file by
```
touch .gitignore
```
- inside the `.gitignore` add `node_modules`


### NPM express + ejs + express-ejs-layouts
- While creating your project folders also install these NPMs locally
```
npm i express ejs express-ejs-layouts
```
- Create a views folder which will house the Routes

- 
```javascript
const express = require("express");
const app = express();
// import ejs layouts
const ejsLayouts = require("express-ejs-layouts");

app.set("view engine", "ejs");
app.use(ejsLayouts);
app.use(express.static('public'))

// Home route
// VERB: GET(read) URL: http://localhost:8000

<!-- app.get("/", (req, res) => {
  res.send("This is the HOME page");  // to test out
}); -->

app.get("/", (req, res) => {
  res.render("index.ejs");      // for use with ejs
});


app.listen(8000, () => {
  console.log("Nodemon out here running through port 8000");
});
```
- app is an object and get, listen, and use are methods
- to use layouts make sure you have a ```layout.ejs``` file inside the views folder
- This layout will be used by all pages, and the content will be filled in where the ```<%- body %>``` tag is placed. ```<%- body %>``` is a special tag used by express-ejs-layouts that cannot be renamed.
- If you want to use static images, js, css use:
```javascript
app.use(express.static('public'))
```

### NPM axios + dotenv
- install axios and dot env ```npm i axios dotenv```
- add ```.env``` into your ```.gitignore```
- create ```.env``` file to your root (this is where your api key will live)
```
MY_SECRET='I ate candy for breakfast'
FRUIT='mango'
OMDB_API_KEY='this will be your api'
```
- to use axios and dotenv
```javascript
require('dotenv').config()
const axios = require('axios')

console.log(process.env.OMDB_API_KEY)  // Should show your api key that's inside .env folder
```
- an example of how to fetch omdb while api key is hidden
```javascript
require('dotenv').config()
console.log(process.env.OMDB_API_KEY)
const axios = require('axios')

const url = `http://www.omdbapi.com/?t=the+good+the+bad+and+the+ugly&apikey=${process.env.OMDB_API_KEY}`

axios.get(url)
  .then(response => {
    console.log(response.data)
  })
```
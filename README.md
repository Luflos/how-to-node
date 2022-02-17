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


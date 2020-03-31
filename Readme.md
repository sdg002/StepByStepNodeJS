
# Overview - My Journey away from using Visual Studio for Web Development
The steps I followed to get started with basic web development without using any support from Visual Studio (no built in templates)
https://nodejs.org/en/docs/guides/debugging-getting-started/


# Getting started with Visual Studio (but not using any VS project types)
- Create a blank folder. This will be the root folder for all our subsequent experiments.
- Use git command line to initialize GIT  `git init`
- I like using *Visual Studio* as my editor and for managing git checkins
- Open this folder using Visual Studio
- VS.NET will create a *.VS* folder. This should  be ignored
- Creat a *.GITIGNORE* file in this directory

Add the following line
```
.vs
```

- Sync with GitHub


# Very Basic - Listening on port 8000 using createServer
- Create a folder *createServerDemo* under the root folder
- Add the following contents of the file *hello.js*
- Run node index.js

## Steps for debugging using Chrome
- node --inspect index.js
- Use chrome://inspect/#devices and add the PORT and localhost
- You should see your server listed under "Remote Target". Click here to open a Chrome Dev tools debugger window
- Invoke requests using the browser
- You should see your console.log statements


# Using Express along with NodeJS for a web server
- Create a folder *ExpressDemo*
- Navigate to this folder
- Run the command `npm init`
- Accept the defaults
- A new file `package.json` will be created
- Now run `npm install express`
- Dependencies will be installed
- The file package.json will be updated with the version number
- Run `node index.js` from the folder
```
const express = require('express')
const app = express();

app.get('/', (req, res) => {
    res.send('Hello World!')
});

app.use(express.static('public'));
app.listen(8000, () => {
    console.log('Example app listening on port 8000!')
});

```
- Browse to http://localhost:8000 and you should see "hello world"
- Create a subfolder *public*
- Add a simple HTML file *Demo.html* in this folder
- Browse to http://localhost:8000/Demo.html
- You should see the contents of the HTML rendered
- Reference https://www.tutorialspoint.com/expressjs/expressjs_static_files.htm
- Remember to omit the folder `node_modules` in the .GITIGNORE file
- Create a new .gitignore file in this folder and add the contents */node_modules*

# About the node_modules folder?
## Where do the packages get installed?
- You should see a folder *node_modules*
## Are we suppose to checkin the folder `node_modules` folder?
- No
- This is why we added */node_modules* to GITIGNORE
## What happens if I delete *node_modules* folder?
No problem. Just run `npm install`

# How to use NPM START and Scripts folder
- Modify the package.json by adding a scripts field
- Specify the command which will run when `npm start` is fired
- Run `npm start` and this will launch NODE
```
{
  "name": "expressdemo",
  "version": "1.0.0",
  "description": "This is my description",
  "main": "index.js",
  "scripts": {
    "test": "echo \"Error: no test specified\" && exit 1",
    "start": "node index.js"
  },
  "author": "Sau",
  "license": "ISC",
  "dependencies": {
    "express": "^4.17.1"
  }
}
```


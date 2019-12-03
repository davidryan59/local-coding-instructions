## NPM directory

Use this directory to keep all the JavaScript packages I've already published to npm.


### Publishing recent changes to npm

Go to terminal

To commit changes to git repo:
`git commit -am 'Description of changes'`

To increment the npm version number
`npm version patch` (or `minor`, or `major`)
Use `patch` for bug fixes
Use `minor` when adding features
Use `major` when backwards compatibility is not ensured.

Then push changes to git repo
`git push`

And publish changes on npm
`npm publish`


### Starting a new npm package

`npm init -y` the -y tag accepts all basic changes

`git init`
`touch .gitignore`
(Put inside .gitignore the things to ignore, e.g. node_modules, etc)

Make a new repo on github, get the location of the form `git@github.com:[USERNAME]/[REPONAME].git`

Add this line to package.json
`  "repository": "git@github.com:[USERNAME]/[REPONAME].git",`

Sign into your npm account
`npm login`
(Need username, email, password)

Check you're logged in
`npm whoami`

Write the JavaScript file to export
- Defaults to `index.js`
- At end of file, declare
`module.exports = {...}`
where ... is the list of functions to export

Use earlier instructions to save/publish changes to git repo and npm website.


### To include my new package in another project

`npm init`
`npm install [PACKAGE]`

In .js file: `var xyz = require('[PACKAGE]')`


### Keywords in package.json - helps my package get found

Install the keywords utility
`npm i -g keywords`

Add keywords to current package
`keywords foo bar baz`

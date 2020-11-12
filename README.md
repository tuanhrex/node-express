# node-express

1. Make repo called `node-express`
2. `clone` the repo
3. Navigate to the directory.
4. Type `npm init -y` to create a `package.json` with default selections.
5. `touch index.js` to make a JS file.
6. `code .` to open the directory in VS Code.
7. Select you `index.js` file and type:
```js
let name = 'Tu Anh Huynh';
console.log(name);
```
8. Save the file and return to command line.
9. Type `node index.js` to confirm that everthing works.
10. `git add` `git commit` and `git push`
11. `touch myModule.js` to make another JS file.
12. Navigate to the new file in VS Code.
13. Type:
```js
const beBasic = () => "That's so fetch"

function add(num1, num2) {
    return num1 + num2
}

function subtract(num1, num2) {
    return num2 - num1
}

module.exports = {
    beBasic,
    add, 
    subtract

}
```
14. Return to you index.js file on VS Code and type:
```js
const { add, subtract } = require("./myModule");

console.log(add(5, 50))
console.log(subtract(10, 20))
```
15. In the command line, type `node index.js` to confirm that everything is working properly.

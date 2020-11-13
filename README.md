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


# node_modules_practice

1. `fork` and `clone` the `node_modules_practice` repo.
2. Refer to Steps 3-12 from previous section.
3. Type in `myModule.js`:
```js
let foods = ['pizza', 'burger', 'sushi', 'tacos']

function favFoods() {
    for (i = 0; i < foods.length; i++) {

    
    console.log(foods[i])
    }
}

module.exports = {
    favFoods
}
```
4. Return to you index.js file on VS Code and type:
```js
const { favFoods } = require("./myModule")
favFoods();
```

5. In the command line, type `node index.js` to confirm that everything is working properly.

6. To install the pokemon npm, type `npm install pokemon` in the command line.

7. In your index.js type 
```js
const pokemon = require('pokemon');

console.log(pokemon.random());

console.log(pokemon.getName(125));

console.log(pokemon.getId('Pikachu'));

// Can also get Pokemon names in different languages

console.log(pokemon.getName(25, 'de'));
console.log(pokemon.getName(125, 'de'));
```

8. In the command line, type `node index.js` to confirm that everything is working properly.

9. To install the temperature npm, type `npm install temperature` in the command line.

10. In the index.js type:
```js
const temperature = require('temperature')
// Use temperature.unitToUnit(num) to convert temperature
console.log(temperature.kelvinToCelsius(100))
console.log(temperature.celsiusToKelvin(100))
console.log(temperature.kelvinToFahrenheit(600))

```
11. In the command line, type `node index.js` to confirm that everything is working properly.

12. To install the randomcolor npm, type `npm install randomcolor` in the command line.

13. In the index.js type :
```js
const randomColor = require('randomcolor')
// Makes an array of random colors
let colorArray = (randomColor({
    count: 25,
    luminosity: 'bright',
    hue: 'random'
 }))

 console.log(colorArray)
 ```
 14. In the command line, type `node index.js` to confirm that everything is working properly.
 
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

# hello-express

1. `fork` and `clone` the `hello-express` repo.
2. Type `npm init -y` in command line.
3. Type `npm install express`
4. Type `touch index.js` to make a js file.
5. Type `code .` to open VS Code.
6. Navigate to `index.js` file and type:
```js
const express = require('express');
const app = express();
```
7. Now that the app is connected, to create a route to the root directory type:
```js
app.get('/', function(req, res) {
    res.send('Hello, SEI world');
});

app.listen(8000);
```
8. To make other routes, you can type anything after the '\' like it is shown below:
```js
app.get('/about', function(req, res) {
    res.send('This is the about page.')
});
```
9. Now return to your command line and type `node index.js`
10. Go to chrome and type in `localhost:800` to view the page.

# express-apis-omdb

1. `fork` and `clone` repo in the terminal.
2. Navigate to the directory in type `npm install` to install all packages needed.
3. Also type `npm install axios` which will be used later
4. Type `touch .env`
5. Type `code .` to open VS Code.
6. Open the `.env` file and type `api=[yourkey]`
7. Open your `server.js` to make sure all required packages as shown below and a listen:
```js
require('dotenv').config();
const express = require('express');
const ejsLayouts = require('express-ejs-layouts');
const app = express();
const axios = require('axios').default;


// Sets EJS as the view engine
app.set('view engine', 'ejs');
// Specifies the location of the static assets folder
app.use(express.static('static'));
// Sets up body-parser for parsing form data
app.use(express.urlencoded({ extended: false }));
// Enables EJS Layouts middleware
app.use(ejsLayouts);

// Adds some logging to each request
app.use(require('morgan')('dev'));

var server = app.listen(process.env.PORT || 3000);

```
8. Now open your `index.ejs` to build your search form with a get method and `/results` action. To do that type:
```ejs
<form method="GET" action="/results">
    <input type="text" name="q" id="movie">
    <input type="submit" value="Search">

</form>
```
9. Go back to your `server.js` to make your root route display `index.ejs`. To build the route type:
```js
app.get('/', function(req, res) {
  res.render('index');
  console.log('Hello');
});
```
10. Now make your results path that takes your query from the search form , searches the omdb API, and then render in the results page.
```js
app.get('/results', (req, res) => {
  

  // for (const key in req.query) {
  //   console.log(key, req.query[key])
  // }
  
  axios.get(`http://www.omdbapi.com/?apikey=${process.env.api}&s=${req.query.q}`)
  .then(function (response) {
    const movies = response.data.Search
    
    
    res.render('results', { movies })
  })
})
```
10. Now open your `results.ejs` and add the results with links to the movie using it's id in the page.
```
<ul>
    <% movies.forEach(function(movie) { %>
        <li> <a href="/movies/<%= movie.imdbID %>"><%= movie.Title %></a></li>
        
    <% }); %>

</ul>
```
11. The links leads to `/movies/` route, so now we need to build that route. Go back to the `server.js` and to build your route to for `/movies`, that searches for the movies based on its movie id, and then render in `/detail`.
```js
app.get('/movies/:movie_id', (req,res) => {
  const movie_id = req.params.movie_id
 

  axios.get(`http://www.omdbapi.com/?apikey=${process.env.api}&i=${movie_id}`)
  .then(function (response) {
    
    const movie = response.data

    res.render('detail', { movie })
  })
})
```
# express-apis-omdb (continue)

14. Type 'npm install -g sequelize-cli` in your terminal to do a global install on your local machine.
15. Type `npm install pg` and `npm install sequelize` to install postgres and sequelize.
16. Type `sequelize init` to initialize sequelize.
17. In VS Code, open the `config.json` and make chages to match your project.
```js
{
  "development": {
    "username": "postgres",
    "password": "whateveryourpasswordis",
    "database": "express-apis-omdb_development",
    "host": "127.0.0.1",
    "dialect": "postgres"
  },
  "test": {
    "username": "postgres",
    "password": "whateveryourpasswordis",
    "database": "express-apis-omdb_test",
    "host": "127.0.0.1",
    "dialect": "postgres"
  },
  "production": {
    "username": "postgres",
    "password": "whateveryourpasswordis",
    "database": "express-apis-omdb_production",
    "host": "127.0.0.1",
    "dialect": "postgres"
  }
}
```
18. Return to your terminal and type `sequelize db:create express-apis-omdb_development` create your database with sequelize and have its name match the database in your config.
19. Type `sequelize model:create --name fave --attributes title:string,imdb:string` to create a model.
20. Type `sequelize db:migrate` to ensure that your model connects to your database.
21. Return to your `server.js` in VS Code and require the new module.
```js
const db = require('./models')
```
22. Navigate to your `detail.ejs` and add a form with two hidden fields of movie title and imdbib. It should be a `POST` method and have an action of `/faves`
```js
<form method="POST" action="/faves">
    
    <label for="fave">Add To Fave</label>
    <input type="hidden" id="movieTitle" name="movieTitle" value="<%= movie.Title %>">
    <input type="hidden" id="movieimdbID" name="movieimdbID" value="<%= movie.imdbID %>">
    <input type="submit">
</form>

```
23. Go back to your `server.js` and create a `POST` route for `/faves`.
```js
app.post('/faves', (req, res) => {
  db.fave.create({
    title: req.body.movieTitle,
    imdbid: req.body.movieimdbID
  }).then(newMovie => {
    console.log(newMovie);
  })


  res.redirect('/faves')
})
```
24. Now create a `GET` route for `/faves` and use your model to get all faves from your database.
```js
app.get('/faves', (req, res) => {
  
  db.fave.findAll().then(allFaves => {
  console.log(allFaves);
  res.render('faves', { allFaves})
});
```
25. Create a `faves.ejs` and open it and add:
```html
This is my faves

<ul>
    <% allFaves.forEach(function(faves) { %>
    <li><%= faves.title%></li>
    <% }); %>
</ul>
```


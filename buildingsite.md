# Building a site using Node.js and Express

[<- Go Back](nodejs.md)

* Now that we know how to create a project with NPM
* Add Express as dependency and create a web server
* We can also create some routes to handle our requests
* And configure our statics assets
* Also, we can create templates using Pug and render them from Express server using the render method
* It's time to put everything in action
* You can donwload the project code from the [github repo]()
* First lets create a node-site-example folder and change directory into it

  ```bash
  mkdir node-site-example
  cd node-site-example
  ```

* After creating the folder lets install pug, express and [nodemon](https://github.com/remy/nodemon)

  ```
  npm install express pug nodemon
  ```
* Nodemon is a Node.js module that will watch our files to see if we save them and reload the server for us
* Configure NPM start script

  ```json
  "start": "nodemon"
  ```
* Nodemon will look for an index.js file to start the server and watch for changes
* Create an `index.js` file and add a express server

* index.js
  ```js
  const express = require('express');
  const app = express();
  const port = 3000;

  app.listen(port, () => {
    console.log(`Server running on port ${port}`);
  });
  ```

* And start the server
  ```bash
  npm start

  > node-site-example@1.0.0 start /node-site-example
  > nodemon

  [nodemon] 1.17.4
  [nodemon] to restart at any time, enter `rs`
  [nodemon] watching: *.*
  [nodemon] starting `node index.js`
  Server running on port 3000
  ```

* Now we have our server running and we need to configure routes, static assets and the template engine
* We can see that nodemon is looking for all our files `[nodemon] watching: *.*`
* Also we can restart the server writing `rs` on the terminal that is running nodemon on in case we need to
* Create a `views` folder
* Add `index.pug` to the views folder
* Add this code to index.pug

* index.pug
  ```
  doctype html
    head
      title Simple site using Node.js, Express and Pug
    body
      h1 Wellcome to Node.js, Express and Pug
      p This project is just to practice
  ```
* Configure Express to use pug
  ```index.js
  app.set('view engine', 'pug');
  ```
* Finaly add a root get route handler to render the home content using index.html
  ```
  app.get('/', (req, res) => {
    res.render('index', {});
  });
  ```
* Your index.js file must look like this

* index.js
  ```js
  const express = require('express');
  const app = express();
  const port = 3000;

  app.set('view engine', 'pug');

  app.get('/', (req, res) => {
    res.render('index', {});
  });

  app.listen(port, () => {
    console.log(`Server running on port ${port}`);
  });
  ```
* It's time to add the static public folder and configure express to use it
* Create a `public` folder
* Configure Express to use the public folder 
* index.js
  ```
  app.use(express.static('public'));
  ```
* We could add all the static assets together as siblings but it's better to organize our code
* Create the following folder structure
  ```
  /node-site-example
  |- public
      |- css
          |- styles.css
      |- img
      |- js
        |- scripts.js
  ```
* Add some CSS to the site
* styles.css
  ```css
  * {
    padding: 0;
    margin: 0;
  }

  body {
    color: black;
    font-family: Arial, Helvetica, sans-serif;
    font-size: 16px;
  }
  ```
* Add some JS to the site
* scripts.js
  ```js
  window.onload = function() {
    console.log('Loaded site');
  }
  ```
* Now that we have the css and js files ready we need to add it to the template
* index.pug
  ```
  link(rel='stylesheet', href="/css/styles.css")
  script(src="/js/scripts.js")
  ```
* We use link for the CSS file and script for the JavaScript file
* If you refresh the browser now the font should look different and the size too
* Also is nice that we removed all padding and margins from the elements
* As we'll have to create more than one page we need to create a layout
* Create the `layout.pug` file inside the view folder
* Copy and paste all the content from index.pug template into the layout.pug one
* Also we need to add a styles, scripts & content block so we can change the content from the different templates
* layout.pug
  ```
  doctype html
  html
    head
      title Simple site using Node.js, Express and Pug
      link(rel='stylesheet', href="/css/styles.css")
      block styles
      script(src="/js/scripts.js")
      block scripts
    body
      block content
  ```
* Now the index.pug file will only contain the code that is relative only to that file
* We need to extend the layout and create the block content

  ```index.pug
  extends ./layout.pug

  block content
    h1 Wellcome to Node.js, Express and Pug
    p This project is just to practice
  ```
* Check that the site it still works as expected
* If we don't have any errors we must see the same content but now using the layout
* Inside the public/img create a `superheroes` folder and download the following images
  ```
  /node-site-example
  |- public
      |- img
          |- blackwidow.jpg
          |- captainmarvel.jpg
          |- captanamerica.jpg
          |- daredevil.jpg
          |- hulk.jpg
          |- ironman.jpg
          |- spiderman.jpg
          |- thor.jpg
          |- wolverine.jpg
  ```
* Now we have the superheroes images in our static assets folder
* We want to create a homepage with some superheores picture and name
* Then we can create a superheroe description page
* Start by creating a superheroes array in the root route handler
* index.js

  ```js
  app.get('/', (req, res) => {
    const superheroes = [
      { name: 'SPIDER-MAN', image: 'spiderman.jpg' },
      { name: 'CAPTAIN MARVEL', image: 'captainmarvel.jpg' },
      { name: 'HULK', image: 'hulk.jpg' },
      { name: 'THOR', image: 'thor.jpg' },
      { name: 'IRON MAN', image: 'ironman.jpg' },
      { name: 'DAREDEVIL', image: 'daredevil.jpg' },
      { name: 'BLACK WIDOW', image: 'blackwidow.jpg' },
      { name: 'CAPTAIN AMERICA', image: 'captanamerica.jpg' },
      { name: 'WOLVERINE', image: 'wolverine.jpg' },
    ];

    res.render('index', { superheroes: superheroes });
  });
  ```
* We can see that we have a `superheroes array` that has JavaScript objects as content
* Each object has a superheroe name and image
* Then we pass this superheroes array as superheroes object property
* This means that at the template level we'll have a `superheroes` variable that represents this objects
* Now lets show the superheroes on our home page
* Using each we can iterate the superheroes collection
  ```index.pug
  each superheroe in superheroes
    div.superheroe-container
      img(src='/img/superheroes/' + superheroe.image)
      h3= superheroe.name
  ```
* Update index.pug to match this code:
  ```
  extends ./layout.pug

  block content
    h1 Superheroes
    p This site shows superheroes information
    each superheroe in superheroes
      div.superheroe-container
        img(src='/img/superheroes/' + superheroe.image)
        h3= superheroe.name
  ```
* Now our site has all the superheroes pictures and name but it would be nice to change the design a little
* Add the following class to your styles.css file
* styles.css
  ```css
  .superheroe-container {
    display: inline-block;
    width: 200px;
    text-align: center;
    margin-right: 10px;
    margin-bottom: 40px;
  }  
  ```
* It would be nice to be able to click the image or the superhero name and see a detail page
* To create this feature we need to do a couple of changes
* First we need to change the template
  ```index.pug
  extends ./layout.pug

  block content
    h1 Superheroes
    p This site shows superheroes information
    each superheroe in superheroes
      div.superheroe-container
        a(href="/superheroes/")
          img(src='/img/superheroes/' + superheroe.image)
          h3= superheroe.name
  ```
* We added a link element that relates this page with `/superheroes/`
* So far so good but we still don't have the superheroes route configured
* Lets add a new route config
* index.js
  ```js
  app.get('/superheros/', (req, res) => {
    const superheroes = [
      { name: 'SPIDER-MAN', image: 'spiderman.jpg' },
      { name: 'CAPTAIN MARVEL', image: 'captainmarvel.jpg' },
      { name: 'HULK', image: 'hulk.jpg' },
      { name: 'THOR', image: 'thor.jpg' },
      { name: 'IRON MAN', image: 'ironman.jpg' },
      { name: 'DAREDEVIL', image: 'daredevil.jpg' },
      { name: 'BLACK WIDOW', image: 'blackwidow.jpg' },
      { name: 'CAPTAIN AMERICA', image: 'captanamerica.jpg' },
      { name: 'WOLVERINE', image: 'wolverine.jpg' },
    ];

    res.render('superhero', { superheroes: superheroes });
  });
  ```
* Great now we have the route but it looks like we have the superheroes repeated
* Also we only need to show one superhero at the time
* And.. we need to create the superhero template
* Uff.. so many things we better start soon!
* Create the `superhero.pug` template inside the views folder
* Add the following code
* superheroe.pug
  ```
  extends ./layout.pug

  block content
    img(src='/img/superheroes/' + superheroe.image)
    h3= superheroe.name
  ```
* Great we are using the layout template that we created but we don't have the superheroe data
* How can we deal with this situation?
* So we know that we can use the router to pass data to the template
* But we need to know the selected superheroe, right?
* We can use the superhero name to select the selected superhero
* Or we can use an id
* To use the id will have to update the superheroes array objects
  ```js
  const superheroes = [
    { id: 1, name: 'SPIDER-MAN', image: 'spiderman.jpg' },
    { id: 2, name: 'CAPTAIN MARVEL', image: 'captainmarvel.jpg' },
    { id: 3, name: 'HULK', image: 'hulk.jpg' },
    { id: 4, name: 'THOR', image: 'thor.jpg' },
    { id: 5, name: 'IRON MAN', image: 'ironman.jpg' },
    { id: 6, name: 'DAREDEVIL', image: 'daredevil.jpg' },
    { id: 7, name: 'BLACK WIDOW', image: 'blackwidow.jpg' },
    { id: 8, name: 'CAPTAIN AMERICA', image: 'captanamerica.jpg' },
    { id: 9, name: 'WOLVERINE', image: 'wolverine.jpg' },
  ];
  ```
* Great now we have ids on our superheroes objects
* I don't know about you but I think it's still pretty bad to have this duplicated array
* Also we'll need the ids to create the links
* What about if we move this array to a higher scoe level so both routes can use it?
* index.js
  ```js
  const express = require('express');
  const app = express();
  const port = 3000;

  app.set('view engine', 'pug');
  app.use(express.static('public'));

  const superheroes = [
    { id: 1, name: 'SPIDER-MAN', image: 'spiderman.jpg' },
    { id: 2, name: 'CAPTAIN MARVEL', image: 'captainmarvel.jpg' },
    { id: 3, name: 'HULK', image: 'hulk.jpg' },
    { id: 4, name: 'THOR', image: 'thor.jpg' },
    { id: 5, name: 'IRON MAN', image: 'ironman.jpg' },
    { id: 6, name: 'DAREDEVIL', image: 'daredevil.jpg' },
    { id: 7, name: 'BLACK WIDOW', image: 'blackwidow.jpg' },
    { id: 8, name: 'CAPTAIN AMERICA', image: 'captanamerica.jpg' },
    { id: 9, name: 'WOLVERINE', image: 'wolverine.jpg' },
  ];

  app.get('/', (req, res) => {
    res.render('index', { superheroes: superheroes });
  });

  app.get('/superheros/', (req, res) => {
    res.render('superhero', { superheroes: superheroes });
  });

  app.listen(port, () => {
    console.log(`Server running on port ${port}`);
  });
  ```
* This is looking much better now
* We still have a problem on how to know the selected superhero
* Having the ids to identify them is great but we still need to update our code
* First modify the links to use the superhero id
* index.pug
  ```
  a(href="/superheroes/" + superheroe.id)
  ```
* If the user clicks on this link it will redirect to a url that looks like this: http://localhost:3000/superheroes/2
* So it looks like the user will select a superhero and we'll go to the /superheroes/ page and we have the id
* Now we need to update our express route so we can get the id param and get the superhero data
* index.js
  ```js
  app.get('/superheros/:id', (req, res) => {
    const selectedId = req.params.id;

    let selectedSuperhero = superheroes.filter(superhero => {
      return superhero.id === +selectedId;
    });

    selectedSuperhero = selectedSuperhero[0];
    
    res.render('superhero', { superheroe: selectedSuperhero });
  });
  ```
* Using `'/superheros/:id'` we define that this route contains a parameter that we need to get
* This request parameter is called id and will come after the `superheros` route
* To get this value we use `req.params.id`
* We could name this parameter with any name
* Then we filter the superheroes array by id
* And assighn the selected superhero to the `selectedSuperhero` variable
* The only remainding thing to do is render the template using the selectedSuperhero data
* Now we can call any this url http://localhost:3000/superheros/2 changing the id from 1 to 9
* Our home page still has blue and violet links so update the css so it looks better
* styles.css
  ```css
  .superheroe-container a {
    color: black;
    text-decoration: none;
  }
  ```

* Great we're able to show the superheroes home and detail page
* It would be really nice to be able to create a new superhero too, right?
* To create any new resource we need to create a form
* Great now we have ids on our superheroes objects
* I don't know about you but I think it's still pretty bad to have this duplicated array
* Also we'll need the ids to create the links
* What about if we move this array to a higher scoe level so both routes can use it?
* index.js
  ```js
  const express = require('express');
  const app = express();
  const port = 3000;

  app.set('view engine', 'pug');
  app.use(express.static('public'));

  const superheroes = [
    { id: 1, name: 'SPIDER-MAN', image: 'spiderman.jpg' },
    { id: 2, name: 'CAPTAIN MARVEL', image: 'captainmarvel.jpg' },
    { id: 3, name: 'HULK', image: 'hulk.jpg' },
    { id: 4, name: 'THOR', image: 'thor.jpg' },
    { id: 5, name: 'IRON MAN', image: 'ironman.jpg' },
    { id: 6, name: 'DAREDEVIL', image: 'daredevil.jpg' },
    { id: 7, name: 'BLACK WIDOW', image: 'blackwidow.jpg' },
    { id: 8, name: 'CAPTAIN AMERICA', image: 'captanamerica.jpg' },
    { id: 9, name: 'WOLVERINE', image: 'wolverine.jpg' },
  ];

  app.get('/', (req, res) => {
    res.render('index', { superheroes: superheroes });
  });

  app.get('/superheros/', (req, res) => {
    res.render('superhero', { superheroes: superheroes });
  });

  app.listen(port, () => {
    console.log(`Server running on port ${port}`);
  });
  ```
* This is looking much better now
* We still have a problem on how to know the selected superhero
* Having the ids to identify them is great but we still need to update our code
* First modify the links to use the superhero id
* index.pug
  ```
  a(href="/superheroes/" + superheroe.id)
  ```
* If the user clicks on this link it will redirect to a url that looks like this: http://localhost:3000/superheroes/2
* So it looks like the user will select a superhero and we'll go to the /superheroes/ page and we have the id
* Now we need to update our express route so we can get the id param and get the superhero data
* index.js
  ```js
  app.get('/superheros/:id', (req, res) => {
    const selectedId = req.params.id;

    let selectedSuperhero = superheroes.filter(superhero => {
      return superhero.id === +selectedId;
    });

    selectedSuperhero = selectedSuperhero[0];
    
    res.render('superhero', { superheroe: selectedSuperhero });
  });
  ```
* Using `'/superheros/:id'` we define that this route contains a parameter that we need to get
* This request parameter is called id and will come after the `superheros` route
* To get this value we use `req.params.id`
* We could name this parameter with any name
* Then we filter the superheroes array by id
* And assighn the selected superhero to the `selectedSuperhero` variable
* The only remainding thing to do is render the template using the selectedSuperhero data
* Now we can call any this url http://localhost:3000/superheros/2 changing the id from 1 to 9
* Our home page still has blue and violet links so update the css so it looks better
* styles.css
  ```css
  .superheroe-container a {
    color: black;
    text-decoration: none;
  }
  ```

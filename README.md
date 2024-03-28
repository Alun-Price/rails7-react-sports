# README

This code is from a Rubyroid Labs Tutorial featuring Ruby on Rails and React (author: Daria Stolyar https://rubyroidlabs.com/blog/2023/11/how-to-use-ruby-on-rails-with-react-in-2024/)

### Why You Should Choose Ruby on Rails for the Backend

- **accelerates software development**
	- Conventions over Configuration (CoC)
		- follow conventions
		- build app in less time
		- fewer lines than Java or Node
	- Don't Repeat Yourself (DRY)
		- concise re-usable code
	- Together
		- reduce number of decisions devs need to make
		- improve code quality
		- RoR accelerates software development by 30-40% over other programming languages (forbes/quora/isrubyadyinglanguage/2018)

- **has an extensive library of gems**
	- 160 000 + free libraries
	- 149 + billion downloads
	- expand core functionality of web apps
	- Top 3 Gems
		- Devise
			- user authentication and authorization
			- password encryption, email confirmation, recovery
		- CarrierWave
			- simplifies file uploads and management
			- image resizing, file validation and storage
		- ActiveAdmin
			- create customised admin dashboards, pages and reports

- **it's a highly secure framework**
	- security against
		- cross-site scripting
		- request forgery
		- SQL Injection
		- web based attacks
		- phishing
	- employs REST API
		- adhere to standard protocols
	- Shopify, Zendesk and AIrBnB choose RoR

- **its a cost effective solution**
	- open source framework
	- free

### Why You Should Choose React For The Frontend

- **React is FLEXIBLE**
	- component-based architecture
	- re-use components in other parts of the app
	- modularity = freedom to create complex interfaces

- **React Supports Fast Rendering**
	- virtual DOM
	- changes are first applied to the vDOM
		- reduces amount of interactions with the actual DOM
		- these can be slow and intensive
	- diffing algorithm - determines small set of changes that should be applied to the main DOM

- **React has a DECLARATIVE SYNTAX**
	- describe how state should look, without describing the actual steps to achieve it
	- easier-to-understand code
	- easier to identify and troubleshoot issues

### How To Use React and Ruby on Rails in 2024

- 2 common ways to use React and RoR together
	- Two separate apps with API communication
		- 2 stand alone apps
		- apps communicate via API requests
		- decouple the frontend and backend
		- operate independently
	- Ruby on Rails App with React Library
		- build RoR app
		- connect React to the frontend
		- devs working on the FE will use JS libraries without modifying the code as per the Rails framework standards
		- smaller applications with more integrated development approach
		- eliminates the need to develop an API

### Why Use RoR with ReactJS??

- faster time to market
- helps you create more complex apps
- reliable and stable combination for web development
	- active communities
	- regular updates
	- advanced features
	- used by X, AirBnB, Github


### How To Integrate Ruby on Rails and React - Tutorial
        
- to follow the practical integration of Ruby on Rails with React, we're going to create an application with sports exercises
- 7 Step Tutorial

### Step 1 - Create a Rails Application

```
rails new rails7-react-sports -d postgresql -j esbuild -c bootstrap -T
```

- places app in rails7-react-sports root directory
	- can find all the files associated with the project
- automatically creates the Ruby and JavaScript dependencies needed for accelerated web development
- configures Webpack
- flags
	- `-d`
		- `postgresql` as the preferred database engine
	- `-j`
		- `esbuild` as the preferred JS bundler


```
cd rails7-react-sports

code . -r
```



### Step 2 - Connect Your Application To A Database

- Your Rails needs to be connected to a databse
- Postgresql in this case
- store the user intent data
- Rails provides the commands to manage the database schema
	- create
	- drop
	- reset
- create a database
	- `rails db:create`
	- creates a development and test database

```
➜  rails7-react-sports git:(main) ✗ rails db:create
Created database 'rails7_react_sports_development'
Created database 'rails7_react_sports_test'
```

- start your application with `bin/dev` command


```
rails7-react-sports git:(main) ✗ bin/dev
14:09:32 web.1  | started with pid 35165
14:09:32 js.1   | started with pid 35166
14:09:32 css.1  | started with pid 35167
14:09:32 js.1   | yarn run v1.22.21
14:09:32 css.1  | yarn run v1.22.21
14:09:32 js.1   | $ esbuild app/javascript/*.* --bundle --sourcemap --format=esm --outdir=app/assets/builds --public-path=/assets --watch
14:09:32 css.1  | $ nodemon --watch ./app/assets/stylesheets/ --ext scss --exec "yarn build:css"
14:09:32 web.1  | DEBUGGER: Debugger can attach via UNIX domain socket (/var/folders/q2/wq97v0n10v92_y_rwk_rmhgw0000gn/T/rdbg-501/rdbg-35165)
14:09:32 js.1   | [watch] build finished, watching for changes...
14:09:32 web.1  | => Booting Puma
14:09:32 web.1  | => Rails 7.1.3.2 application starting in development 
14:09:32 web.1  | => Run `bin/rails server --help` for more startup options
14:09:32 css.1  | [nodemon] 3.1.0
14:09:32 css.1  | [nodemon] to restart at any time, enter `rs`
14:09:32 css.1  | [nodemon] watching path(s): app/assets/stylesheets/**/*
14:09:32 css.1  | [nodemon] watching extensions: scss
14:09:32 css.1  | [nodemon] starting `yarn build:css`
14:09:32 web.1  | Puma starting in single mode...
14:09:32 web.1  | * Puma version: 6.4.2 (ruby 3.3.0-p0) ("The Eagle of Durango")
14:09:32 web.1  | *  Min threads: 5
14:09:32 web.1  | *  Max threads: 5
14:09:32 web.1  | *  Environment: development
14:09:32 web.1  | *          PID: 35165
14:09:32 web.1  | * Listening on http://127.0.0.1:3000
14:09:32 web.1  | * Listening on http://[::1]:3000
14:09:32 css.1  | $ yarn build:css:compile && yarn build:css:prefix
14:09:32 web.1  | Use Ctrl-C to stop
14:09:33 css.1  | $ sass ./app/assets/stylesheets/application.bootstrap.scss:./app/assets/builds/application.css --no-source-map --load-path=node_modules
14:09:34 css.1  | $ postcss ./app/assets/builds/application.css --use=autoprefixer --output=./app/assets/builds/application.css
14:09:34 css.1  | [nodemon] clean exit - waiting for changes before restart
```

- going to http://127.0.0.1:3000/ in a browser, we should see the Rails Welcome Splash screen ...

### Step 3 - Install React FrontEnd Dependencies

- React = the core library, useful for interfaces
- React DOM = renders React elements into the DOM
- React Router = handles navigation in the app

```
yarn add react react-dom react-router-dom
```

- find the installed dependencies in the package.json file

**package.json**
```json
{
  "name": "app",
  "private": true,
  "dependencies": {
    "@hotwired/stimulus": "^3.2.2",
    "@hotwired/turbo-rails": "^8.0.4",
    "@popperjs/core": "^2.11.8",
    "autoprefixer": "^10.4.19",
    "bootstrap": "^5.3.3",
    "bootstrap-icons": "^1.11.3",
    "esbuild": "^0.20.2",
    "nodemon": "^3.1.0",
    "postcss": "^8.4.38",
    "postcss-cli": "^11.0.0",
    "react": "^18.2.0",
    "react-dom": "^18.2.0",
    "react-router-dom": "^6.22.3",
    "sass": "^1.72.0"
  },
  "scripts": {
    "build": "esbuild app/javascript/*.* --bundle --sourcemap --format=esm --outdir=app/assets/builds --public-path=/assets",
    "build:css:compile": "sass ./app/assets/stylesheets/application.bootstrap.scss:./app/assets/builds/application.css --no-source-map --load-path=node_modules",
    "build:css:prefix": "postcss ./app/assets/builds/application.css --use=autoprefixer --output=./app/assets/builds/application.css",
    "build:css": "yarn build:css:compile && yarn build:css:prefix",
    "watch:css": "nodemon --watch ./app/assets/stylesheets/ --ext scss --exec \"yarn build:css\""
  },
  "browserslist": [
    "defaults"
  ]
}
```

### Step 4 - Create the Homepage

- create the homepage where users land when they open your app
- Rails follows the MVC architecture pattern
	- takes user input and passes the data to the appropriate model or view
- Rails also has a controller component generator to create controllers
	- controllers handle and process user inputs, update the model and view
- Lets create a `Homepage` controller with an `index` action

```
rails g controller Homepage index
```

```
rails7-react-sports git:(main) rails g controller Homepage index
      create  app/controllers/homepage_controller.rb
       route  get 'homepage/index'
      invoke  erb
      create    app/views/homepage
      create    app/views/homepage/index.html.erb
      invoke  helper
      create    app/helpers/homepage_helper.rb
```

- we see that this command has generated 3 new pages
	- homepage_controller.rb
		- receives requests related to the Homepage
	- homepage_helper.rb
		- includes helper methods for the Homepage controller
	- index.html.erb
		- view page for rendering homepage-related actions
- ALSO
	- added a GET route to `config/routes.rb`

```rb
Rails.application.routes.draw do
  get 'homepage/index'
  # Define your application routes per the DSL in https://guides.rubyonrails.org/routing.html

  # Reveal health status on /up that returns 200 if the app boots with no exceptions, otherwise 500.
  # Can be used by load balancers and uptime monitors to verify that the app is live.
  get "up" => "rails/health#show", as: :rails_health_check

  # Defines the root path route ("/")
  # root "posts#index"
end
```

- Note:  change the `get homepage/index` to `root homepage#index`
	- Rails sets the root url to the index action of the Homepage
	- Makes Homepage the default landing page

```rb
Rails.application.routes.draw do
  root 'homepage#index'
  # Define your application routes per the DSL in https://guides.rubyonrails.org/routing.html

  # Reveal health status on /up that returns 200 if the app boots with no exceptions, otherwise 500.
  # Can be used by load balancers and uptime monitors to verify that the app is live.
  get "up" => "rails/health#show", as: :rails_health_check

  # Defines the root path route ("/")
  # root "posts#index"
end
```

- go to `http://127.0.0.1:3000/` in the browser (ensure server still running) and you should see the Homepage (instead of the Rails Splash page)


- Next: go to `app/views/homepage/index.html.erb` and remove the code and save the file as empty
	- will ensure that contents will render separately from your frontend part

```html
<h1>Homepage#index</h1>
<p>Find me in app/views/homepage/index.html.erb</p>

```

- you should see nothing if you refresh the homepage now!!!

### Step 5 - Configure React as your Rails Frontend

- most of the settings for seamless work between React and Rails are in place
- need to configure the `esbuild` entry point for JS files
- create a `app/javascript/components` folder
	- where components for the entire app will be housed
	- including the entry file
- open the `app/javascript/application.js` file

```js
// Entry point for the build script in your package.json
import "@hotwired/turbo-rails"
import "./controllers"
import * as bootstrap from "bootstrap"
```

- add `import "./components"` to the last row
- with the directory imported into the entry point now, we can create a component for the Homepage
	- content
	- CTA button to view all the exercises
- in the `app/javascript/components` folder, create a `Home.jsx` file
- add the following code ...

**Home.jsx**
```jsx
import React from "react";
import { Link } from "react-router-dom";

export default () => (
  <div className="vw-100 vh-100 primary-color d-flex align-items-center justify-content-center">
    <div className="jumbotron jumbotron-fluid bg-transparent">
      <div className="container secondary-color">
        <h1 className="display-4">Sport exercises</h1>
        <p className="lead">
          A list of sport exercises to boost your workout.
        </p>
        <hr className="my-4" />
        <Link
          to="/exercises"
          className="btn btn-lg custom-button"
          role="button"
        >
          View Exercises
        </Link>
      </div>
    </div>
  </div>
);
```

- Note: `Link` component from React Router = helps us navigate from one page to another in the app
- Now we need to create the routes directory
	- has corresponding components that are rendered to the browser when a route is loaded
	- create `app/javascript/routes` dir
		- then create an `index.jsx` file in the routes folder
		- add the following code to it ...

**router/index.js**
```jsx
import React from "react";
import { BrowserRouter as Router, Routes, Route } from "react-router-dom";
import Home from "../components/Home";

export default (
	<Router>
		<Routes>
			<Route path="/" element={<Home />} />
		</Routes>
	</Router>
);
```

- pull in the required modules
- set up routing using React Router
- new file `app/javascript/components/App.jsx`
- add the code ...

```jsx
import React from "react";
import Routes from "../routes";

export default props => <>{Routes}</>;
```

- render your App.jsx file in the entry file by adding the following code to the `app/javascript/components/index.jsx` file ...

```jsx
import React from "react";
import { createRoot } from "react-dom/client";
import App from "./App";

document.addEventListener("turbo:load", () => {
	const root = createRoot(
	document.body.appendChild(document.createElement("div"))
	);
	root.render(<App />);
});
```

- when the routing is set up, you can add CSS styles to the Homepage
- open `app/assets/stylesheets/application.bootstrap.scss` and replace the code with the following ...

```scss
@import 'bootstrap/scss/bootstrap';
@import 'bootstrap-icons/font/bootstrap-icons';

.bg_primary-color {
background-color: #FFFFFF;
}
.primary-color {
background-color: #FFFFFF;
}
.bg_secondary-color {
background-color: #293241;
}
.secondary-color {
color: #293241;
}
.custom-button.btn {
background-color: #293241;
color: #FFF;
border: none;
}
.hero {
width: 100vw;
height: 50vh;
}
.hero img {
object-fit: cover;
object-position: top;
height: 100%;
width: 100%;
}
.overlay {
height: 100%;
width: 100%;
opacity: 0.4;
}
```

- defines primary, secondary and background colours
- style of buttons on the page
- added a hero image to a hero section

### Step 6 - Create the Exercise Model and Controller

- next: create the exercise model and controller
- model = contains information about the exercises
- controller = handles users' requests and interacts with the database (retrieves data and sends it to the browser)

```
rails g model Exercise name:string trainings:text instruction:text image:string
```

```
 invoke  active_record
      create    db/migrate/20240327165826_create_exercises.rb
      create    app/models/exercise.rb
```

- `exercise.rb` = holds model related logic
- migration file = instructions for a table where Exercise data is stored
- to ensure your database contains only valid data
	- add database validation
		- open Exercise model at `app/models/exercise.rb`
		- add following lines ...

```rb
validates :name, presence: true
validates :trainings, presence: true
validates :instruction, presence: true
```

-  these lines confirm that exercises are saved to your database
- add some `null: false` code to the migration file at `db/migrate` so code looks like this  ....

```rb
class CreateExercises < ActiveRecord::Migration[7.1]
  def change
    create_table :exercises do |t|
      t.string :name, null: false
      t.text :trainings, null: false
      t.text :instruction, null: false
      t.string :image

      t.timestamps
    end
  end
end
```

- now you need to create the exercises controller

```
rails g controller api/v1/Exercises index create show destroy --skip-template-engine --no-helper
```

```
create  app/controllers/api/v1/exercises_controller.rb
       route  namespace :api do
                namespace :v1 do
                  get 'exercises/index'
                  get 'exercises/create'
                  get 'exercises/show'
                  get 'exercises/destroy'
                end
              end
```

- creates a ExercisesController file in the `app/controllers/api/v1` directory with `index`, `create`, `show`, `destroy` actions
- to use these routes, need to add code to your `config/routes.rb`

```rb
Rails.application.routes.draw do
  namespace :api do
    namespace :v1 do
      get 'exercises/index'
      post 'exercises/create'
      get '/show/:id', to: 'exercises#show'
      delete `/delete/:id`, to: 'exercises#destroy'
    end
  end
  root 'homepage#index'
  get '/*path' => 'homepage#index'
  # Define your application routes per the DSL in https://guides.rubyonrails.org/routing.html

  # Reveal health status on /up that returns 200 if the app boots with no exceptions, otherwise 500.
  # Can be used by load balancers and uptime monitors to verify that the app is live.
  get "up" => "rails/health#show", as: :rails_health_check

  # Defines the root path route ("/")
  # root "posts#index"
end
```

- to check the available list of actions, run`rails routes`
- to ensure they run correctly, need to add the logic to get exercises at once
- the Active Record library will help with that
- for that, open `exercises_controller.rb`

```rb
class Api::V1::ExercisesController < ApplicationController
  def index
    exercise = Exercise.all.order(created_at: :desc)
    render json: exercise
  end

  def create
    exercise = Exercise.create!(exercise_params)
    if exercise
      render json: exercise
    else
      render json: exercise.errors
    end
  end

  def show
  end

  def destroy
  end

  private
  def exercise_params
    params.permit(:name, :image, :trainings, :instruction)
  end  
end
```

```
rails db:migrate
```


### Step 7 - Create a Component for Creating Exercises

- create a component that allows users to create new exercises
- component
	- collects exercise details from user
	- saves the data in the Exercise controller
- create a new file `NewExercise.jsx` in the `components` folder

**NewExercise.jsx**
```jsx
import React, { useState } from "react";
import { Link, useNavigate } from "react-router-dom";

const NewExercise = () =>
{
  const navigate = useNavigate();
  const [ name, setName ] = useState( "" );
  const [ trainings, setTrainings ] = useState( "" );
  const [ instruction, setInstruction ] = useState( "" );

  const stripHtmlEntities = ( str ) =>
  {
    return String( str )
      .replace( /\n/g, "<br> <br>" )
      .replace( /</g, "&lt;" )
      .replace( />/g, "&gt;" );
  };

  const onChange = ( event, setFunction ) =>
  {
    setFunction( event.target.value );
  };

  const onSubmit = ( event ) =>
  {
    event.preventDefault();
    const url = "/api/v1/exercises/create";

    if ( name.length == 0 || trainings.length == 0 || instruction.length == 0 )
      return;

    const body = {
      name,
      trainings,
      instruction: stripHtmlEntities( instruction ),
    };

    const token = document.querySelector( 'meta[name="csrf-token"]' ).content;
    fetch( url, {
      method: "POST",
      headers: {
        "X-CSRF-Token": token,
        "Content-Type": "application/json",
      },
      body: JSON.stringify( body ),
    } )
      .then( ( response ) =>
      {
        if ( response.ok )
        {
          return response.json();
        }
        throw new Error( "Network response was not ok." );
      } )
      .then( ( response ) => navigate( `/exercises/${ response.id }` ) )
      .catch( ( error ) => console.log( error.message ) );
  };

  return (
    <div className="container mt-5">
      <div className="row">
        <div className="col-sm-12 col-lg-6 offset-lg-3">
          <h1 className="font-weight-normal mb-5">
            Add a new exercise to our exercise collection.
          </h1>
          <form onSubmit={ onSubmit }>
            <div className="form-group">
              <label htmlFor="exerciseName">Exercise name</label>
              <input
                type="text"
                name="name"
                id="exerciseName"
                className="form-control"
                required
                onChange={ ( event ) => onChange( event, setName ) }
              />
            </div>
            <div className="form-group">
              <label htmlFor="exercisetraining">Trainings</label>
              <input
                type="text"
                name="trainings"
                id="exerciseTrainings"
                className="form-control"
                required
                onChange={ ( event ) => onChange( event, setTrainings ) }
              />
              <small id="trainingsHelp" className="form-text text-muted">
                Separate each training with a comma.
              </small>
            </div>
            <label htmlFor="instruction">Preparation Instructions</label>
            <textarea
              className="form-control"
              id="instruction"
              name="instruction"
              rows="5"
              required
              onChange={ ( event ) => onChange( event, setInstruction ) }
            />
            <button type="submit" className="btn custom-button mt-3">
              Create Exercise
            </button>
            <Link to="/exercises" className="btn btn-link mt-3">
              Back to exercises
            </Link>
          </form>
        </div>
      </div>
    </div>
  );
};

export default NewExercise;
```


- to access the component on the browser update the `app/javascript/routes/index.jsx`
```jsx
import React from "react";
import { BrowserRouter as Router, Routes, Route } from "react-router-dom";
import Home from "../components/Home";
import NewExercise from "../components/NewExercise";

export default (
  <Router>
    <Routes>
      <Route path="/exercises" element={ <NewExercise /> } />
      <Route path="/" element={ <Home /> } />
    </Routes>
  </Router>
);
```

- import the new component and add the route

### What You Have Now

- You do NOT have a full app
- go to `http://localhost:3000`
	- Homepage
		- button to `View Exercises`
		- clicking on button brings you to `/exercises`
	- NewExercise
		- Form to create a new exercise
		- Exercises are added to the database
		- redirect to `exercise/:id` but no page exists
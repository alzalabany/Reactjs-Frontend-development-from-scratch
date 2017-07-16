# Frontend React.js Client

## Step 2 Task break down

if you have read [Project planning and management](chapter_4/project_planning_and_management.md) you already know how this will go.

## A. create components list and folder structure
* project root
  * delete all files inside /src to start clean :). we dont need create-react-app demos.
  * index.js --> app entry and setup
  * app.js --> main app component or Root component as some people call it
  * createStore.js --> create Redux store;
  * api.js --> setup our apisauce Fetch in this file,
  * rootReducer.js --> our main redux reducer file
  * autoFetch.js --> will create a simple component that will autoamticly fetch new drug data every time any of the drugs filter changes. this way we dont need to worry about API anymore ! it will happen autoamticly.
  * contstants.js --> app configs and constants
  * styles.js --> app main styles
  * actions.js --> app common redux actions
* sidebar
  * Filters /src/filters/index.js
    * Price /src/filters/priceFilter.js
    * Tradename /src/filters/name.js
    * OrderBy /src/filters/orderby.jsƒ
    * company /src/filters/companies.js
    * form /src/filters/forms.js
    * group /src/filters/groups.js
    * Ing /src/filters/ingredients.js
    * \<Select \/\> Select dropdown with search input component /src/components/Select.js
    * Tree Like list with checkboxs /src/components/Tree.js
    * The last 2 components are presentational components that will be reused by some of our filters
* main-content-area
  * Header /src/main-area/header.js
  * Statistics /src/main-area/stats.js
  * company /src/main-area/company.js in case there where only 1 company selected, we will show its name ina nice formated card on top of list.
  * List /src/main-area/drugList.js
  * Index /src/main-area/index.js this is where we will glue all above parts together to compose main content area

#### B. List All Actions

* /ROOT/DRUGS/LOAD_DRUGS/
* /ROOT/FILTER/UPDATE/ (key, value)
* /ROOT/FILTER/CLEAR/

Thats it, our simple app have only 3 behaviours ! 

* 1st to fetch drugs from api. 
* 2nd to set a filter and its value
* 3rd to clear all filters.

#### C. implement all components UI (this is first Task.)

1. open dawaya in terminal
1. lets create all folders needed and all files too. you can use `mkdir` and `touch` commands to do this super fast !.

```shell
  rm -rf ./src
  mkdir ./src && ./src/main-area && mkdir ./src/filters && mkdir ./src/components
  cd ./src
  touch index.js app.js api.js rootReducer.js createStore.js autoFetch.js
  cd ./src/components
  touch Select.js Tree.js index.js
  cd ../filters
  touch index.js priceFilter.js nameFilter.js companyFilter.js groupFilter.js #...etc
```

carry on and create all files we listed in step A. final structure of project should look like following:-

[PIcture of vscode will all files and folders created]()

now we need to setup github.

1. cd back to your daway project root
1. initiate your git repo `git init`
1. commit and push our project `git add . && git commit -m"initial commit" && git push`
1. branch out to design-layout `git branch -b layout-design` in this branch we will create all our ui

Thats it, its straight simple app with only 4 behaviours !, lets save the above list at /src/readme.md so that we can use later.

[open your vscode and lets code, please check my screen cast for how we implemented the ui](https://youtube.com/alzalabany/reactjs-cours "momen's yourtube")

## create all CONSTANTS, TYPES, ACTIONS needed

lets open the readme.md file we created, and copy all behviour list that we saved earlier.
open new file and past the list into it, now we want to generate redux TYPES.

use search and replace function of your vscode, we will use regex search and replace to create file

search for `(.*)/([A-Z_]+)/` and replace it with `exports.types.$2 = "$1/$2/";` . out put that your 
list should now be converted into

```javascript
exports.types.LOAD_DRUGS = "/ROOT/DRUGS/LOAD_DRUGS/";
exports.types.UPDATE = "/ROOT/FILTER/UPDATE/";
exports.types.CLEAR = "/ROOT/FILTER/CLEAR/";
```

see how easy this was :), this is why i keep a list of all behaviours in a readme file, so that i can use this list to generate boilerplate code in future :)

now open `/src/constants.js` and copy past your types into it

```javascript
// constants.js
const exports = {};
exports.types = {};
exports.types.LOAD_DRUGS = "/ROOT/DURGS/LOAD_DRUGS/";
exports.types.UPDATE = "/ROOT/FILTER/UPDATE/";
exports.types.CLEAR = "/ROOT/FILTER/CLEAR/";
export default exports;
```

### create all reducers that will handle those actions.

we will use the types we export in constants, lets create reduer inside every domain.

create 2 reducers files `touch ./src/main-area/reducer.js ./src/filters/reducer.js`

open filters reducer and enter following
```javascript
import {Map, Record, List} from 'immutable';
import { types } form '../constants';

const filtersShape = Record({
  name: String(''),
  price: List([0,1]),
  groups: Map({}),
  forms: Map({}),
  company: Map({}),
  ingredients: Map({}),
})

export const initialState = new filtersShape({});

export function filtersReducer(state = initialState, action){
  if(action.type === '/ROOT/FILTER/CLEAR/') return initialState;

  if(action.type === '/ROOT/FILTER/UPDATE/') return state.set(action.key, action.value);
  
  return state;
}
```

Thats simple, next reducer is Drugs reducer, this one will update our store with new data that arrives from server.

add this reducer to `main-area/reducer.js`

```javascript
import {Map} from 'immutable'

export function drugsReducer(state={}, action){
  if(action.type === '/ROOT/DRUGS/LOAD_DRUGS/') return Map(action.payload);
  
  return state;
}
```

one thing we need to consider is cacheing !. how are we going to cache requests ? should we do it in application logic ?

Answer to this is no, i will prefer to handle cache inside the server-worker, advantages of this

1. easier implementation, drugsReducer now dont need to merge new data
1. service-worker runs on another thread, so our app will now be utlizing multiple threads, which will give a greate bonuce performance
1. its very easy to setup caching in service-workers. way easier than amount of hacking required if we where to implement this in react-redux.

Thans it we have all our reducers. lets create our root reducer :)

inside ./src/rootReducer.js
```javascript
import { drugsReducer } from './main-area/reducer.js'
import { filtersReducer } from './filters/reducer.js'
import { Record } from 'immutable';

const initialState = new Record({
  drugs: drugsReducer(underfined,{type:'@@getInitialShape'}),
  filters: filtersReducer(underfined,{type:'@@getInitialShape'}),
});

const reducers = { 
  drugs: drugsReducer,
  filters: filtersReducer,
}

export default function rootReducer(state=initialState, action){
  let newState = state;
  Object.keys(initialState).map(key=>{
    newState = 
  })
}

```

* If you are the one who will create backend, now is a good time to do it !, make sure backend endpoints return same data in same shape as your current static lists in your app.
* replace static lists with actual remote fetch calls if they are from remote origin, or by connecting your component and getting data from redux store.
* Grap a cup of coffee and celebrate ! your have finished work :) !
* Finish by making sure all your code is Clean and properly Documented.
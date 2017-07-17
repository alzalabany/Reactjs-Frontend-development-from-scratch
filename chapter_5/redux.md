# Redux

Redux create a singelton **store** this store is basicly just a large JS object that we will use to save all data needed for our application,

Redux api is very simple [review our createStore.js and /src/index.js]((https://github.com/alzalabany/course-frontend.git)) for how we created the redux store for this app

Insert/Updating data to this store is done in something called "Reducers" these reducers are **Pure function** pure functions are functions that doenot produce any side effect, [check appened programmin-types for more information about pure functions and Functional Programming](appendix/programming-types.md) .

these Reducers takes in **the store/or/peace of it**, and an Action that instruct reducer what to do, and return a new Store.

example

```javascript
function reducer(store, action){
  if(action.type==='add')return store+action.payload

  store
}
const store = 1;
reducer(store)
reducer(store, {type:'add' payload: 3});
```

this is a simple example of reducer in action !. off course in real app the store will be more complicated than that, and and reducer will also be more complicated, for this reason its a good practice to use multiple reducers, every one handle a part of the state, and we create a rootReducer than handle calling every reducer with his own peace of info.

example in our Dawway app our rootreducer will be:

```javascript
import { drugsReducer } from './main-area/reducer.js'
import { filtersReducer } from './filters/reducer.js'
import { Record, fromJS } from 'immutable';

export const initialStateShape = new Record({
  db: fromJS(window.db),
  show_sidebar: true,
  drugs: drugsReducer(undefined,{type:'@@getInitialShape'}),
  filters: filtersReducer(undefined,{type:'@@getInitialShape'}),
});

export const initialState = new initialStateShape({});

const reducers = { 
  drugs: drugsReducer,
  filters: filtersReducer,
}

function handle(name, allState, action){
  const part = allState.get(name);
  let state = reducers[name](part, action, allState);
  
  return part===state ? allState : allState.set(name, state);
}

export default function rootReducer(state=initialState, action={type:'@@ERROR'}){
  
  if(action.type==='RESET')return initialState;

  let newState = Object.keys(reducers).reduce(
    (carry,key)=>handle(key, carry, action)
    , state);

  return newState;
}

```

* here rootReducer if the action had type = reset, it will reset the store to initialState.

* otherwise
  * Loop over every part of the state object `Object.keys(reducers).reduce`
  * call the reducer with this part `handle(key, carry, action)` we also include the whole state as 3rd argument to the reducer.

  example or drugs reducer


add this reducer to `main-area/reducer.js`

```javascript
import {Map} from 'immutable'

const initialState = Map({});

export function drugsReducer(state = initalState, action){
  if(action.type === '/ROOT/DRUGS/LOAD_DRUGS/') return Map(action.payload);
  if(action.type === '/ROOT/DRUGS/LOAD_MORE_DRUGS/') return state.deepMerge(Map(action.payload));

  return state;
}
```

* if action is Load_drugs, it will return those newdrugs and just discard what we have in store,
* if action was Load_More, it will merge new data, with whatever we had before in store.


our 2nd and final reducer is filters reducer

```javascript
import {Map, Record, List} from 'immutable';
import { types } form '../constants';

const filtersShape = Record({
  name: String(''),
  price: List([0,1]),
  groups: Map({}),
  forms: Map({}),
  companies: Map({}),
  ingredients: Map({}),
})

export const initialState = new filtersShape({});

export function filtersReducer(state = initialState, action){
  if(action.type === '/ROOT/FILTER/CLEAR/') return initialState;

  if(action.type === '/ROOT/FILTER/UPDATE/') return state.set(action.key, action.value);
  
  return state;
}
```

we are using ImmutableJS.Records to create initial State, Records are an immutable object that has default values, and doenot allow you to add more attribute to the object, **this way to make sure the object shape stay consistent**.

* we pass emtpy object to filtersShape to create empty initla state in `initialState = new filtersShape({});`
* we return this empty state whenever we want to clear all filter values,
* we set the [key] to value if action was Update,

Now our Filter Actions can be something like.

```javascript
function SetFilterAction(val, key){

  if(['name','price','groups','forms','companies','ingredients'].indexOf(key) === -1)
    console.warn('warrning: you are setting a filter that doenot exists');

  return {
    type: '/ROOT/FILTER/UPDATE/',
    key,
    value: val
  }
}
```

offcourse we need to replace all those '/root/*'  strings with constants that we define in `constants.js` file.

```javascript
// source of /src/constants.js

const exports = {};
exports.types = {};
exports.types.LOAD_DRUGS = "/ROOT/DURGS/LOAD_DRUGS/";
exports.types.ADD_MORE_DRUGS = "/ROOT/DURGS/MERGE/";
exports.types.UPDATE = "/ROOT/FILTER/UPDATE/";
exports.types.CLEAR = "/ROOT/FILTER/CLEAR/";

export const types = exports.types;
export default exports;
```

update reducers now with our constants

```javascript
import {types} from '../constants';
..rest
export function drugsReducer(state = initalState, action){
  if(action.type === types.LOAD_DRUGS) return Map(action.payload);
  if(action.type === types.ADD_MORE_DRUGS ) return state.deepMerge(Map(action.payload));
  ..rest
}
```

[check our source code](https://github.com/alzalabany/course-frontend.git) to view the final shape of 
/src/filters/reducer.js, /src/rootReducer.js and /src/main-area/reducer.js.
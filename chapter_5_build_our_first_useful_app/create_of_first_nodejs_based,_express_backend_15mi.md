## Create Of first NodeJS based, Express Backend (15mins) {#create-of-first-nodejs-based-express-backend-15mins}

This will be a simple -one file- server.js that will consume drugs.json database and allow client to :-

*   Paginate through list of all drugs
*   Search for drugs
*   Filter drugs
*   It will be responsible for returning Drugs collection with all its relations.
*   Return Useful Statistics about Drugs

### Design Application routes {#design-application-routes}

I think I will only need few routes, view screen cast of this course to continue along, but here are few snippets.

This is a Stateless function in reactjs terms.

FiltersComponent, DrugListComponent, and DrugDetailsComponent

Are all components that we need to create so that App.js can load !.

Switch, is a react-router component, it will render the first route that match, and if none match then it will render the &lt;Redirect /&gt; component, which will redirect us to /list so that switch can match first Route when it re render.

Inline styles, is something that give us lots of advantages over classical .css files, including

*   Backing style with components in one place
*   Allow Our code to be ported to Mobile react-native, or Electron app easily.
*   Using libraries like Radium, you still get Auto prefix and all goodies of using .css
*   You can drive styles from calculations, this is something css cannot do !.
*   Saving all Styles. In a .js file that you can share will all your components

We also used **flexible boxes Css “display: flex”** this is new to css, but is much more powerful than old css techniques for layouts.

Now before we continue further we need to agree on rules to keep our JSX clean and reusable

### JSX Rules {#jsx-rules}

1.  Maximum 2 level nesting, if you nest to much this mean you need to split your code into presentational components, this will help having cleaner and easier to maintain and extend code.
2.  Inline style over css classes
3.  Group inline styles into styles.js
4.  If you don’t need state use stateless
5.  Always use proptypes &amp; defaultProps
6.  Document you work.. Always
7.  _Import Btn from ‘lib/btn’_ over _import {btn} from ‘lib’_ to allow webpack to do tree shaking and code splitting automatically without any custom configuration.

More components , now we need 6 more components 1 for each filter ,

this is Healthy, this is how reactjs apps can scale become easier to maintain !
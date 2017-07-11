## Plan our App UI and features. {#plan-our-app-ui-and-features}

This is Dawaya ui, I think it’s good enough, we only want to 1\. Remove filter button from search bar as we will not need it !. and remove items in side menu to contain all filters we want users to be able to use.

In our app we will also show Drug list on right side, using same exact design, yet on left side menu we will show list of filters like

*   &quot;name&quot;: search drugs by name
*   Order By: change ordering
*   &quot;price&quot;: price range {min, and max}
*   &quot;companies&quot;: select checkboxes {show drugs of certain company}
*   &quot;forms&quot;: : select checkbox’s, {show drugs of certain form}
*   “groups” select checkbox {show drugs of certain group}
*   &quot;ingredients&quot;: select checkbox {show drugs that contain ingredients}

as for Drug details screen, we will show exact same details as Dawaya, except that:-

*   We will allow users to click on any ingredient to show all drugs that contain this ingredient
*   We allow user to click on a company to list all its drugs.

Enough talking! let’s write some code we only have 42mins left to finish this project !.

First we do our nodejs express powered backend, then we design routes for app and convert design to html and css
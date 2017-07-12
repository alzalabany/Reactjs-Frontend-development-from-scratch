## How to install libraries in your Reactjs Project {#how-to-install-libraries-in-your-reactjs-project}

To install all these tools you have 2 options

1.  manual open each website and download zip file and extract it them move .js file to you project folder, and every time a new version is released you need to repeat this again, also you need to make sure you download all dependencies “if a library depend on jQuery they you need to include jQuery also”, then you need to manual include all script; tags in index.html.. **THIS IS BAD and counter productive**
2.  use package manager to do all that for you in a single command!. **This is good**/standard practice in frontend development as described in Chapter 1 of this course.

#### Diffrence between yarn and npm installation command

| Npm | Yarn |
| --- | --- |
| npm install --save ..libraries | yarn add  ..libraries |
| npm install –-save-dev ..lib | yarn add -d ..lib |

*i prefer to use yarn for this course, but if you want to just use npm its fine, just replace the "add" with install, and dont forget to add the --save argumment*

to install all libraries in 1 command 1<sup>st</sup> open terminal and make sure you are in dawaya folder

```bash
yarn add apisauce font-font-awesome immutable Lodash material-design-icons-  awesome immutable Lodash material-design-icons-iconfont moment offline-plugin react react-dom react-redux react-router react-router-dom redux reselect sanitize.css
```

Then to install Development dependencies *libraries that will only be included during development and will not be included in production build use* `yarn add -d prop-types eslint-config-airbnb`

These two libraries are only usefull in debug mode, for this reasone i used the -d flag, no need to include them in production :) !


Above 2 commands will simply Do all steps we mentioned in step 1 automatically for you !, and will save all files in “node_modules” folder, and keep track of all versions for you too !.

Command is simple yarn add ..list of libs you want to add.

As you can see, both yarn and npm use very similar commands, from now on, we will be using yarn only in this course.

Now open package.json file it should look like following

In future if you want to remove a library, or upgrade a library

you can also use yarn to do it and it will automatically handle

everything for you !!
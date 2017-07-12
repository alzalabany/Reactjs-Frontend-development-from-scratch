## How to install libraries in your Reactjs Project {#how-to-install-libraries-in-your-reactjs-project}

To install all these tools you have 2 options

*   *   1.  manual open each website and download zip file and extract it them move .js file to you project folder, and every time a new version is released you need to repeat this again, also you need to make sure you download all dependencies “if a library depend on jQuery they you need to include jQuery also”, then you need to manual include all &lt;script&gt; tags in index.html.. **THIS IS BAD and counter productive**
        2.  use package manager to do all that for you in a single command!. **This is good**/standard practice in frontend development as described in Chapter 1 of this course.

| Npm | Yarn |
| --- | --- |
| npm install --save apisauce font- | yarn add apisauce font- |
| npm install –-save-dev prop-types eslint-config-airbnb | Yarn add -d prop-types eslint-config-airbnb |

Above 2 commands will simply Do all steps we mentioned in step 1 automatically for you !, and will save all files in “node_modules” folder, and keep track of all versions for you too !.

Command is simple yarn add ..list of libs you want to add.

As you can see, both yarn and npm use very similar commands, from now on, we will be using yarn only in this course.

Now open package.json file it should look like following

In future if you want to remove a library, or upgrade a library

you can also use yarn to do it and it will automatically handle

everything for you !!
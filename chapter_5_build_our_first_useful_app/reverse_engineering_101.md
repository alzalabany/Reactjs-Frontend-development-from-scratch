## Reverse Engineering 101 {#reverse-engineering-101}

### What is Daweay.com/app ? {#what-is-daweay-com-app}

*   Progressive Web application
*   Built with Ionic (Angular.io&gt;v2)
*   It use Material Design
*   It list all drugs in Egyptian pharma
*   Click on any drug and you view details about this drug
*   You can search list on right side by using search bar on top, and selecting which attribute to search by click on filter button on right side of search box
*   It use static JSON file to hold all drugs database, the database is an array that contain 13,000++ drug object (collection of drugs [ {drug..}, {drug..} ]
*   Json although static file, the chose not to include it using a script tag, and use Angular Fetch to load the database once app is loaded. So you will see a spinner once app load this spinner will disappear once drugs.json file is downloaded
*   It use the id of the drug to point to its picture “/assets/pictures/[id].png”
*   They have 11 colors in the website theme .. You can use http://bgrins.github.io/devtools-snippets/#allcolors snippet to extract colors used in any website !.
*   They cache the database.json file using service worker “this is why it’s called progressive web app because it can work offline as all static files are cached on client browser using service workers”

Screen 1 homepage drug list

Screen 1 filter modal

Screen 2 drug information

| Quest 1 |
| --- |
| To keep things timed, and challenging, we will try to finish our |
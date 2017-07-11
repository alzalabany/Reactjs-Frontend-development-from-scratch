## Setup Project {#setup-project}

### First Command-line usage {#first-command-line-usage}

Open command line, and navigate to home folder where you want to save this course work (Desktop ?).

&gt;mkdir course-workspace

&gt;cd course-workspace

&gt;create-react-app dawaya

&gt;code .

&gt;cd dawaya

&gt;touch database-generator.js

in above, we create course-workspace folder, which we will use to save all this course work from now on, navigate inside folder using cd, then created our first reactjs Application using create-react-app tool which we installed earlier in Chapter 2, then we launch vscode in root folder with “code .” command.

### Basic recommended libraries for any reactjs Project {#basic-recommended-libraries-for-any-reactjs-project}

*   **prop-types** “library used during react development, it was part of react but moved out to its own lib”
*   **Immutable.js**
*   **React-proptypes**
*   **Redux**
*   **React-router**
*   A **reset.css** library
    *   reset/normalize css are styles that remove cross browser differences in look of html
*   A **react u.i. library** of your choice “react-toolbox, material-ui, react-bootstrap”
*   **a css library** “bootstrap, Materialize css, Foundation, mdl” or any other of your choice !
*   For ajax server communication I use &quot;**apisauce**” which is based on excellent axios lib.
*   **Icons library** [&quot;font-awesome”, material-design-icons-iconfont, ionicons, or all of them !]
*   **Airbnb-eslint-styles** or any eslint config you prefers.

### Special case libraries I yet prefer to include them all in initial setup {#special-case-libraries-i-yet-prefer-to-include-them-all-in-initial-setup}

*   Select :- Create advanced memorized selectors for your data –more about that later
*   Moment.js :- make manipulating Dates in js very easy and fun moment.add(1,’day’).subtract(‘1’,’month’).toCalendar() //hurray!
*   Lodash :- a collection of super-fast JavaScript helpers “slice and array, filter objects etc..”
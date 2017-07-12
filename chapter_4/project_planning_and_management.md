# Project planning and management {#project-planning-and-management}

Any project starts with simple steps

* create User story back log
* create UI design
any thing from a professional PSD designed by a professional designer
or a simple powerpoint slide you do your self, or even a good old paper and pen sketch that you draw will do.
but you **must** have a visual representation of the idea and of all user story board.
* distruct each user store into tasks backlog
Her comes hairy part, you need to distruct each user story into small doable tasks, and assign them to a personal in you team.
if you are working along, this is still no execuse to skip this point, just create all tasks and assign them to your self.

## Pro Tips

* use github branchs to organize your tasks
* use numbered list to order all your tasks, and sub nest list under every branch name for example check [chapter 5 planning](chapter_5/plan_our_app_and_features)

a good plan can looks like

* User story backlog
  * a user can login using his email and password
  * a user can reset his password using email
  * a user can create new account using [email, password]
  * a user can verify his email after registration using email token
* Tasks backlog
  * Master branch
    * create UI sketch design
    * distruct design into routes, and component list and document them in project root README.md file
    * create proper file structure
    *task description : .... etc should list all files and folder under every task you should specify details, tutorials links anything that will help person assigned to do his task
    * layout-design branch
      * create 3 columns layout with center column stretched as per design
      * create login box html & css
      * create reset password box html & css
      * create account acctivation box html & css
    * login-behaviour branch
      * create login actions
        * login
        * validate login info and return errors if any.
      * create reset password
        * validate email and send to server.
        * if a reset token  present in url, then validate the token
        * if user has valid token then show create new password inputs.
      * create account acctivation box html & css in scope of Reactjs every feature you can break tasks of creating any react app into following.

in above example, team should wait for work on master to finish, then 2 teams will split and branch our of master while they work on there own tasks.
every task should be destructred as small as possible, and any discription should be attached.

following lets see how we do these in react scope world.

----

* create components list required to build this ui, -[remember the JSX rules we mentioned before](../chapter_3/jsx.md)-
* list all actions and user interactions as capitalized / separated list [chapter 5 planning for example](../chapter_5/plan_our_app_ui_and_features.md), these lists will construct your redux action TYPES in future.
  * [FEATURE]/[ACTION]/[OPTIONAL INFO] \(params you will pass in action\) remember to always start and end with /, just like namespacing concept in some programming languages :). 
    * Example
      * /LOGIN/GET_INFO/
      * /LOGIN/VALIDATED_CREDENTIALS/ \(usernmae, password\)
      * /LOGIN/VALIDATE_DATA/ \(usernmae, password\)
      * /LOGIN/LOGOUT/
      * /LOGIN/RESET/SEND_EMAIL/
      * /LOGIN/RESET/VALIDATE_TOKEN/ \(email, token\)
      * etc..
  * now save this list in your readme.md file inside feature/app folder, keep it in same raw format it will be very usefull as a seed for documentation, and to convert it into constants, functions with names
* implement all components UI, don't even bother with behaviour at this point, you only want a static good looking app that meets the product manager requirements. -if your app use data that it will fetch from remote website, use static list that mock the data you will get from remote host for now. we are only concerned with UI and UX at this phase
* create all CONSTANTS, TYPES, ACTIONS needed.
* create all reducers that will handle those actions.
* If you are the one who will create backend, now is a good time to do it !, make sure backend endpoints return same data in same shape as your current static lists in your app.
* replace static lists with actual remote fetch calls if they are from remote origin, or by connecting your component and getting data from redux store.
* Grap a cup of coffee and celebrate ! your have finished work :) !
* Finish by making sure all your code is Clean and properly Documented.

in above list, you can split tasks into :

* Design work from *3
* 4,5,7,8,9 Frontend work
* 6 Backend work

in a proper team setup, all your 3 teams can even work on parallel, none. the only show stopper that during your planning phases you should be already **Set** with the shape of data that the server will return to the client, this is essential for frontend, designers and backend teams to be able to plan how they will impelement and handle such data.
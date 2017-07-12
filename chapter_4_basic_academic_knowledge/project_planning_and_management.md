## Project planning and management {#project-planning-and-management}

Any project starts with simple steps

1. create User story back log
2. create UI design
any thing from a professional PSD designed by a professional designer
or a simple powerpoint slide you do your self, or even a good old paper and pen sketch that you draw will do.
but you **must** have a visual representation of the idea and of all user story board.
3. distruct each user store into tasks backlog
Her comes hairy part, you need to distruct each user story into small doable tasks, and assign them to a personal in you team.
if you are working along, this is still no execuse to skip this point, just create all tasks and assign them to your self.
**Pro Tips** 
  1. use github branchs to organize your tasks
  2. use numbered list to order all your tasks, and sub nest list under every branch name for example check [chapter 5 planning](chapter_5/plan_our_app_and_features)

a good plan can looks like

* User story backlog
  * 1. a user can login using his email and password
  * 2. a user can reset his password using email
  * 3. a user can create new account using [email, password]
  * 4. a user can verify his email after registration using email token
* Tasks backlog
  * Master branch
    1. create UI sketch design
    2. distruct design into routes, and component list and document them in project root README.md file
    3. create proper file structure
    *task description : .... etc should list all files and folder under every task you should specify details, tutorials links anything that will help person assigned to do his task
    * layout-design branch
      1. create 3 columns layout with center column stretched as per design
      2. create login box html & css
      3. create reset password box html & css
      4. create account acctivation box html & css
  * login-behaviour branch
    1. create login actions
      1. login
      2. validate login info and return errors if any.
    2. create reset password
      1. validate email and send to server.
      2. if a reset token  present in url, then validate the token
      3. if user has valid token then show create new password inputs.
    3. create account acctivation box html & css in scope of Reactjs every feature you can break tasks of creating any react app into following.

in above example, team should wait for work on master to finish, then 2 teams will split and branch our of master while they work on there own tasks.
every task should be destructred as small as possible, and any discription should be attached.

following lets see how we do these in react scope world.
----

1. create components list required to build this ui, -remember the JSX rulles we mentioned before-
2. list all actions and user interactions as capitalized / separated list [chapter 5 planning for example](chapter_5/plan_our_app_and_features), these lists will construct your redux action TYPES in future.
3. implement all components UI, don't even bother with behaviour at this point, you only want a static good looking app that meat requirements. -if your app use data that it will fetch from remote website, use static list that mock the data you will get from remote host for now. we are only concerned with UI and UX at this phase
4. create all CONSTANTS, TYPES, ACTIONS needed.
5. create all reducers that will handle those actions.
6. If you are the one who will create backend, now is a good time to do it !, make sure backend endpoints return same data in same shape as your current static lists in your app.
7. replace static lists with actual remote fetch calls if they are from remote origin, or by connecting your component and getting data from redux store.
8. Grap a cup of coffee and celebrate ! your have finished work :) !
9. Finish by making sure all your code is Clean and properly Documented.

in above list, you can split tasks into :
1. Design work from 1-3
2. 4,5,7,8,9 Frontend work
2. 6 Backend work

in a proper team setup, all your 3 teams can even work on parallel, none. the only show stopper that during your planning phases you should be already **Set** with the shape of data that the server will return to the client, this is essential for frontend, designers and backend teams to be able to plan how they will impelement and handle such data.
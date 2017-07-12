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

in scope of Reactjs every feature you can break tasks of creating any react app into following.

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
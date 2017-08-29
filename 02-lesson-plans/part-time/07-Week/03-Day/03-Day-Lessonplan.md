## 7.3 Lesson Plan - Firebase Application Building

### Overview

In this class, we will be using Firebase and MomentJS to create a real-world application for calculating billable hours.

`Summary: Complete activities 17-21 in Unit 07`

##### Attention: If you’re teaching a part time section and this isn’t a Saturday, please use the “Weekday” tab inside of the "03-Day-TimeTracker.xlsx" for activity lengths instead of those printed on this lesson plan

##### Instructor Priorities

* Students should understand the following Firebase methods `.push({})` and `.on("child_added")`

* Students should understand the utility of the MomentJS library

* Students should complete and understand the TimeSheet Application

* Students should complete and understand the Train Prediction Activity

* Students should build their confidence at building applications from scratch

* Students should be broken up into groups of 3-4 (by section) for next week's project week

##### Instructor Notes

* Today's class is all about giving students ample room to work through the entire development process. This means leaving them enough time to design an app, figure out how to transmit and retrieve data from a database, and utilize the data collected to calculate new results.

* Today's in-class activity is _highly_ related to the Train Time homework assignment, and as such, merits significant effort from students.

* Prior to class, you will need to create three Firebase databases for use in today's lecture. Place the config from the first database you create into the `01-TimeSheet` example, the second into the `02-Push` examples, and the third into the `03-Add_Child` examples.

  * **Your 1st new Firebase DB Goes Here**

    * `timesheetLogic.js` in `17-TimeSheet`
      ![1st New DB](Images/1-Timesheet.png)

  * **Your 2nd new Firebase DB Goes Here**

    * `01-recent-user-with-set.html`, `01-recent-user-with-set.html`, and `02-recent-user-with-push.html` in `18-Push`
      ![2nd New DB](Images/2-RecentUser.png)

  * **Your 3rd new Firebase DB Goes Here**
    * `recent-user-with-all-users.html` and `recent-user-with-all-users-solved.html` in `19-Add_Child`
      ![3rd New DB](Images/3-RecentUserWithAll.png)


* Also, next week is project week! As such, you will need to divide students into groups of 3-4 (by section) at the end of class. When choosing groups be sure to consider aspects like: personality, coding proficiency, leadership, etc. Try to form groups in which no one will be left idle, de-motivated, or alienated. We want project week to be a positive experience for everyone.

* Have your TAs reference [03-Day-TimeTracker](03-Day-TimeTracker.xlsx) to help keep track of time during class.

- - -

### Class Objectives

* To provide a "real-world" application development scenario that utilizes HTML, CSS, Databases, and Data Manipulation

* To introduce the concept of creating lists and children using Firebase

* To introduce the MomentJS library for date-time manipulation

- - -

### 1. Instructor Do: Scenario Introduction + Today's Group Formation (15 min)

* Welcome students and ask if there are any lingering questions, concerns, revelations, or thoughts from the previous class.

* If there are none, open up the link to the [Employee Time Tracker App](https://time-sheet-55009.firebaseapp.com/) or open the local version of the `17-TimeSheet` application in a browser. (Don't slack the URL to students or else they will be able to download the source).

* Inform students that today's class will be to re-create this application.

![2-employeetracker](Images/4-EmployeeTracker.png)

* In discussing the app, point out that this application is intended to serve as a way for employers to monitor their employee names, roles, start dates, lengths of employment, monthly rates, and total amounts billed.

* Create an example employee using the Add Employee Panel. When doing so, be sure to point out that we are only inputting "some" fields and that the application is calculating the remaining fields using the initial inputs.

* Finally, break students into groups of three. Each group must have at least one student from each section. (Groups can be pre-determined or self-selected).

### 2. Everyone Do: Where's the Data? (5 min)

* Pose the questions to students:

  * "Which fields MUST BE in the database?"

  * "Which fields can we avoid sending to the database in favor of calculating locally?

### 3. Instructor Do: App Backend Demo (5 min)

* Open your local version of the `17-TimeSheet` application as well as your Firebase database so that they are side-by-side.

* Then create a new employee and demonstrate that the only fields being saved in the database are:

  * Employee Name
  * Role
  * Start Date
  * Monthly Rate

    ![3-Keyfields](Images/5-Tracker.png)

* Ask students why this approach might have advantages over uploading every calculated field into the DB.

* Explain to students that this approach of storing limited data on the backend has its advantage because it allows us to avoid "constantly" sending updates to the database every month (or in other situations, every second) as employees' tenures grow.

* Let students think about this for a moment and then have them move onto their first activity of the class.

### 4. Students Do: Main Application Design Phase (20 min)

* Instruct students that for the first phase of today's class, they will be focused on re-creating (or improving) the front-end design of the Employee Data Management page you showed earlier.

* Then slack out the following instructions:

* **Instructions:**

  * For the next 20 minutes, focus all your efforts on creating the application layout for your site.

  * This phase involves both:

    * Creating the overall HTML/CSS/Bootstrap Layout

    * Creating the initial `.on("click")` event that will dynamically trigger new HTML rows to be generated.

  * This phase DOES NOT involve sending or receiving data to Firebase.

  * If you finish early:

    * Continue refining the design! Take things to the next level. Make this application portfolio-grade!

    * Begin reading about `push({})` and `.on("child_added")` in the Firebase documentation.

### 5. Instructor Do: Intro to Push (15 min)

* Confirm that all students were able to create an initial design. If any students are significantly behind and were unable to create an initial layout, instruct a TA to work with that group to help them catch-up during the next phase. (In today's class, we won't be offering "catch-up" code as we would normally. This is all about giving them their first taste of project week).

* Then open up the file `01-recent-user-with-set.html` in `18-Push`. Remind students that this is the same application we've worked on before. Create a new user to remind students how it replaces the most recent member on the screen and how, when you close the browser and re-open it, the same member is still displayed.

* Now open the database attached to your `01-recent-user-with-set` example. Point out that whenever you create a new member it isn't actually _saving_ the new member, it's just replacing it with the latest one.

  * 1st submission...

    ![4-set_1](Images/6-Frodo.png)

  * 2nd submission ("Where's Frodo??)...

    ![4-set_2](Images/7-Tobias.png)

* Explain that this is the limitation of the `.set({})` method we've been using since it will override all data in the directory.

    ![4-set_3](Images/8-Set.png)

* Now go back to the code and then replace the `.set({})` method the `.push({})` method.

    ![5-push_1](Images/9-Smallpush.png)

* Refresh the page in your browser and once again add a new user. Point out how this time, instead of replacing the old member, Firebase created a new separate entry. Create a few more users and allow students to see how the database responds.

    ![5-push_2](Images/10-Push.png)

* Explain that each of these entries that Firebase is creating are called "children".

* Answer any questions students may have about this and then slack out the file `02-recent-user-with-push.html` in `18-Push` for them to see.

### 6. Students Do: Main Application - Push Phase (25 min)

* Now, instruct students to return to their main Employee Tracker application and slack out the following instructions.

* **Instructions**

  * Using your newfound knowledge of the `.push({})` method, create the code necessary to push employee data into the database upon clicking the `submit` button on your webpage.

  * NOTE: Don't worry about getting the data to display in the HTML just yet. Just focus on getting data pushed to the database.

  * If you finish early, begin reading about `.on("child_added")` in the Firebase documentation and/or the MomentJS library.

### 7. Instructor Do: Intro to Child_Added (15 min)

* Open the file `recent-user-with-all-users-solved.html`in `19-Add_Child` in the browser. Demonstrate to students how the previous Recent-User example has been expanded to not only showcase the most recent users, but also to create a running list of users.

* Show students that the Firebase Database is keeping a running list of all the users as "children" and that we are using a new Firebase method to retrieve and display the children data in our HTML.

![6-childadded_2](Images/11-childadded_2.png)

* Now, open either `recent-user-with-all-users.html` or `recent-user-with-all-users-solved.html` in `19-Add_Child` in Sublime. (If you'd like to attempt live-coding choose the unsolved version. If you're short on time or feel more comfortable just explaining open the solved version.)

* Walk students through the process of creating this new functionality using the below details as a guide.

  * First, point out that we've kept the same .push({}) method to send data into our database.

  * Be sure to point out that we've added a special property called `Firebase.ServerValue.TIMESTAMP`. This will add a timestamp in unix format in our database.

    ![6-childadded_3](Images/12-Timestamp.png)

  * Next, show them that instead of using the `.on("value")` function, we have replaced it with `.on("child_added")`. Explain that this event gets run both at the start of our application run AND whenever a new child (i.e. user) is added to the DB. Point out that all data is stored in the `childSnapshot` variable.

    ![6-childadded_4](Images/13-ChildAdded.png)

  * Finally, show them that we have this `.orderByChild` method which sorts all or the records in our database by date and then shows us only the most recent record (for the "Recent Member" Panel). Again that record is stored in `snapshot` variable.

    ![6-childadded_5](Images/14-OrderBy.png)

* Give students a few moments to ask questions before slacking out the code to them.

* Let them know that they will be using this code as an example for their Employee Tracking application.

### 8. Students Do: Main Application - Child_Added Phase (25 min)

* Now instruct students to return to their main Employee Tracker application and slack out the following instructions.

* **Instructions**

  * Using your newfound knowledge of the `.on("child_added")` method, begin to retrieve your employee data from the database and populating the records into your table.

  * Note: Don't worry about calculating Months Worked or the Total Billed just yet. Just focus on retrieving the data that is already in the database.

  * If you finish easily, continue refining the aesthetics of your website, consider incorporating "update" or "delete" employee buttons, or begin reading up on the MomentJS library.

- - -

### 9. LUNCH (40 min)

- - -

### 10. Instructor Do: Intro to MomentJS (5 min)

* Go to the [MomentJS Library](http://momentjs.com/) website.

* Begin to explain that, in web development, there are often numerous instances where one needs to work with or manipulate dates and times. Using native JavaScript this can be difficult because parsing out a date like "3/3/2016 03:25 AM" is not straightforward.

* Explain that MomentJS provides a standardized set of tools for parsing, adding, subtracting, and comparing datetimes.

* Show students a very simple example of using the momentjs library. As a suggestion you can use the code in `momentjs-instructor.html` in `20-MomentJS` as an example of formatting the current datetime into a readable format.

  ![7-moment_1](Images/15-moment_1.png)

### 11. Students Do: MomentJS Activity (15 min)

* Now let students know that as web developers one challenge that's a big part of the job is reading documentation and quickly becoming familiar with how to use it on your own. So for the next few moments they will be working on an activity in which they will use more advanced features of the MomentJS library.

* Slack out the following file and instructions to students.

* **File:**

  * `momentjs-activity.html` in `20-MomentJS`

* **Instructions:**

  * Complete each of the activities listed in the comments.

  * Note: You don't need to go in order.

  * Note: Don't let the simple example fool you. Working with a new library can be tough. Be prepared to get frustrated. Stick with it!

### 12. Instructor Do: MomentJS Activity Review (5 min)

* Offer to let students come to the front and solve whichever questions they were able to solve.

* Open the `momentjs-activity-solved.html` file and walk students through the solution. Remind them that this was a hard activity!

  ![7-moment_2](Images/16-moment_2.png)

* Slack out the solution when done.

### 13. Students Do: Main Application - Datetime Manipulation (10 min)

* Now, have students attempt to complete the Employee Tracker application, utilizing their newfound datetime knowledge to calculate the number of months worked and subsequently the total amount billed.

* Instructors and TAs should be walking around to see how students are doing.

### 14. Instructor Do: Recap the Employee Tracker application (5 min)

* Open the `timesheetLogic.js` in `17-TimeSheet`.

* Spend a little time reviewing the Employee Tracking Application. Don't expect to walk students through everything. Keep things at a high-level, and encourage students to look back at this working code. It is nearly identical in structure to the TrainTime Homework.

* Key points to emphasize:

  * There are two major `.on` events.

  * The first is the `.on("click")`. This event takes data from the textboxes and relays it to the database.

    ![8-mainex_1](Images/17-OnEvents.png)

  * The second is the `.on("child_added")`. This event retrieves data from the database and displays it in the HTML. This event gets run both at the beginning of the application's launch and each time a new entry is added to the database.

    ![8-mainex_2](Images/18-OnChild.png)

  * Finally, point out that we use moment.js to calculate the difference between the current time and the time of the employee's start date. Let students know that they will have one more example of using MomentJS that will help if they struggled with this part (the next activity).

* Don't get so buried in the explanation of this app that you don't get to the next set of activities. The next few activities are critical to the homework's completion!

### 15. Everyone Do: Traintime Prediction (Math) (10 min)

* Open the Homework-4 solution for TrainTime in the browser. (Alternatively go to <https://train-times-93583.firebaseapp.com/>)

* Remind students how this application works. Point out that, in this application, administrators input the time for the first train of the day and the frequency with which a train arrives at a station. With this information the application AUTOMATICALLY calculates the next arrival time.

* This is trickier than it seems and requires a bit of math.

* Let them know that you won't be giving them the answer to this question.

* Then slack out the following instructions to students:

* **Instructions:**

  * With your group write out the steps you would use "mathematically" to determine the answer to the following situation:

  * Assuming:

    1. The first train of the day comes in at 3:00 AM.
    2. The train runs every 17 minutes
    3. The current time is 7:12 PM.
    4. There have been no delays and will be no delays.

  * Question:
    1. How many minutes away is the next train?

### 16. Everyone Do: Traintime Prediction (Code) (15 min)

* Again, let students know that you won't be giving them the answer.

* Instead, slack out the following:

* **File:**

  * `train-example.html` in `21-TrainPredictions`

* **Instructions:**

  * Using the comments in the code as a guide, determine the mathematical formula for calculating train times.

  * Then explain to one another how the code works (line by line) and how it could be used in relationship to the homework assignment.

### 17. Instructor Do: Project Group Formation (5 min)

* As a final activity for the day, let students know that the next two weeks will be Project Weeks.

* Then, slack out the Team lists along with the below information.

* **Instructions:**

  * Project Goal:

    * Build Something Awesome

  * Requirements:

    * Must uses at least two APIs

    * Must use AJAX to pull data

    * Must utilize at least one new library or technology that we haven’t discussed

    * Must have a polished frontend / UI

    * Must meet good quality coding standards (indentation, scoping, naming)

    * Must NOT use alerts, confirms, or prompts (look into modals!)

    * Must have some sort of repeating element (table, columns, etc)

    * Must use Bootstrap or Alternative CSS Framework

    * Must be Deployed (GitHub Pages or Firebase)

    * Must have User Input Validation

  * Presentation Date:

    * Two Weeks from Today

* Let them know that more information will be provided next class.

* Be pumped!

### 18. Slack out the Video Guide

* Slack out the video guide for this week's key activities and last week's homework! Emphasize how helpful a tool these videos can be if a student feels as if they are falling behind or simply wants to review the material once again.

* [Video Guide](../VideoGuide.md)

- - -

### Copyright

Coding Boot Camp (C) 2015. All Rights Reserved.

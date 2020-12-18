---
layout: project
type: project
image: images/study-dojo-small.png
title: Study Dojo
permalink: projects/study-dojo
date: 2020-12-17
labels:
  - Meteor
  - Javascript
  - Semantic UI React
summary: An app for students to organize study sessions for a class.
---

<img class="ui image" src="../images/study-dojo-home.png">

[Study Dojo](https://study-dojo.github.io) was worked on by a group of four students, including me, for our software engineering class. We organize the work using Issue Driven Project Management to design an app using [Meteor](https://www.meteor.com/) for students to organize study sessions amongst themselves. After signing up, they can go to the My Dojo page to register as a "grasshopper" or "sensei" for classes they attend. On the Session List page, the user can create a study session and specific the title of the study session, the class, and the date and time of the study session. This creates a notification to all other users registered for that class, allowing them to register for the study session. Participating in study sessions give users points, that are shown on the Leaderboard page. All study sessions are shown on the Calendar page. The creator of the study session can delete the session, deleting it for all other uses, while other users can unregister themselves from the study session.


For this project, I created the Session List page and used [Semantic UI React](https://github.com/Semantic-Org/Semantic-UI-React) to display the study sessions as cards and linked it to display on a [Full Calendar](https://fullcalendar.io/). On the Add Session page, I created a form to generate study sessions using [uniforms' autoform](https://uniforms.tools/docs/api-forms/). The creation of the study session sends a notification to all other users registered for that class. I also made the calendar show all study sessions.


This was the first project I deployed to a server, thus I learned a lot about using Digital Ocean and setting up HTTPS encryption. The form utilized [simple schema](https://github.com/aldeed/simpl-schema), allowing me to further expand my knowledge on using them. Utilizing the date and time information from the form helped me better understand the system's internal clock and converting it to usable data. Working on the project as a group gave me first hand experience on using Issue Driven Project Management and allowed me to learn more about working efficiently as a group.

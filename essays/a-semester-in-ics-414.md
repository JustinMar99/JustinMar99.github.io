---
layout: essay
type: essay
title: A Semester in ICS 414
date: 2020-09-03
labels:
  - Javascript
  - React
---

## User Experience
Working with Hawaiian Electric Industries (HEI) was an interesting experience. I learned a lot about designing websites for people to use. Within our group, we had to constantly discuss the benefits of certain features and how it affected user experience. For example, we created a "What If" page where users can manipulate their transportation data to see how that affected their green house gas emissions. We also know that people prefer certain looks such as a dark theme, thus we added it in, and to make it clear to the user, we had a switch that showed day then night, depending on which theme was selected. Futhermore, meeting with members of HEI and having them give their input helped in understanding the difference between what we as the developers look for and what they as clients look for. 

## React
This project has improved my understanding of React states. In the previous ICS software engineering class, 314, there was hardly a need to learn React states indepth. For this project, I had to learn about useRef(), such as with:

```javascript
const nMilesSavedPerDay = useRef(_.map(milesSavedPerDay.mode, (mode, i) => ({
        date: milesSavedPerDay.date[i],
        distance: milesSavedPerDay.distance[i],
        mode: mode,
    })));
```
Working on the "What If" page, further increased my knowledge about passing states between different pages and manipulating them allowing states to be transferred between multiple components and pages. This way we were able to separate the form component where user selected data and the component that rendered the data. I also learned more about debugging React states. Before this semester, I was confused about rendering and how to view the state, but after digging more into it this semester, I know how to check what values the states are currently on. Initially, I was confused about functions vs class in React. This semester has helped me learn about when to use each and how to utilize React states in both. In the previous semseter, I used class for React states, thus was initially clueless on setStates() for functions. For example:

```javascript
const handleChange = (event, { value }) => setTransport(value);
```
This simply updates the transport state with value on submitting a form. 

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
I learned a lot working with the Hawaiian Electric Industries (HEI). I learned a lot about designing websites for people to use. Within our group, we had to constantly discuss the benefits of certain features and how it affected user experience. For example, we created a "What If" page where users can manipulate their transportation data to see how that affected their green house gas emissions. We also know that people prefer certain looks such as a dark theme, thus we added it in, and to make it clear to the user, we had a switch that showed day then night, depending on which theme was selected. 

## React
This project has improved my understanding of React states. In the previous ICS software engineering class, 314, there was hardly a need to learn React states indepth. For this project, I had to learn about useRef(), such as with:

```javascript
const nMilesSavedPerDay = useRef(_.map(milesSavedPerDay.mode, (mode, i) => ({
        date: milesSavedPerDay.date[i],
        distance: milesSavedPerDay.distance[i],
        mode: mode,
    })));
```
Working on the "What If" page, further increased my knowledge about passing states between different pages and manipulating them allowing states to be transferred between multiple components and pages. This way we were able to separate the form component where user selected data and the component that rendered the data. I also learned more about debugging React states. Before this semester, I was confused about rendering and how to view the state, but after looking more into it this semester, I know how to check what values the states are currently on. Initially, I was confused about functions vs class in React. This semester has helped me learn about when to use each and how to utilize React states in both. In the previous semseter, I used class for React states, thus was initially clueless on setStates() for functions. For example, this updates the transport state with value on submitting a form. 

```javascript
const handleChange = (event, { value }) => setTransport(value);
```

I also learned more about creating states that stores multiple values, like an array. For example, this code extracts data from milesSavedPerDay to store as a state called "events" for the calendar:

```javascript
    const [events, setEvents] = useState(() => _.map(milesSavedPerDay.date, function (date, i) {
        const year = `${date.getFullYear()}`;
        let month = `${date.getMonth() + 1}`;
        let day = `${date.getDate()}`;

        // Adjust month and day to have 2 numbers if necessary
        if (month.length < 2) {
            month = `0${month}`;
        }
        if (day.length < 2) {
            day = `0${day}`;
        }

        return { id: i, title: milesSavedPerDay.mode[i], date: [year, month, day].join('-'), color: colorType(milesSavedPerDay.mode[i]) };
    }));
```

While updating the state requires more steps than just calling setEvents(). Instead I needed to store the data in events in a new array, manipulate the new array, then call setEvents() using the new array:

```javascript
const eventArr = [...events];
eventArr[selectedEvent.id] = { id: eventArr[selectedEvent.id].id, title: transport, date: selectedEvent.date, color: colorType(transport) };
setEvents(eventArr);
```
## Group
We worked in a bigger group than in ICS 314 and there were pros and cons to both. In ICS 314, I feel working in a smaller group caused me to learn more about what goes on in the code both front-end and back-end, since there was so much more for each individual member to do. I also felt it was easier to coordinate who does what because there was a lot less to split between the members. If I did finish early, it was easy to decide on what to work on next since I knew what I could work on without messing or needing to wait on a different member to finish. In ICS 414, we had more members in the group, thus we could cover more ground easier. However, it meant there was more waiting on other members to finish their work, so that we don't mess anything up. 

---
layout: essay
type: essay
title: Cooking an Omlette
date: 2020-12-03
labels:
  - Design Patterns
---

## A Home Cooked Omlette
Based on my understanding of design patterns, it is like a recipe. Imagine you wake up one morning and are faced with the problem that you want to make some scrumptious omletes, but the question is how? Well, I hope you don't throw something on a plate, crack some eggs on it and put it on the stove top, otherwise I think you need to get your tastebuds checked. You follow steps from a general recipe, where different people have made their own **prototype**, with alterations to the original recipes. After all, creating your own recipes from scratch is just too much for some breakfeast in the morning. Furthermore, its nice that they use the same name for things, a sort of global name for all the different things you need to cook some omletes. Imagine if the world of cooking instead of having **singletons**, had their own jargon for salt and peppers, whisking, frying, etc. It would be such a nightmare for outsiders trying to understand what they are talking about. And of course, you must be a proper **observer** when cooking the omlete. You gotta pour the egg mix on the frying pan when it is whisked enough, and you have to take it off when it is done cooking, or face the consequences. As a cook, you must take care of how you do things, you can salt and pepper the eggs as you're frying them, but don't whisk the eggs as you're frying the omlete, those two things don't mix.

Now while home cooking doesn't require much, if you step into the world of professional chefs, there would be others things to consider. There's now multiple people in the kitchen, and you don't want to get in each other's way. And based on how most restaurants are set up, they don't want you to see how they prepare your food either. They implement a **Model-View-Controller** system where each chef can work, preparing the parts that they specialize in, with the customers only having to view and select their choice off a menu. A restuarant also may have their own special recipe that they don't want leaking out to their competitors. Like a **factory**, they can create and bring out meals without exposing the steps they took to create those meals.

## My Omlette
I have certainly cooked a couple of omlettes before, so let me lay down my experience doing so. For one of my classes, the professor provided us with his recipe on cooking an omlette and as a group, we set about modifying it to create our own **prototype** of the recipe that we can call our own. We have certain areas in our recipe that requires observation to go to the next step. For example:

```javascript
submit(data, formRef) {
    const { topic, className, sessionDate, sessionTime } = data;
    const owner = Meteor.user().username;
    StudySessions.collection.insert({ topic, className, sessionDate, sessionTime, owner },
        (error) => {
          if (error) {
            swal('Error', error.message, 'error');
          } else {
            swal('Success', 'Item added successfully', 'success');
            formRef.reset();
            // find all other users that are registered under the same class
            const sameOwners = _.without(_.pluck(DojoOwners.collection.find({ className: className }).fetch(), 'owner'), owner);

            // Insert an alert for all other users
            sameOwners.map((entry) => Alerts.collection.insert({
              owner: entry,
              topic: topic,
              className: className,
              sessionDate: sessionDate,
              sessionTime: sessionTime,
            }));
          }
        });
```
In this step, we observe when a new doc is succesfully inserted into StudySessions.collection, which then cause a new doc to be inserted into Alerts.collection. 

In our recipe, we also change how the information is handled internally to how the user views it. If we look at the ingredients we prepared before we begin cooking:
```javascript
"defaultAccounts": [
    { "email": "admin@foo.com", "password": "changeme", "role": "admin" },
    { "email": "john@foo.com", "password": "changeme" },
    { "email": "bob@foo.com", "password": "changeme" }
  ],

  "defaultDojo": [
    { "className": "ICS 314", "status": "grasshopper", "owner": "john@foo.com" },
    { "className": "ICS 311", "status": "grasshopper", "owner": "john@foo.com" },
    { "className": "ICS 311", "status": "sensei", "owner": "bob@foo.com"}
  ],

  "defaultStudySessions": [
    { "topic": "Help with HW", "className": "ICS 311", "sessionDate": "11/15/2020", "sessionTime": "Right Now!", "owner": "john@foo.com" },

    { "topic":  "Exam Study", "className":  "ICS 311", "sessionDate": "11/17/2020", "sessionTime": "5:00 pm", "owner":  "john@foo.com"}
  ]
  ```
we prepare a lot of ingredients to use, however, each customer will only see the parts that they ordered and thus are the owner.

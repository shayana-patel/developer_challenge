# developer_challenge
Coding a well-structured, user-friendly UI for scale, with  minimal help from UI libraries/frameworks

# Getting started
To get started:
```
npm i
npm run dev
```
In VS Code run live server to view the web page 

# The Process
The layout was created on a single HTML page using semantic HTML. Styling was done using SCSS. I used node-sass (npm package) to complie SCSS to CSS.

I created wire-frames to plan the layout and figure out the elements I would need.

I used a mixture of grid and flex display for various elements. For the header I used flex display to make it easier for changing flex direction at different viewpoints. For the section element I used grid display. This design decision was made to make it easier to design the page layout without having to use floats and positioning to get elements into the desired layout.

I then used flex display on the section (grid-container) element to make the layout responsive at different viewports. By doing so it meant the content of the grid-container was not squished or cut off on various screen sizes.


NOTE: The puppy images used in the project were taken from the following source [Cuddle Clones]("https://cuddleclones.com/blogs/all/a-simple-guide-for-training-golden-retriever-puppies")

# Written Questions
  Global Variables:
  ```
  let today = new Date();
  let date = today.getFullYear()+"-"+(today.getMonth()+1)+"-"+(today.getDate());

  ```

1. Using .filter()
```

function getActivePlans (arr) {
  let activePlans = arr.filter(plan => plan.endDate > date)
  return activePlans;
}
getActivePlans(plans);

```

2.
```
function sortActivePlans (arr) {
  let sortedPlans = arr.filter(plan => plan.endDate > date)
  .sort(function(a,b) {
    if (a.name < b.name) {
      return -1
    }
    if (a.name > b.name) {
      return 1
    }
    return 0;
  })
}

sortActivePlans(plans);

```

3.
  The Variable Rate:
  ```
  function offPeakVariableRate (arr) {
  let offPeakRate = arr
    .filter(plan => plan.endDate > date && plan.name === 'Off Peak')
    .reduce((obj, plan) => {
      obj[plan.name] = plan.variableRate;
      return plan.variableRate
    },{})
    return offPeakRate;
  }
  offPeakVariableRate(plans);

  ```
  The Day Rate:
  ```
  function offPeakDayRate (arr) {
    let offPeakRate = arr
      .filter(plan => plan.endDate > date && plan.name === 'Off Peak')
      .reduce((obj, plan) => {
        obj[plan.name] = plan.dayRate;
        return plan.dayRate
      }, {})
    return offPeakRate;
  }
  offPeakDayRate(plans);

  ```

4.
```
  function flatPlanCost (arr) {

  let filteredPlan = arr
    .filter(plan => plan.endDate > date && plan.name === 'Flat')

  let flatPlanDayRate = filteredPlan
    .reduce((obj, plan) => {
      obj[plan.name] = plan.dayRate;
      return plan.dayRate * 7
    }, {});

  let flatPlanVarRate = filteredPlan
    .reduce((obj, plan) => {
      obj[plan.name] = plan.variableRate;
      return plan.variableRate * 29 * 24
    }, {});
  
  return flatPlanDayRate * flatPlanVarRate;
}

flatPlanCost(plans);

```
5. Unfortunately I was unable to completely solve this question. I know that a loop is required to iterate through the objects inside the array, however after several attempts the code below is the closest I got. The console.log shows the plans and what their cost is for a 7 day period where 29kWh of electricity is used. 
```
let filteredPlans = plans.filter(plan => plan.endDate > date);
  
  for (let i = 0; i <= filteredPlans.length; i++) {
    let comparePlanCost = ("Plan: " + filteredPlans[i].name + ", cost: " + ((filteredPlans[i].dayRate * 7) * (filteredPlans[i].variableRate * 29 * 24)));
    console.log(comparePlanCost);
}
```


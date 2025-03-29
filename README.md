# Javascript Syntax Cheatsheet
Created for people who know programming but don't know javascript's syntax


&nbsp;


## Variables
Syntax:  
- let (changeable, scoped to block).  
- const (unchangeable value, scoped to block).  
- var (old-school, avoid it—can cause bugs due to weird scope).
```
let reps = 5;          // Can change later
const maxLift = 315;   // Locked, can't reassign
reps = 10;             // Works
// maxLift = 405;      // Error!
```


&nbsp;


## Data Types  
- Number: let weight = 225;  
- String: let lift = "squat";  
- Boolean: let isPR = true;  
- Array: let lifts = [225, 275, 315];  
- Object: let bests = { squat: 405, bench: 315 };
```
let day = "Monday";
let weights = [135, 185, 225];
let pr = { lift: "deadlift", weight: 500 };
```


&nbsp;


## Functions
- Regular: function name() {}
- Arrow (modern, shorter): () => {}
```
function logLift(weight) {
  return weight + 10;  // Adds 10 lbs
}

const addPlates = (weight) => weight + 45;  // Arrow version
console.log(logLift(225));  // 235
console.log(addPlates(225)); // 270
```


&nbsp;


## Conditionals
Syntax: if, else if, else, or ternary (? :).
```
let weight = 315;
if (weight > 300) {
  console.log("Heavy!");
} else {
  console.log("Light.");
}
// Ternary (short if-else)
let message = weight > 300 ? "Beast!" : "Keep going"; // "Beast!"
```


&nbsp;


## Loops
Syntax:
- for: Classic loop.  
- .map(): Loop over arrays, returns new array.
```
for (let i = 0; i < 3; i++) {
  console.log(i);  // 0, 1, 2
}
let lifts = [225, 275, 315];
lifts.map((lift) => console.log(lift));  // 225, 275, 315
```


&nbsp;


## Objects
Syntax: { key: value }.
```
let lifter = { name: "Alex", squat: 405 };
console.log(lifter.name);      // "Alex"
console.log(lifter["squat"]);  // 405
lifter.bench = 315;            // Add new key
```


&nbsp;


## Arrays
```
let days = ["Mon", "Wed", "Fri"];
console.log(days[0]);      // "Mon"
days.push("Sat");          // Add to end
console.log(days.length);  // 4
```


&nbsp;


# ES6 Stuff
## Destructuring: Pull values out easily.
```
let { squat, bench } = { squat: 405, bench: 315 };
console.log(squat);  // 405
let [first, second] = [1, 2, 3];
console.log(first);  // 1
```


&nbsp;


## Template Literals: Fancy strings with variables
```
let lift = "squat";
console.log(`My best ${lift} is 405!`);  // "My best squat is 405!"
```


&nbsp;


## Spread: Copy or combine stuff
```
let oldLifts = [225, 275];
let newLifts = [...oldLifts, 315];  // [225, 275, 315]
```


&nbsp;


## Aysnc stuff
Syntax: async, await, or .then().  
```
async function getMaxLift() {
  let response = await fetch("http://api.example.com/lifts");
  let data = await response.json();
  return data.max;
}
// Or with .then()
fetch("http://api.example.com/lifts")
  .then(res => res.json())
  .then(data => console.log(data.max));
```


&nbsp;


# React Native-Specific
## Components: 
Building blocks of your app, like Lego pieces. Each piece is a chunk of UI (screen stuff) and logic. Think of a component as a reusable workout move—like a "squat" block you can use anywhere. You make components, then stack them to build your app.  
```
import { Text, View } from 'react-native';
const BestSquat = () => (
  <View>
    <Text>Squat: 405 lbs</Text>
  </View>
);
```


&nbsp;


## State: Track changing data
Data that can change while your app runs, like a live scorecard. Imagine tracking your reps—you lift, it updates. That’s state. Use useState to create and update state. When it changes, the screen re-renders (updates).
```
import { useState } from 'react';
import { Text, Button } from 'react-native';
const RepCounter = () => {
  const [reps, setReps] = useState(0); // Starts at 0
  return (
    <View>
      <Text>Reps: {reps}</Text>
      <Button title="Add Rep" onPress={() => setReps(reps + 1)} />
    </View>
  );
};
```


&nbsp;


## Props
Info you pass to a component to customize it. Like telling your squat block, “Hey, this time it’s 315 lbs, not 405.” Props are read-only—components don’t change them.  
```
const BestLift = (props) => (
  <Text>{props.lift}: {props.weight} lbs</Text>
);
// Use it like this:
<BestLift lift="Squat" weight="405" />
```


&nbsp;


## JSX
A mix of JavaScript and HTML-like code to describe your UI. It’s like writing a workout plan in code—looks like tags but works with JS. JSX isn’t HTML—it turns into native mobile stuff (like iOS buttons).
```
const WorkoutLog = () => (
  <View>
    <Text>Deadlift: 500 lbs</Text>
  </View>
);
```


&nbsp;


## Hooks
Special tools (functions) to add features to components. Hooks are like power-ups for your workout blocks. 
- useState: Tracks changing stuff (see State above).  
- useEffect: Runs code when something happens (e.g., app starts or data loads).
Hooks keep your components smart and simple.  
```
import { useState, useEffect } from 'react';
const BestLifts = () => {
  const [squat, setSquat] = useState(0);
  useEffect(() => {
    // Pretend this fetches from your Django API
    setSquat(405);
  }, []); // Empty [] means "run once when component loads"
  return <Text>Squat: {squat} lbs</Text>;
};
```


&nbsp;


## Styling
How you make your app look good. Like choosing gym gear—color, size, position—but in code. No CSS files—just JS. Flexbox is your layout buddy.
```
import { View, Text, StyleSheet } from 'react-native';
const WorkoutBox = () => (
  <View style={styles.box}>
    <Text style={styles.text}>Bench: 315 lbs</Text>
  </View>
);
const styles = StyleSheet.create({
  box: { backgroundColor: 'green', padding: 10 },
  text: { color: 'white' }
});
```


&nbsp;











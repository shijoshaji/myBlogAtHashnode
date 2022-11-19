# simplification Syntax

# For loop in JS

```
// output: John, Mathew, Luke, Mark, Abraham, Issac
```

**Usual way:**
```
const names = ['John', 'Mathew', 'Luke', 'Mark', 'Abraham', 'Issac'];

for (let index = 0; index < names.length; index++) {
  const element = names[index];
  console.log(element);
}
```

**Simplified:**
```
const names = ['John', 'Mathew', 'Luke', 'Mark', 'Abraham', 'Issac'];

// get values in index
for (let ele of names) {
  console.log(ele);
}

// get index
for (let ele in names) {
  console.log(ele);
}
```

# forEach in JS

> Note: forEach dont return anything, it will be `undefined`

We can use `forEach` concept too for above example:
I have divided into 2 ways

**defined function**

```
const names = ['John', 'Mathew', 'Luke', 'Mark', 'Abraham', 'Issac'];

function eachName(item) {
  console.log(item);
}

names.forEach(eachName);
```

**anonymous function**

```
const names = ['John', 'Mathew', 'Luke', 'Mark', 'Abraham', 'Issac'];

names.forEach(function (i) {
  console.log(i);
});
```

Lets see same with different input where its an array of objects, I will use here the anonymous function (*can be achieved with defined function too*)

```
const people = [
  { uName: 'John', role: 'SDE' },
  { uName: 'Mathew', role: 'SDE2' },
  { uName: 'Luke', role: 'SDE4' },
  { uName: 'Mark', role: 'TL' },
  { uName: 'Abraham', role: 'Principal Staff' },
  { uName: 'Issac', role: 'MD' },
];

people.forEach(function (eachPerson) {
  console.log(eachPerson.uName);
});
```

# map in JS

From above example of people, we want to get an array of roles available.

How to achieve this, we can use `map` here, it return `new array`


```
const people = [
  { uName: 'John', role: 'SDE' },
  { uName: 'Mathew', role: 'SDE2' },
  { uName: 'Luke', role: 'SDE4' },
  { uName: 'Mark', role: 'TL' },
  { uName: 'Abraham', role: 'Principal Staff' },
  { uName: 'Issac', role: 'MD' },
];

const roles = people.map(function (item) {
  return item.role;
});

console.log('New Array:', roles);

// output: ["SDE", "SDE2", "SDE4", "TL", "Principal Staff", "MD"]
```

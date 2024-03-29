---
title: "simplification Syntax"
datePublished: Sat Nov 19 2022 06:07:25 GMT+0000 (Coordinated Universal Time)
cuid: clanj31f7000g08jq02vf4czs
slug: simplification-syntax
tags: javascript, map, filter, for-loop, array-javascript-array-methods-map-filter-foreach

---

# For loop in JS

```plaintext
// output: John, Mathew, Luke, Mark, Abraham, Issac
```

**Usual way:**

```plaintext
const names = ['John', 'Mathew', 'Luke', 'Mark', 'Abraham', 'Issac'];

for (let index = 0; index < names.length; index++) {
  const element = names[index];
  console.log(element);
}
```

**Simplified:**

```plaintext
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

We can use `forEach` concept too for above example: I have divided into 2 ways

**defined function**

```plaintext
const names = ['John', 'Mathew', 'Luke', 'Mark', 'Abraham', 'Issac'];

function eachName(item) {
  console.log(item);
}

names.forEach(eachName);
```

**anonymous function**

```plaintext
const names = ['John', 'Mathew', 'Luke', 'Mark', 'Abraham', 'Issac'];

names.forEach(function (i) {
  console.log(i);
});
```

Lets see same with different input where its an array of objects, I will use here the anonymous function (*can be achieved with defined function too*)

```plaintext
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

```plaintext
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

# filter in JS

similar to `map` where we can get new array, but for certain condition alone. Then we can use `filter`

```plaintext
const people = [
  { uName: 'John', role: 'SDE', age: 25 },
  { uName: 'Mathew', role: 'SDE2', age: 25 },
  { uName: 'Luke', role: 'SDE4', age: 30 },
  { uName: 'Mark', role: 'TL', age: 35 },
  { uName: 'Abraham', role: 'Principal Staff', age: 36 },
  { uName: 'Issac', role: 'MD', age: 40 },
];

const youngForce = people.filter(function (item) {
  return item.age <= 30;
});

console.log('Young ppl', youngForce);

//output:
[
    {
        "uName": "John",
        "role": "SDE",
        "age": 25
    },
    {
        "uName": "Mathew",
        "role": "SDE2",
        "age": 25
    },
    {
        "uName": "Luke",
        "role": "SDE4",
        "age": 30
    }
]
```

# find in JS

Similar to filter, but `find` returns one instance, first match value even if multiple values exist. Good for unique values. returns `undefined` if no match found

```plaintext
const people = [
  { uName: 'John', role: 'SDE', age: 25, id: 1 },
  { uName: 'Mathew', role: 'SDE2', age: 25, id: 2 },
  { uName: 'Luke', role: 'SDE4', age: 30, id: 3 },
  { uName: 'Mark', role: 'TL', age: 35, id: 4 },
  { uName: 'Abraham', role: 'Principal Staff', age: 36, id: 5 },
  { uName: 'Issac', role: 'MD', age: 40, id: 5 },
];

const unique = people.find(function (item) {
  return item.id === 5;
});

console.log('unique', unique);

//output: return first match ie Abraham
{
    "uName": "Abraham",
    "role": "Principal Staff",
    "age": 36,
    "id": 5
}
```

### Find Duplicate/Unique in Array

```javascript
const names= ['John', 'Mathew', 'John', 'Issac', 'Abraham', 'Issac'];

const toFindDuplicates = arry => arry.filter((item, index) => arry .indexOf(item) !== index)
console.log(toFindDuplicates (names))

const toFindUnique = arry => arry.filter((item, index) => arry .indexOf(item) === index)
console.log(toFindUnique(names))
```
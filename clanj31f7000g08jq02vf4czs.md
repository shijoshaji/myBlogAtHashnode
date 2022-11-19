# simplification Syntax

# For loop in JS

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


Mutable Types

```js
let userData = {
  name: "Vimal",
  age: 24,
  email: "vimal24@gmail.com",
};

let userDataCopy = userData;

userDataCopy["age"] = 45;

console.log(userData);
console.log(userDataCopy);
```

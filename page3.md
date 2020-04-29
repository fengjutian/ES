* Array.of()  
看段代码
```
new Array(5,10); // [5, 10]
new Array(5); // 长度为5的空数组
```
```
Array.of(5) // [5]
Array.of(5, 10) // [5, 10]
```

* Array.from()  
```
const numbers = [1, 2, 3, 4, 5];
const copy = Array.from(numbers, value => value * 2);
console.log(copy) // [2, 4, 6, 8, 10]
```
```
Array.from(document.scripts)
 .forEach(script => console.log(script.src));
```

* Array.find()  
返回第一个符合的元素
```
const employees = [
 { name: "David Carlson", age: 30 },
 { name: "John Cena", age: 34 },
 { name: "Mike Sheridan", age: 25 },
 { name: "John Carte", age: 50 }
];
const employee = employees.find(employee =>       
employee.name.indexOf("John") > -1);
console.log(employee); // { name: "John Cena", age: 34 }
```

* Array.findIndex()  
```
const employees = [
 { name: "David Carlson", age: 30 },
 { name: "John Cena", age: 34 },
 { name: "Mike Sheridan", age: 25 },
 { name: "John Carte", age: 50 }
];
const index = employees.findIndex(employee => employee.name.indexOf("John") > -1);
console.log(index); // 1
```

* Array.filter()  
```
const employees = [
 { name: "David Carlson", age: 30 },
 { name: "John Cena", age: 34 },
 { name: "Mike Sheridan", age: 25 },
 { name: "John Carte", age: 50 }
];
const employee = employees.filter(employee => employee.name.indexOf("John") > -1);
console.log(employee); // [ { name: "John Cena", age: 34 }, { name: "John Carte", age: 50 }]
```

[链接](https://medium.com/javascript-in-plain-english/insanely-useful-array-methods-b3f93bf5415e)



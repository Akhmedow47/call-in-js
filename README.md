# call-in-js
# call-bind-apply
# Object ва Methods of Object дар JavaScript

## Object чист?
**Object** (объект) дар JavaScript як сохтори додаҳо мебошад, ки аз маҷмӯи ҷуфтҳои **калид-арзиш** иборат аст. Объектҳо барои нигоҳдорӣ ва коркарди маълумот бо тарзи структуравӣ истифода мешаванд.

### Эҷоди Object
Дар JavaScript объектҳоро бо ду роҳ эҷод кардан мумкин аст:

1. **Истифодаи literal object:**
```javascript
const person = {
    name: "Ali",
    age: 25,
    city: "Dushanbe"
};
```

2. **Истифодаи constructor:**
```javascript
const person = new Object();
person.name = "Ali";
person.age = 25;
person.city = "Dushanbe";
```

## Methods of Object
Методҳо функсияҳое мебошанд, ки ҳамчун хосиятҳои объект нигоҳ дошта мешаванд. Методи объект метавонад маълумоти объекти худро истифода барад ва тағйир диҳад.

### Эҷоди метод дар объект
```javascript
const person = {
    name: "Ali",
    age: 25,
    city: "Dushanbe",
    greet: function() {
        return `Салом, ман ${this.name} ҳастам!`;
    }
};

console.log(person.greet()); // Салом, ман Ali ҳастам!
```

### Методи `Object.keys()`
Методи `Object.keys(obj)` ҳамаи калидҳои объектро ҳамчун массив бармегардонад.
```javascript
const keys = Object.keys(person);
console.log(keys); // ["name", "age", "city", "greet"]
```

### Методи `Object.values()`
Методи `Object.values(obj)` ҳамаи арзишҳои объектро ҳамчун массив бармегардонад.
```javascript
const values = Object.values(person);
console.log(values); // ["Ali", 25, "Dushanbe", ƒ]
```

### Методи `Object.entries()`
Методи `Object.entries(obj)` массиви ҷуфтҳои калид-арзишро бармегардонад.
```javascript
const entries = Object.entries(person);
console.log(entries);
// [["name", "Ali"], ["age", 25], ["city", "Dushanbe"], ["greet", ƒ]]
```

### Методи `Object.assign()`
Методи `Object.assign(target, source)` як объектро бо хосиятҳои объекти дигар нусха мекунад.
```javascript
const obj1 = { a: 1, b: 2 };
const obj2 = { c: 3, d: 4 };
const merged = Object.assign({}, obj1, obj2);
console.log(merged); // { a: 1, b: 2, c: 3, d: 4 }
```

### Методи `Object.freeze()`
Методи `Object.freeze(obj)` объектро ях мекунад, ки дигар тағйир додан мумкин нест.
```javascript
const frozenObj = Object.freeze({ x: 10, y: 20 });
frozenObj.x = 100; // Кор намекунад
console.log(frozenObj.x); // 10
```

### Методи `Object.seal()`
Методи `Object.seal(obj)` тағйир додани арзишҳоро иҷозат медиҳад, аммо хосиятҳои нав илова ё ҳазф карда намешаванд.
```javascript
const sealedObj = Object.seal({ name: "Ali", age: 25 });
sealedObj.age = 30; // Кор мекунад
sealedObj.city = "Dushanbe"; // Илова намешавад
console.log(sealedObj); // { name: "Ali", age: 30 }
```

## `this`, `bind`, `apply`, `call` дар JavaScript

### `this`
`this` ишора ба объекте мекунад, ки функсия дар он иҷро мешавад.
```javascript
const user = {
    name: "Ali",
    greet: function() {
        console.log(`Салом, ман ${this.name} ҳастам!`);
    }
};
user.greet(); // Салом, ман Ali ҳастам!
```

### `bind()`
Методи `bind()` функсияро бо объекти муайян пайваст мекунад ва объектро ҳамчун `this` таъин мекунад.
```javascript
const person1 = {
    name: "Karim"
};

const greet = user.greet.bind(person1);
greet(); // Салом, ман Karim ҳастам!
```

### `call()`
Методи `call()` функсияро бо `this`-и муайян иҷро мекунад ва аргументҳоро мустақим қабул мекунад.
```javascript
user.greet.call(person1); // Салом, ман Karim ҳастам!
```

### `apply()`
Методи `apply()` низ монанди `call()` кор мекунад, вале аргументҳоро ҳамчун массив қабул мекунад.
```javascript
user.greet.apply(person1); // Салом, ман Karim ҳастам!
```

## Хулоса
- **Object** дар JavaScript маҷмӯи ҷуфтҳои "калид-арзиш" мебошад.
- Методҳо ба объектҳо имконият медиҳанд, ки маълумоти худро коркард кунанд.
- Методҳои муфид ба монанди `Object.keys()`, `Object.values()`, `Object.entries()`, `Object.assign()`, `Object.freeze()` ва `Object.seal()` барои коркарди объектҳо истифода мешаванд.
- `this` ба объекте, ки метод дар он иҷро мешавад, ишора мекунад.
- `bind()`, `call()`, ва `apply()` барои идоракунии `this` истифода мешаванд.

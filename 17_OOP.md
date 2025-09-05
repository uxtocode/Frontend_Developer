# 🟨 Object-Oriented Programming (OOP) in JavaScript – Complete Guide

---

## 1. What is OOP?

* **Definition:** OOP is a programming paradigm based on **objects** that contain **data (properties)** and **behavior (methods)**.
* JavaScript is **prototype-based**, not class-based like Java, but ES6 introduced `class` syntax.
* Benefits of OOP:

  * Code **reusability**
  * **Encapsulation** (hide data)
  * **Modularity**
  * Easier **maintenance**

---

## 2. Objects in JS

### 2.1 Object Literal

```js
const user = {
  name: "Max",
  age: 25,
  greet: function() {
    console.log(`Hello, I am ${this.name}`);
  }
};

user.greet(); // Hello, I am Max
```

### 2.2 Dynamic Property Access

```js
console.log(user.name);     // dot notation
console.log(user["age"]);   // bracket notation
```

---

## 3. Constructor Functions

* Before ES6, constructors were used to create multiple objects:

```js
function Person(name, age) {
  this.name = name;
  this.age = age;
  this.greet = function() {
    console.log(`Hi, I am ${this.name}`);
  };
}

const p1 = new Person("Max", 25);
p1.greet(); // Hi, I am Max
```

---

## 4. Prototypes

* JavaScript objects have a **prototype chain**.
* Methods defined in a prototype are **shared** among all instances → memory-efficient.

```js
function Person(name) {
  this.name = name;
}

Person.prototype.greet = function() {
  console.log(`Hi, I am ${this.name}`);
};

const p1 = new Person("Max");
const p2 = new Person("Alice");
p1.greet(); // Hi, I am Max
p2.greet(); // Hi, I am Alice
```

---

## 5. ES6 Classes

* Modern way to implement OOP in JS.
* Syntactic sugar over prototypes.

```js
class Person {
  constructor(name, age) {
    this.name = name;
    this.age = age;
  }

  greet() {
    console.log(`Hi, I am ${this.name}`);
  }

  static species() {
    console.log("Humans");
  }
}

const p1 = new Person("Max", 25);
p1.greet(); // Hi, I am Max
Person.species(); // Humans
```

### Notes:

* `constructor()` → initializes objects.
* `static` → belongs to class, not instance.
* Methods in class → automatically added to **prototype**.

---

## 6. Inheritance

### 6.1 Using Classes

```js
class Employee extends Person {
  constructor(name, age, role) {
    super(name, age); // call parent constructor
    this.role = role;
  }

  work() {
    console.log(`${this.name} is working as ${this.role}`);
  }
}

const emp = new Employee("Max", 25, "Developer");
emp.greet(); // Hi, I am Max
emp.work();  // Max is working as Developer
```

---

## 7. Encapsulation

* Hide internal data → only accessible via **methods (getters/setters)**.

```js
class BankAccount {
  #balance = 0; // private field

  deposit(amount) {
    this.#balance += amount;
  }

  getBalance() {
    return this.#balance;
  }
}

const account = new BankAccount();
account.deposit(500);
console.log(account.getBalance()); // 500
// console.log(account.#balance); // Error: private
```

---

## 8. Polymorphism

* Same method, different behaviors in child classes.

```js
class Animal {
  speak() { console.log("Some sound"); }
}

class Dog extends Animal {
  speak() { console.log("Woof!"); }
}

class Cat extends Animal {
  speak() { console.log("Meow!"); }
}

const dog = new Dog();
const cat = new Cat();
dog.speak(); // Woof!
cat.speak(); // Meow!
```

---

## 9. Abstraction

* Hide complex logic behind simple interfaces.

```js
class API {
  fetchData(endpoint) {
    // internal complex logic hidden
    return fetch(endpoint).then(res => res.json());
  }
}

const api = new API();
api.fetchData("/api/projects").then(data => console.log(data));
```

---

## 10. Object Methods & Built-in Features

* **Object.keys(obj)** → returns array of keys
* **Object.values(obj)** → returns array of values
* **Object.entries(obj)** → returns array of `[key, value]` pairs
* **Object.assign(target, source)** → copy properties
* **Spread syntax** → `{ ...obj }` → clone objects

---

## 11. Real-World Example (ClientPanel SaaS)

```js
class Client {
  constructor(name, email) {
    this.name = name;
    this.email = email;
    this.projects = [];
  }

  addProject(project) {
    this.projects.push(project);
  }

  listProjects() {
    return this.projects.map(p => p.name).join(", ");
  }
}

class Project {
  constructor(name, status) {
    this.name = name;
    this.status = status;
  }
}

const client1 = new Client("John Doe", "john@example.com");
const proj1 = new Project("Website", "In Progress");
const proj2 = new Project("SEO Campaign", "Completed");

client1.addProject(proj1);
client1.addProject(proj2);

console.log(client1.listProjects()); // Website, SEO Campaign
```

👉 Encapsulates **clients & projects**, making data easy to manage.

---

## 12. Key Takeaways

* **Objects** are the core of JS OOP.
* **Classes & prototypes** allow reusable and memory-efficient code.
* **Encapsulation, Inheritance, Polymorphism, Abstraction** → OOP principles.
* Essential for **structuring complex apps**, like dashboards, user management, or multi-component SaaS platforms.
* Modern JS uses **ES6 classes + private fields + async methods** for maintainable code.

---

✅ **Summary**
OOP in JS = clean, modular, reusable code.

* Objects store **state + behavior**.
* Classes simplify **inheritance & prototypes**.
* Private fields and methods → **encapsulation**.
* Polymorphism & abstraction → flexible, maintainable architecture.

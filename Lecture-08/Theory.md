# INTERFACE

* **Interface** is used to define the **structure or blueprint of an object**.

* It specifies which properties and their data types an object or class should have.

* An interface does not create an actual object. It only defines a **structure** that the object or class must follow.

### Basic Interface

```typescript
interface PersonInterface {
    name: string,
    age: number,
    email: string,
    isActive?: boolean
}

const person: PersonInterface = {
    name: "Usman Hameed",
    age: 24,
    email: "usman@gmail.com",
    isActive: true
};

console.log(person);
```

* In the above example, `PersonInterface` defines the structure that a `Person` object should follow.

* The `isActive?` property is optional, so it can either be included or omitted.

### Interface with Class

* Interfaces are commonly used with **classes** to define a **structure** that the class must follow.

* A class can implement an interface using the **`implements`** keyword.

```typescript
// Interface
interface PersonInterface {
    name: string,
    age: number,
    email: string,
    isActive?: boolean
}

// Class
class Person implements PersonInterface
{
    name = "Usman Hameed";
    age = 24;
    email = "usman@gmail.com";
    isActive = true;
}

// Instance
const person = new Person();
console.log(person);
```

* When a class implements an interface, it must provide all the **required properties and methods** defined by that interface.

```typescript
interface PersonInterface {
    name: string,
    age: number,
    email: string
}

class Person implements PersonInterface
{
    name = "Usman Hameed";
    age = 24;
    // Error: email is missing
}
```

* This makes interfaces useful for creating a **standard structure** that multiple classes can follow.

### Type vs Interface

Both `type` and `interface` can be used to define the structure of objects.

```typescript
// Using type
type Person = {
    name: string,
    age: number,
    email: string
};
```

```typescript
// Using interface
interface Person {
    name: string,
    age: number,
    email: string
}
```

* Both approaches can be used to define the structure of an object.

* A `type` can also be implemented by a class.

```typescript
type PersonType = {
    name: string,
    age: number
};

class Person implements PersonType
{
    name = "Usman";
    age = 24;
}
```

### Why Prefer Interface for Classes?

* Although both `type` and `interface` can be implemented by classes, **interfaces are commonly preferred for defining class structure**.

* Interfaces are specifically designed around describing **object structures and contracts**, which makes their purpose clearer when working with classes.

* Interfaces can also be **extended** easily.

```typescript
interface Person {
    name: string,
    age: number
}

interface Employee extends Person {
    employeeId: number
}
```

* Interfaces also support **declaration merging**, where multiple declarations with the **same interface name** can be combined.

```typescript
interface User {
    name: string
}

interface User {
    age: number
}

// Both properties are now part of User
const user: User = {
    name: "Usman",
    age: 24
};
```

### When to Use `type`?

* `type` is more flexible when creating **Union Types**, **Intersection Types**, primitive aliases, tuples, and other type compositions.

```typescript
type Status = "pending" | "success" | "failed";

type ID = string | number;
```

### When to Use `interface`?

* Prefer **`interface`** when you are primarily defining the **structure of objects or contracts for classes**.

```typescript
interface User {
    name: string,
    email: string
}
```

* Prefer **`type`** when you need **unions, intersections, tuples, or other type combinations**.

```typescript
type Status = "pending" | "success" | "failed";
```

> **In simple words:** `interface` is commonly preferred for defining **object structures and class contracts**, while `type` is more flexible for creating **type aliases and combining types**.

> **Important:** This is a convention, not a strict rule. Both `type` and `interface` are powerful, and either can be used to describe object structures or be implemented by a class.
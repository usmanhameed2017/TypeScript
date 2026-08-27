# TYPE GUARDS & TYPE NARROWING

* **Type Narrowing** means reducing a variable from a broader type to a more specific type based on a condition.

* **Type Guard** is a condition or technique that TypeScript uses to determine the more specific type of a value.

* Type guards are especially useful when working with **Union Types**, because a variable can contain values of different types.

### `typeof` Type Guard

* The `typeof` operator can be used as a type guard to check the type of a value.

```typescript
function demo(value: string | number): string
{
    if(typeof value === "string") return `${value} is a string`;
    if(typeof value === "number") return `${value} is a number`;
    return `${value} is an unknown type`;
}

console.log(demo(24));
```

* When TypeScript finds `typeof value === "string"`, it **narrows** `value` from `string | number` to `string` inside that block.

* Because TypeScript now knows that `value` is a string, you can safely use **string-specific properties and methods**.

* Similarly, after checking `typeof value === "number"`, TypeScript narrows `value` to `number`, allowing you to use **number-specific properties and methods**.

### `instanceof` Type Guard

* The `instanceof` operator is another type guard. It is mainly used to check whether an object is an **instance of a particular class**.

```typescript
class Human
{
    public name = "Usman Hameed";
    public age = 24;
    public gender = "Male";
}

class Animal
{
    public name = "Lion";
    public age = 10;
}

function detect(blueprint: Human | Animal): string
{
    if(blueprint instanceof Human) return `${blueprint.name} is a Human`;
    if(blueprint instanceof Animal) return `${blueprint.name} is an Animal`;
    return `An unknown value`;
}

// Instance references
const human = new Human();
const animal = new Animal();

// Output
console.log(detect(human));
console.log(detect(animal));
```

* In the above example, `blueprint` can be either a `Human` or an `Animal`.

* When TypeScript finds `blueprint instanceof Human`, it narrows the type of `blueprint` to **`Human`** inside that block.

* Because TypeScript knows that `blueprint` is a `Human`, you get **autocomplete** for properties and methods available on the `Human` class, including the `gender` property.

* Similarly, `blueprint instanceof Animal` narrows the type to **`Animal`**.

### `in` Type Guard

* The `in` operator is another type guard. It is mainly used to check whether a property exists in an object.

```typescript
const user = {
    name: "Usman",
    age: 24,
    email: "usman@gmail.com"
};

// Logs
console.log("age" in user); // Output => true
console.log("gender" in user); // Output => false
```

> **Note:** Type narrowing does not change the actual value. It only tells TypeScript which type a value has within a specific part of the code.

### Common Type Guards

Some commonly used type guards are:

* **`typeof`** — Checks primitive types such as `string`, `number`, and `boolean`.
* **`instanceof`** — Checks whether an object is an instance of a specific class.
* **`in`** — Checks whether a property exists in an object.
* **Equality checks** — Checks values using conditions such as `===` or `!==`.

> **In simple words:** **Type Guard** is the check, while **Type Narrowing** is the result of that check. The guard helps TypeScript narrow a broad type into a more specific type.
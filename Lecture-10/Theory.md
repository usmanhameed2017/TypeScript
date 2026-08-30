# ARRAYS, TUPLES & ENUMS

### Arrays

* An **Array** is a collection of multiple values stored in a single variable.

* In TypeScript, we can specify the type of values that an array can contain.

### Array of Strings

* We can define an array using the **`type[]`** syntax.

```typescript
const users: string[] = ["Usman", "Bilal", "Ali", "Raheel"];

console.log(users);
```

* We can also use the **`Array<Type>`** syntax.

```typescript
const users: Array<string> = ["Usman", "Bilal", "Ali", "Raheel"];
console.log(users);
```

> **Note:** Both syntaxes are valid. `string[]` is usually preferred because it is shorter and easier to read.

### Array of Numbers

```typescript
const prices: number[] = [100, 200, 300];
console.log(prices);
```

* The generic syntax can also be used:

```typescript
const prices: Array<number> = [100, 200, 300];
console.log(prices);
```

### Nested Arrays

* An array can contain other arrays. This is called a **nested array**.

```typescript
const users: string[][] = [
    ["Usman", "Bilal", "Ali"],
    ["Raheel", "Talha", "Shahzaib"],
    ["Saad", "Danish", "Zain"]
];

console.log(users);
```

* The same structure can also be written using the generic syntax:

```typescript
const users: Array<Array<string>> = [
    ["Usman", "Bilal", "Ali"],
    ["Raheel", "Talha", "Shahzaib"],
    ["Saad", "Danish", "Zain"]
];

console.log(users);
```

> **Note:** Prefer `string[][]` for simple nested arrays because it is shorter and easier to understand.

### Array of Objects

* We can use a custom `type` to define the structure of objects and then create an array of those objects.

```typescript
type User = {
    name: string;
    age: number;
    email: string;
};

const users: User[] = [
    { name: "Usman", age: 24, email: "usman@gmail.com" },
    { name: "Ali", age: 27, email: "ali@gmail.com" },
    { name: "Bilal", age: 25, email: "bilal@gmail.com" }
];

console.log(users);
```

### Array with Partial Objects

* We can combine **`Partial<Type>`** with an array when objects may contain only some properties of the original type.

```typescript
type User = {
    name: string;
    age: number;
    email: string;
};

const users: Partial<User>[] = [
    { name: "Usman", age: 24, email: "usman@gmail.com" },
    { name: "Ali", email: "ali@gmail.com" },
    { name: "Bilal", age: 25 }
];

console.log(users);
```

* `Partial<User>` makes all properties of `User` optional.

* `Partial<User>[]` means an **array containing objects where all `User` properties are optional**.

---

### Tuples

* A **Tuple** is a special type of array where we define the **exact number, order, and type of elements**.

```typescript
type UserTuple = [string, number];
const user: UserTuple = ["Usman", 24];
console.log(user);
```

* In the above example:

  * The first element must be a `string`.
  * The second element must be a `number`.
  * The tuple must contain exactly these two elements.

```typescript
const user: UserTuple = ["Usman", 24]; // Correct
const user: UserTuple = [24, "Usman"]; // Error
```

### Named Tuples

* We can also give names to tuple elements to make their purpose clearer.

```typescript
type UserTuple = [name: string, age: number];
const user: UserTuple = ["Usman", 24];
console.log(user);
```

* The names `name` and `age` are mainly for **readability and editor suggestions**. They do not change how the tuple works.

### Array vs Tuple

| Array                                           | Tuple                                                   |
| ----------------------------------------------- | ------------------------------------------------------- |
| Stores multiple values of the same/general type | Stores values with specific types at specific positions |
| Length is generally flexible                    | Number of elements can be fixed                         |
| Order is usually not important for the type     | Order is important                                      |
| Example: `string[]`                             | Example: `[string, number]`                             |

```typescript
// Array
const users: string[] = ["Usman", "Ali", "Bilal"];
```

```typescript
// Tuple
const user: [string, number] = ["Usman", 24];
```

---

### Enums

* An **Enum** is a way to define a set of **named constant values**.

* Enums are useful when a variable can have a limited set of predefined values.

```typescript
enum Profiles
{
    PARENT = "User",
    BUSINESS = "BusinessProfile",
    USER = "UserProfile"
}
```

* We can then use the enum values instead of repeatedly writing the same strings.

```typescript
function sendNotification(profile: "User" | "BusinessProfile" | "UserProfile"): void
{
    if(profile === "User") return console.log("Send notification to parent user");
    if(profile === "BusinessProfile") return console.log("Send notification to business profile");
    if(profile === "UserProfile") return console.log("Send notification to user profile");
}

// Output
sendNotification(Profiles.PARENT);
```

* `Profiles.PARENT` provides the value `"User"`.

* Enums make related values easier to **organize, reuse, and understand**.

### Numeric Enums

* If you do not explicitly assign values to enum members, TypeScript uses **numeric values starting from `0`**.

```typescript
enum Status
{
    PENDING,
    SUCCESS,
    FAILED
}

console.log(Status.PENDING); // 0
console.log(Status.SUCCESS); // 1
console.log(Status.FAILED);  // 2
```

* The values are automatically incremented by `1`.

```typescript
enum Status
{
    PENDING = 5,
    SUCCESS,
    FAILED
}

console.log(Status.PENDING); // 5
console.log(Status.SUCCESS); // 6
console.log(Status.FAILED);  // 7
```

> **Note:** If you do not provide values, numeric enums start from `0` and automatically increment.

### String Enums

* You can explicitly assign string values to enum members.

```typescript
enum Profiles
{
    PARENT = "User",
    BUSINESS = "BusinessProfile",
    USER = "UserProfile"
}
```

* String enums are often easier to understand and safer to use because their values are meaningful instead of numeric indexes.

### `void` Function Note

* A function with a `void` return type does not return a meaningful value.

* You can still use `return` to **exit the function early**.

```typescript
function demo(value: boolean): void
{
    if(!value) return;
    console.log("Value is true");
}
```

* You can also write `return console.log(...)` because `console.log()` itself returns `void`.

```typescript
function demo(): void
{
    return console.log("Hello");
}
```

> **Note:** A `void` function can use `return`, but it cannot return a meaningful value such as `return 10` or `return "Hello"`.
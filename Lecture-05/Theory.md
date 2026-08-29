# CUSTOM TYPES

* You can create or define your own custom types using the **`type`** keyword.

* Custom types are especially useful in **TypeScript** for defining reusable types for variables, objects, arrays, function parameters, and more.

### Basic Custom Types

* You can create a custom type that acts as an alias for an existing data type.

```typescript
// For string
type Varchar = string;
const name: Varchar = "Usman";

// For number
type Integer = number;
const age: Integer = 24;

// Output
console.log(name);
console.log(age);
```

* In the above example, `Varchar` is an alias for `string`, and `Integer` is an alias for `number`.

> **Note:** Custom type names are usually written in **PascalCase**, such as `User`, `Product`, and `Status`.

### Custom Types for Objects

* Custom types are very useful for defining the **structure or blueprint of an object**.

```typescript
type User = {
    name: string,
    age: number,
    email: string,
    isActive?: boolean // "?" makes the property optional
};

const user: User = {
    name: "Usman",
    age: 24,
    email: "usman@gmail.com",
    isActive: true
};

console.log(user);
```

* The `User` type defines which properties an object should have and what data type each property should contain.

* The `?` after `isActive` makes that property **optional**. This means the property can be omitted when creating a `User` object.

```typescript
const user: User = {
    name: "Usman",
    age: 24,
    email: "usman@gmail.com"
};
```

### Custom Types with Union

* You can also create your own custom type using a **Union Type**.

```typescript
type Status = "pending" | "success" | "failed";
const status: Status = "success";

console.log(status);
```

* Now, the `status` variable can only contain one of these three values:

```text
"pending"
"success"
"failed"
```

* This is useful when you want to restrict a variable or function parameter to a specific set of allowed values.

> Note: Commas `,` and semi-colons `;` are optional when defining a custom type for an object.
```typescript
// Correct - With commas
type User = {
    name: string,
    age: number,
    email: string
};

// Correct - With semi-colons
type User = {
    name: string;
    age: number;
    email: string;
};

// Correct - Without commas and semi-colons
type User = {
    name: string
    age: number
    email: string
};
```
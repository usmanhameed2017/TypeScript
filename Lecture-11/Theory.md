### FUNCTIONS

* Functions in TypeScript can have **typed parameters** and a **typed return value**.

* TypeScript can automatically **infer the return type** of a function, so you do not always need to explicitly specify it.

* If a function does not return a value, TypeScript automatically infers its return type as **`void`**.

```typescript
function greet(name: string)
{
    console.log(`Hello ${name}`);
}

// Output
greet("Usman");
```

* In the above example, the function does not return any value, so TypeScript infers its return type as `void`.

* If a function returns a value, TypeScript infers the return type based on the returned value.

```typescript
function greet(name: string)
{
    return `Hello ${name}`;
}

// Output
console.log(greet("Usman"));
```

* In the above example, TypeScript infers the return type as `string`.

> **Note:** Function parameters can also be explicitly typed. In the above example, `name: string` means the function only accepts a string as an argument.

### Return Type Annotation

* You can explicitly specify the return type of a function after its parameter list.

```typescript
function updateStatus(status: "pending" | "success" | "failed"): string
{
    return `Status is ${status}`;
}

// Output
console.log(updateStatus("success"));
```

* The `status` parameter only accepts `"pending"`, `"success"`, or `"failed"`.

* The `: string` after the parameter list specifies that the function must return a `string`.

### Default Parameter Value

* You can provide a **default value** for a function parameter.

```typescript
function updateStatus(status: "pending" | "success" | "failed" = "pending"): string
{
    return `Status is ${status}`;
}

// Output
console.log(updateStatus());
```

* If no argument is provided, the parameter automatically gets the value `"pending"`.

* You can still provide another allowed value.

```typescript
console.log(updateStatus("success"));
```

### Optional Parameter

* You can make a function parameter **optional** by using the `?` symbol.

```typescript
function updateStatus(status?: "pending" | "success" | "failed"): string
{
    if(status) return `Status is ${status}`;
    return `Status not provided`;
}

// Output
console.log(updateStatus());
```

* An optional parameter can be omitted when calling the function.

* Unlike a default parameter, an optional parameter does **not automatically receive a default value**.

> **Default parameter:** If no value is provided, use a specific value.
> **Optional parameter:** The value may or may not be provided.

### Function with Custom Types

* You can use custom types and utility types such as **`Pick`** with function parameters and return types.

```typescript
type User = {
    name: string;
    age: number;
    email: string;
    password: string;
};

// User details function
function getUserDetails(details: Pick<User, "name" | "age" | "email">): Pick<User, "name" | "age" | "email">
{
    const { name, age, email } = details;
    return { name, age, email };
}

// Output
console.log(getUserDetails({ name: "Usman", age: 24, email: "usman@gmail.com" }));
```

* `Pick<User, "name" | "age" | "email">` creates a type containing only the `name`, `age`, and `email` properties.

* In this example, the function:

  * Accepts an object containing `name`, `age`, and `email`.
  * Returns an object containing `name`, `age`, and `email`.

### `void` Function

* A function with a **`void`** return type does not return a meaningful value.

```typescript
function demo(value: boolean): void
{
    if(!value) return; // Exit function
    console.log("Value is true");
}
```

* You can use `return` without a value to **exit the function early**.

* You can also write `return console.log(...)` because `console.log()` returns `void`.

```typescript
function demo(): void
{
    return console.log("Hello");
}
```

> **Note:** A `void` function can use `return` to exit early, but it cannot return a meaningful value such as `return 10` or `return "Hello"`.

### Function Return Type Summary

* **No return value** → TypeScript infers `void`.

* **Returns a value** → TypeScript infers the **return type** based on the **returned value**.

* **Explicit return type** → We can manually specify the return type.

```typescript
// Inferred as void
function logMessage()
{
    console.log("Hello");
}

// Inferred as number
function add(a: number, b: number)
{
    return a + b;
}

// Explicit return type
function multiply(a: number, b: number): number
{
    return a * b;
}
```
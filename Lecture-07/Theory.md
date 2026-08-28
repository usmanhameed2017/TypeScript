# TYPE ASSERTION, ANY, UNKNOWN & NEVER

### Type Assertion

* **Type Assertion** is used when you tell TypeScript that you know the type of a value better than TypeScript does.

* It does **not change the actual value or type at runtime**. It only tells the TypeScript compiler how you want it to treat that value.

* Type assertion can be written using the **`as`** keyword.

```typescript
let data: unknown;
data = "Usman Hameed";

// Tell TypeScript to treat it as a `string`
let name = data as string;
console.log(name.toUpperCase());

console.log((data as string).toUpperCase());
```

> Note: You can also use round brackets `()` to access built-in methods directly, instead of storing it to a variable.

```typescript
let data: unknown;
data = "Usman Hameed";

console.log((data as string).toUpperCase());
```

* In the above example, `data` is originally `unknown`, but we tell TypeScript to treat it as a `string`.

* You can also use the angle-bracket syntax, but the `as` syntax is generally preferred, especially in projects that use JSX.

```typescript
let data: unknown = "Usman";
let name = <string>data;
```

> **Note:** Type assertion does not perform any runtime type checking. If your assertion is incorrect, TypeScript will not automatically convert or validate the value.

### `any`

* **`any`** is a type that tells TypeScript to **disable type checking** for a particular value.

* A variable with the `any` type can contain a value of any data type and can later be assigned a value of a different type.

```typescript
let value: any = "Usman";
value = 24;
value = true;
value = { name: "Usman" };
```

* You can also perform almost any operation on an `any` value without TypeScript reporting an error.

```typescript
let value: any = "Usman";
console.log(value.toUpperCase());
value = 24;

console.log(value.toUpperCase()); // No TypeScript error
```

* However, this can cause runtime errors because TypeScript is no longer protecting you from incorrect operations.

> **Note:** Avoid using `any` unless you have a specific reason to use it. It removes many of the benefits of TypeScript's type system.

### `unknown`

* **`unknown`** is similar to `any` because it can store a value of any type.

```typescript
let value: unknown = "Usman";
value = 24;
value = true;
```

* The main difference is that you **cannot directly perform operations** on an `unknown` value until you check or narrow its type.

```typescript
let value: unknown = "Usman";
console.log(value.toUpperCase()); // Error
```

* We first need to use a **type guard** to narrow the type.

```typescript
let value: unknown = "Usman";
if(typeof value === "string")
{
    console.log(value.toUpperCase());
}
```

* `unknown` is safer than `any` because it forces you to **check the type before using the value**.

> **In simple words:** `any` says **"Trust me, I know what I am doing."** `unknown` says **"I don't know the type yet, so check it first."**

### `never`

* **`never`** represents a value that **never occurs**.

* It is commonly used for functions that **never successfully return** because they always throw an error or continue running forever.

```typescript
function throwError(message: string): never
{
    throw new Error(message);
}
```

* The function above has a return type of `never` because it always throws an error and never returns a value.

* Another example is an infinite loop:

```typescript
function infiniteLoop(): never
{
    while(true)
    {
        console.log("Running...");
    }
}
```

* `never` can also be useful when TypeScript determines that a particular case is impossible.

```typescript
function checkStatus(status: "pending" | "success"): string
{
    if(status === "pending") return "Request is pending";
    if(status === "success") return "Request was successful";

    const impossible: never = status;
    return impossible;
}
```

> **Note:** `never` is different from `void`. A function returning `void` can finish without returning a value, while a function returning `never` **never reaches the point where it returns**.

### Quick Difference

| Type               | Meaning                                                |
| ------------------ | ------------------------------------------------------ |
| **Type Assertion** | Tell TypeScript to treat a value as a specific type    |
| **`any`**          | Allows anything and disables type checking             |
| **`unknown`**      | Allows any value but requires type checking before use |
| **`never`**        | Represents a value that can never occur                |
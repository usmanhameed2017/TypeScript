# UNION TYPE

* **Union Type** allows a variable to accept values of **multiple specified data types**.

```typescript
let value: string | number = "Usman";

value = "Ali"; // Correct
value = 2017;  // Correct
value = true;  // Error
```

* In the above example, `value` can contain either a **string** or a **number**, but it cannot contain a boolean value.

### Literal Union Type

* You can also create a custom type by allowing a variable to contain only **specific values**.

```typescript
let status: "pending" | "success" | "failed";
```

* Now, `status` can only contain `"pending"`, `"success"`, or `"failed"`.

```typescript
status = "pending"; // Correct
status = "success"; // Correct
status = "failed";  // Correct

status = "loading"; // Error
```

* You can also assign a default value while defining the variable.

```typescript
let status: "pending" | "success" | "failed" = "pending";
```

### Using Union Types in Functions

* Union types are especially useful for function parameters because they clearly define which values a function accepts.

```typescript
function updateStatus(status: "pending" | "success" | "failed") 
{
    console.log(`Status: ${status}`);
}

updateStatus("pending"); // Correct
updateStatus("success"); // Correct
updateStatus("failed");  // Correct

updateStatus("loading"); // Error
```

* This makes the function easier and safer to use because the developer gets **autocomplete** and TypeScript prevents unsupported values from being passed to the function.
# TYPE ANNOTATIONS & TYPE INFERENCE

* **Annotation** means explicitly specifying the data type of a variable.

```typescript
let age: number = 26;
let name: string = "Usman";
```

* **Inference** means TypeScript automatically detects the data type based on the value assigned to a variable.

```typescript
let age = 26; // TypeScript infers number
let name = "Usman"; // TypeScript infers string
```

* TypeScript uses the assigned value to **infer the type** of a variable and then expects the variable to follow that type.

```typescript
let age = 26;

age = 30;      // ✅ Same type
age = "26";    // ❌ Error: Type 'string' is not assignable to type 'number'
```

* Type inference is similar to JavaScript because JavaScript also determines the type of a value at runtime.

* However, in JavaScript, a variable can be reassigned to a value of a completely different type.

```javascript
let value = 10;

value = "Hello"; // ✅ Allowed in JavaScript
```

* In TypeScript, the inferred type normally prevents assigning a value of a different type.

```typescript
let value = 10;

value = 20;      // ✅ Allowed
value = "Hello"; // ❌ Error
```

### Annotation vs Inference

* **Annotation** — We explicitly tell TypeScript what type a variable should have.

```typescript
let age: number = 26;
```

* **Inference** — We let TypeScript determine the type automatically.

```typescript
let age = 26;
```

> **Note:** Type annotations are not always required. When TypeScript can safely infer the type, it is usually better to let TypeScript infer it instead of writing the type manually.
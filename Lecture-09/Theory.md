# OBJECTS & SPECIAL TYPES

* In TypeScript, an **object type** defines the structure of an object, including its properties and their data types.

* We can use a custom `type` to define the structure of an object and then use that type when creating objects.

### Object

* We can create a custom type to define the structure of an object.

```typescript
// Type
type User = {
    name: string;
    age: number;
    email: string;
    isActive?: boolean;
};

// Object
const user: User = {
    name: "Usman Hameed",
    age: 24,
    email: "usman@gmail.com",
    isActive: true
};

// Output
console.log(user);
```

* The `User` type acts as a **blueprint** for the object.

* The `isActive?` property is optional, so it can be included or omitted.

### Partial

* **`Partial<Type>`** makes **all properties optional**.

* It is useful when you want to create an object that contains only some properties of an existing type.

```typescript
// Type
type User = {
    name: string;
    age: number;
    email: string;
    isActive?: boolean;
};

// Partial
const user: Partial<User> = {
    name: "Usman",
    email: "usman@gmail.com"
};

// Empty object is also allowed
const anotherUser: Partial<User> = {};

// Output
console.log(user);
```

* In the above example, all properties of `User` become optional.

### Required

* **`Required<Type>`** makes **all properties required**, including properties that were originally optional.

```typescript
// Type
type User = {
    name: string;
    age: number;
    email?: string;
    isActive?: boolean;
};

// Required
const user: Required<User> = {
    name: "Usman Hameed",
    age: 24,
    email: "usman@gmail.com",
    isActive: true
};

// Output
console.log(user);
```

* Normally, `email` and `isActive` are optional, but `Required<User>` makes them mandatory.

### Pick

* **`Pick<Type, Keys>`** creates a new type containing **only the properties that you specify**.

```typescript
// Type
type User = {
    name: string;
    age: number;
    email?: string;
    isActive?: boolean;
};

// Pick
const user: Pick<User, "name" | "email"> = {
    name: "Usman Hameed",
    email: "usman@gmail.com"
};

// Output
console.log(user);
```

* In the above example, only `name` and `email` are picked from the `User` type.

> **Note:** `email` was originally optional, so it remains optional in the `Pick` type.

### Omit

* **`Omit<Type, Keys>`** creates a new type by **excluding the specified properties** from an existing type.

```typescript
// Type
type User = {
    name: string;
    age: number;
    email: string;
    password: string;
    ipAddress: string;
    isActive?: boolean;
};

// Omit
const user: Omit<User, "password" | "ipAddress"> = {
    name: "Usman Hameed",
    age: 24,
    email: "usman@gmail.com",
    isActive: true
};

// Output
console.log(user);
```

* In the above example, `password` and `ipAddress` are excluded from the new type.

> **Note:** `Omit` does not actually delete properties from an existing object. It only creates a **new TypeScript type** without the specified properties.

* You can also utilize a combination of `Pick` & `Partial`.
```typescript
// Type
type User = {
    name: string;
    nickname?: string;
    age: number;
    email: string;
    password: string;
    ipAddress: string;
    isActive?: boolean;
};

// Specific fields (name, age & email)
type SelectedFields = Pick<User, "name" | "age" | "email">;

// Make them optional
type PartialFields = Partial<SelectedFields>;

// User object
const user: PartialFields = {
    name: "Usman",
    age: 24
};

// Output
console.log(user);
```

### Quick Summary

| Special Type           | Purpose                             |
| ---------------------- | ----------------------------------- |
| **`Partial<Type>`**    | Makes all properties optional       |
| **`Required<Type>`**   | Makes all properties required       |
| **`Pick<Type, Keys>`** | Keeps only the specified properties |
| **`Omit<Type, Keys>`** | Excludes the specified properties   |
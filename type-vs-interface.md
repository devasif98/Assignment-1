# Type Aliases vs Interface in TypeScript

## Introduction
When learning TypeScript, many developers wonder whether to use `type` or `interface`. Both help us define the shape of our data. However, they have some important differences that make each useful in different situations.

## Core Differences

### 1. Primitives, Unions, and Tuples
A `type` alias is very flexible. We can use it to create union types, tuples, or shortcuts for primitives. An `interface` only works with objects, so it cannot create a direct union or rename a primitive.

```typescript
type ID = string | number;
type Role = "admin" | "user";
```

### 2. Extending Types
Both can be extended, but the syntax is different. An `interface` uses the `extends` keyword, just like normal object-oriented programming. A `type` alias uses the intersection operator (`&`) to join types.

```typescript
interface Person {
  name: string;
}
interface Employee extends Person {
  salary: number;
}

type Car = { brand: string };
type SportsCar = Car & { topSpeed: number };
```

### 3. Declaration Merging
Interfaces have a handy feature called declaration merging. If you create two interfaces with the same name, TypeScript merges them into one. Type aliases do not allow this and will show an error if declared twice.

```typescript
interface User {
  name: string;
}
interface User {
  age: number;
}
// User now has both name and age
```

## When to Choose Which?
Use `interface` when defining object shapes, class structures, or props. Use `type` when you need union types, tuples, or primitive aliases.

## Conclusion
Both `type` and `interface` are great in TypeScript. Using `interface` for objects and `type` for unions keeps our code clean and easy to understand.

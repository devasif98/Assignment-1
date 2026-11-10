# What is Type Narrowing in TypeScript?

## Introduction

Sometimes in TypeScript, a variable can have more than one type, like `string | number`. When this happens, TypeScript does not let us use methods that only belong to one type. Type narrowing is the way we check the type at runtime so TypeScript knows the exact type inside our code block.

## Practical Narrowing Examples

### 1. The `typeof` Operator

The `typeof` operator is the simplest way to check primitive types like strings or numbers. Inside an `if` condition, TypeScript narrows the type automatically.

```typescript
function printValue(value: string | number) {
  if (typeof value === "string") {
    return value.toUpperCase();
  }
  return value.toFixed(2);
}
```

### 2. The `instanceof` Operator

We use `instanceof` to check if an object comes from a specific class or constructor. This is very helpful when checking built-in objects like `Date`.

```typescript
function printDate(value: Date | string) {
  if (value instanceof Date) {
    return value.toISOString();
  }
  return value.trim();
}
```

### 3. The `in` Operator

The `in` operator helps us check if a specific property exists inside an object. It allows us to tell two different object types apart.

```typescript
type Dog = { bark: () => void };
type Cat = { meow: () => void };

function makeNoise(pet: Dog | Cat) {
  if ("bark" in pet) {
    pet.bark();
  } else {
    pet.meow();
  }
}
```

## Conclusion

Type narrowing is a core part of writing safe TypeScript code. By using simple checks like `typeof`, `instanceof`, and `in`, we can avoid runtime bugs and write reliable code with confidence.

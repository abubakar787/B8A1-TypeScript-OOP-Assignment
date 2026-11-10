# What is Type Narrowing in TypeScript?

## Introduction

TypeScript is a strongly typed programming language that helps developers write safer code. Sometimes, a variable can contain different types of values. Type Narrowing is a technique that helps TypeScript identify the specific type of a variable before performing an operation.

## Detailed Explanation

There are several ways to perform Type Narrowing in TypeScript.

**1. Using typeof**

The `typeof` operator checks primitive data types such as string, number, and boolean.

```ts
function processValue(value: string | number): string {
  if (typeof value === "string") {
    return value.toUpperCase();
  }
  return value.toString();
}
```

Here, TypeScript understands whether the value is a string or a number.

**2. Using instanceof**

The `instanceof` operator checks whether an object belongs to a particular class.

```ts
function getMessage(value: Error | Date): string {
  if (value instanceof Error) {
    return value.message;
  }
  return value.toISOString();
}
```

**3. Using the in Operator**

The `in` operator checks whether a specific property exists in an object.

```ts
type Admin = { name: string; permissions: string[] };
type User = { name: string; email: string };

function getUserInfo(person: Admin | User): string {
  if ("permissions" in person) {
    return "Admin";
  }
  return "Regular User";
}
```

These techniques help developers handle different types safely and avoid unexpected errors.

## Conclusion

Type Narrowing is an important feature of TypeScript. Using `typeof`, `instanceof`, and the `in` operator makes code safer, clearer, and easier to maintain.
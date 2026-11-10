# Type Narrowing in TypeScript

## Introduction

TypeScript allows a variable to have more than one possible type. This is useful, but we must check the actual value before using operations that are only valid for one type. Type narrowing is the process of reducing a broad type to a more specific type through conditions and checks.

## Detailed Explanation

A common technique is the `typeof` operator. It is useful for primitive values such as strings, numbers, and booleans.

```ts
function formatValue(value: string | number): string {
  if (typeof value === "string") {
    return value.trim().toLowerCase();
  }

  return (value * 10).toString();
}
```

Inside the first branch, TypeScript knows that `value` is a string. In the second branch, it knows that the value is a number.

The `instanceof` operator checks whether an object was created by a particular class or constructor. For example:

```ts
function showError(error: Error | Date): string {
  if (error instanceof Error) {
    return error.message;
  }

  return error.toISOString();
}
```

The `in` operator checks whether a property exists on an object. It is helpful when working with object unions.

```ts
type Admin = { name: string; permissions: string[] };
type Customer = { name: string; purchaseCount: number };

function describe(user: Admin | Customer): string {
  if ("permissions" in user) {
    return `Admin: ${user.permissions.length} permissions`;
  }

  return `Customer: ${user.purchaseCount} purchases`;
}
```

These checks help TypeScript understand which properties and methods are safe to use. They also reduce runtime mistakes because the code handles each possible case deliberately.

## Conclusion

Type narrowing makes union types practical and safer. Using `typeof`, `instanceof`, and `in` helps developers write readable code while allowing the compiler to verify that each operation matches the value's actual type.

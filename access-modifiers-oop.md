# Access Modifiers in TypeScript OOP

## Introduction

Object-oriented programming organizes code around classes and objects. In TypeScript, access modifiers control where class properties and methods can be accessed. The main modifiers are `public`, `private`, and `protected`. TypeScript also supports `readonly` to prevent reassignment after initialization.

## Detailed Explanation

A `public` member can be accessed from inside the class, from subclasses, and from outside the class. It is the default access level when no modifier is written.

A `private` member can only be accessed inside the class where it is declared. This is useful for implementation details that should not be changed directly by outside code.

A `protected` member is available inside its class and its subclasses, but not through an object from outside the class. For example:

```ts
class Employee {
  protected name: string;
  private salary: number;

  constructor(name: string, salary: number) {
    this.name = name;
    this.salary = salary;
  }

  public getDetails(): string {
    return `${this.name}: ${this.salary}`;
  }
}

class Manager extends Employee {
  constructor(name: string, salary: number) {
    super(name, salary);
  }

  public getName(): string {
    return this.name;
  }
}
```

Here, `Manager` can use `name` because it is protected. It cannot directly access `salary` because that property is private to `Employee`.

The `readonly` modifier allows a property to be assigned during declaration or inside the constructor, but prevents later reassignment.

```ts
class Product {
  readonly productId: number;

  constructor(productId: number) {
    this.productId = productId;
  }
}
```

These modifiers help define a clear boundary between the public features of a class and its internal data.

## Conclusion

Access modifiers improve encapsulation and maintainability. Use `public` for the intended API, `private` for class-only details, `protected` for subclass access, and `readonly` for values that should not be reassigned.

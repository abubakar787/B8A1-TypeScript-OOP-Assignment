 # Access Modifiers in TypeScript OOP

## Introduction

Access Modifiers are an important part of Object-Oriented Programming (OOP) in TypeScript. They control how class properties and methods can be accessed. TypeScript provides three main access modifiers: public, private, and protected. It also supports readonly to prevent changing a property after initialization.

## Detailed Explanation

**1. Public**

A public property can be accessed from anywhere, including outside the class. It is the default access modifier in TypeScript.

**2. Private**

A private property can only be accessed inside its own class. It helps protect important data from direct access outside the class.

**3. Protected**

A protected property can be accessed inside its own class and its child classes. It cannot be accessed directly from outside.

**4. Readonly**

The readonly keyword prevents a property from being reassigned after it has been initialized. It can be assigned when declared or inside the constructor.

Here is a practical example:

```ts
class Employee {
  public name: string;
  private salary: number;
  protected department: string;
  readonly employeeId: number;

  constructor(
    name: string,
    salary: number,
    department: string,
    employeeId: number
  ) {
    this.name = name;
    this.salary = salary;
    this.department = department;
    this.employeeId = employeeId;
  }

  getSalary(): number {
    return this.salary;
  }
}

class Manager extends Employee {
  getDepartment(): string {
    return this.department;
  }
}
```

In this example, the Manager class can access the protected department property through inheritance, but it cannot directly access the private salary property.

## Conclusion

Access Modifiers help developers organize classes and protect data. Using public, private, protected, and readonly properly makes TypeScript applications easier to manage and maintain.
# Demystifying Type Narrowing in TypeScript

When working with union types like string or number, TypeScript requires you to refine the variable type before calling type-specific methods. This essential process is known as type narrowing.

Type narrowing allows the compiler to inspect runtime conditions and automatically narrow down a broad union type into a specific type within conditional code blocks.

The three primary checks used in day-to-day development are:

1. typeof: Used to verify primitive types like string, number, or boolean.
2. instanceof: Checks whether an object is created from a specific class constructor.
3. in operator: Checks whether a specific property exists inside an object.

Here is how type narrowing works in practice:

```typescript
// 1. Using typeof for primitives
function processInput(val: string | number): string {
  if (typeof val === "string") {
    return val.trim().toLowerCase();
  }
  return val.toFixed(2);
}

// 2. Using instanceof for class instances
class Dog {
  bark() {
    return "Woof!";
  }
}
class Cat {
  meow() {
    return "Meow!";
  }
}

function getSound(animal: Dog | Cat): string {
  if (animal instanceof Dog) {
    return animal.bark();
  }
  return animal.meow();
}

// 3. Using the in operator for object properties
type Admin = { name: string; permissions: string[] };
type Guest = { name: string };

function checkAccess(user: Admin | Guest): boolean {
  if ("permissions" in user) {
    return user.permissions.length > 0;
  }
  return false;
}
```

## Conclusion

Type narrowing lets TypeScript follow the same checks we already write at runtime. Use typeof for primitives, instanceof for class instances, and the in operator for object shapes. With these guards, union types stay flexible while every branch remains fully type-safe, which catches mistakes during compilation instead of in production.

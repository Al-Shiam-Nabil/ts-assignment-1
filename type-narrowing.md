# Demystifying Type Narrowing in TypeScript

When building applications with TypeScript, you often run into scenarios where a variable can accept multiple data types using union types like string | number. While union types are super helpful, TypeScript won't let you run string-specific methods on a variable unless it's completely sure it's a string. This is where Type Narrowing comes into play.

Type narrowing is simply the mechanism TypeScript uses to refine a broad type into a specific type based on runtime checks. The compiler analyzes your control flow, so when you write conditional checks, it automatically narrows down the type inside that specific code block.

The three most common guard checks we use every day are:

1. **typeof**: Perfect for checking primitive types like strings, numbers, and booleans.
2. **instanceof**: Used to check if an object is an instance of a specific class.
3. **in operator**: Checks whether a specific property key exists inside an object structure.

Here is how these guard checks look in practice:

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

// 3. Using the 'in' operator for object properties
type Admin = { name: string; permissions: string[] };
type Guest = { name: string };

function checkAccess(user: Admin | Guest): boolean {
  if ("permissions" in user) {
    return user.permissions.length > 0;
  }
  return false;
}
```

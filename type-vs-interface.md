# Type Aliases vs Interface in TypeScript: Which One Should You Pick?

When I first started learning TypeScript, one of the biggest questions on my mind was whether to use type or interface. At first glance, both seem to do almost the exact same job—defining the shape of an object. But once you work on real projects, the subtle differences become clear.

The main difference comes down to declaration merging and flexibility. Interfaces can be declared multiple times with the same name, and TypeScript will automatically merge them together into a single structure. On the other hand, type aliases cannot be redeclared once created. Also, interfaces are mainly meant for defining object structures and OOP patterns with the extends keyword, while type aliases are far more flexible because they can handle primitive values, unions, and tuples directly using intersection (&) operators.

Here is a quick look at how they look in practice:

```typescript
// Interface with declaration merging and extension
interface User {
  id: number;
  name: string;
}

interface AdminUser extends User {
  permissions: string[];
}

// Type alias handling unions and intersections
type ResponseStatus = "success" | "error" | "loading";
type UserWithStatus = User & { status: ResponseStatus };
```

# Type Aliases vs Interfaces in TypeScript

When building applications in TypeScript, one of the first design decisions you make is choosing between type aliases and interfaces. Both of these features allow us to define custom object shapes, but they have key differences in flexibility and OOP features.

The main difference lies in declaration merging and syntax. An interface can be declared multiple times with the exact same name, and TypeScript will automatically merge all those properties into one single structure. A type alias cannot be redeclared once created. Moreover, type aliases are great for defining union types, primitive aliases, and complex tuples, whereas interfaces focus heavily on object structures and class inheritance using the extends keyword.

Here is a practical look at how both look in code:

```typescript
// Interface declaration merging
interface User {
  id: number;
}
interface User {
  name: string;
}

// Interface extension
interface AdminUser extends User {
  permissions: string[];
}

// Type alias handling unions
type ResponseStatus = "success" | "error" | "loading";
```

## Conclusion

Choose an interface when describing object shapes, building class contracts, or when a public library type may need declaration merging. Choose a type alias for unions, tuples, primitive aliases, or combining types with intersections. In practice, pick one default for objects, stay consistent across the project, and reach for the other only when its specific feature is needed.

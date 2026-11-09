# Type Alias vs Interface in TypeScript

## Introduction

In TypeScript, we often need to describe what our data looks like. For this, we have two tools: `type` and `interface`. At first, both look almost the same, so we can easily get confused. In this blog, we will see how they are different and when to use each one.

## Both Can Describe an Object

```ts
interface User {
  name: string;
  age: number;
}

type Product = {
  title: string;
  price: number;
};
```

Both tell TypeScript which properties an object must have.

## Difference 1: type Can Do More

An interface can only describe an object. A type can also describe other things, like a union or a tuple. We cannot write these with an interface.

```ts
type Status = "active" | "inactive";
type Point = [number, number];
```

## Difference 2: How We Extend Them

When we want to add more properties, we use `extends` with an interface and `&` with a type.

```ts
interface Admin extends User {
  role: string;
}

type SaleProduct = Product & {
  discount: number;
};
```

## Difference 3: Interfaces Can Merge

If we declare the same interface twice, TypeScript joins them into one. If we try the same thing with a type, we get an error.

```ts
interface Car { brand: string }
interface Car { year: number }
// now Car has both brand and year
```

## When Should We Use Which?

- We use an interface for objects, especially when other code may extend them later.
- We use a type for unions, tuples, or when we combine other types.

## Conclusion

Both describe the shape of our data. A simple rule is: interface for objects, type for everything else. Whichever we choose, we should stay consistent.
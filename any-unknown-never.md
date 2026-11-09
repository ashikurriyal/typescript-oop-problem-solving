# any, unknown and never in TypeScript's Type Hierarchy

## Introduction

TypeScript has three special types that are: `any`, `unknown` and `never`. We can think of these types as levels. `any` and `unknown` sit at the top because they accept every value. `never` sits at the bottom because it accepts no value at all.

## any: TypeScript Stops Checking

When we give a variable the `any` type, TypeScript stops checking it. We can do anything with it, even things that will crash.

```ts
let data: any = "hello";
data.toFixed(2); // no error here, but it crashes when we run it
```

## unknown: Check First, Then Use

`unknown` also accepts any value. The difference is that TypeScript does not let us use it until we check what it is.

```ts
let value: unknown = "hello";
value.toUpperCase(); // Error

if (typeof value === "string") {
  value.toUpperCase(); // OK, now we know it is a string
}
```

## never: A Value That Can Never Exist

`never` means "this can never happen". We see it when a function always throws an error, or when we have already handled every possible case.

```ts
function throwError(message: string): never {
  throw new Error(message);
}
```

## Why We Should Prefer unknown Over any

Both accept any value. But with `any`, TypeScript stops protecting us, and bugs show up only when the code runs. With `unknown`, TypeScript makes us check the value first, so we catch mistakes early. That is why `unknown` is the safer choice.

## Conclusion

We use `unknown` when we do not know a value's type yet, like data from an API. We use `never` for things that should never happen. And we avoid `any` as much as we can.
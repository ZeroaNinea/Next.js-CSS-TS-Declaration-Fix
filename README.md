# Next.js + CSS + TS Declaration Fix

Found a small DX issue in a fresh Next.js project: CSS side-effect imports trigger a TS error. Here’s why it happens and the minimal fix.

## Background

When you create a new Next.js project, it throws an error: "Cannot find module or type declarations for side-effect import of './globals.css'.". This issue occurs because TypeScript by default does not support CSS side-effect imports.

## Solution

To fix this, create a new declaration file in the root of the project that allows TypeScript to understand the CSS side-effect import.

[`custom.css.d.ts`](./custom.css.d.ts)

```ts
declare module '*.css';

declare module '*.module.css' {
  const classes: { readonly [key: string]: string };
  export default classes;
}
```

## References

- **Medium article:** Next.js + CSS + TS Declaration Fix

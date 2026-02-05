# Next.js + CSS + TypeScript Declaration Fix

This repository demonstrates a small DX issue in a fresh Next.js project where
TypeScript reports an error for CSS side-effect imports, and shows a minimal fix.

## Background

When creating a new Next.js project, TypeScript may report the following error:

> Cannot find module or type declarations for side-effect import of "./globals.css".

This happens because TypeScript does not include type declarations for CSS
side-effect imports by default, even though the runtime behavior is valid.

## Solution

Add a global declaration file to inform TypeScript how to handle CSS imports.

[`custom.css.d.ts`](./custom.css.d.ts)

```ts
declare module '*.css';

declare module '*.module.css' {
  const classes: { readonly [key: string]: string };
  export default classes;
}
```

## Notes

This does not affect runtime behavior — it only resolves TypeScript's
type-checking.

## References

- **Medium:** [https://medium.com/@heghine.dev357/next-js-css-typescript-declaration-fix-b9373d263935](https://medium.com/@heghine.dev357/next-js-css-typescript-declaration-fix-b9373d263935)
- **LinkedIn:** (link)

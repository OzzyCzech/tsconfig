# @ozzyczech/tsconfig

Shared [TypeScript config](https://www.typescriptlang.org/docs/handbook/tsconfig-json.html) for my projects.
Two variants: a strict **Node.js / Bun** library preset (default) and a **DOM / browser** preset for bundler-based apps.

## Install

```shell
npm install --save-dev @ozzyczech/tsconfig
```

```shell
yarn add --dev @ozzyczech/tsconfig
```

```shell
pnpm add -D @ozzyczech/tsconfig
```

```shell
bun add -d @ozzyczech/tsconfig
```

## Usage

### Node.js / Bun library (default)

Strict Node ESM: `module` and `moduleResolution` set to `nodenext`, `lib: ["ES2024"]`, no DOM, no JSX.

```json
{
	"extends": "@ozzyczech/tsconfig",
	"include": ["src/**/*"]
}
```

### DOM / browser / React

Extends the base and adds `DOM` + `DOM.Iterable` libs, `jsx: "react-jsx"`, and `moduleResolution: "bundler"` for Vite / esbuild / Next / Bun.

```json
{
	"extends": "@ozzyczech/tsconfig/dom",
	"include": ["src/**/*"]
}
```

## What's enabled

Both variants share these strict compiler options:

- `strict`, `noImplicitReturns`, `noImplicitOverride`
- `noUnusedLocals`, `noUnusedParameters`
- `noFallthroughCasesInSwitch`, `noUncheckedIndexedAccess`, `noUncheckedSideEffectImports`
- `erasableSyntaxOnly` — disallows `enum`, parameter properties, `namespace`; keeps code compatible with type-stripping runtimes (Node 22+, Bun, `tsx`)
- `isolatedModules` — every file must be transpilable in isolation (required by esbuild, swc, Babel)
- `declaration`, `stripInternal` — emits clean `.d.ts` suitable for libraries
- `resolveJsonModule`, `esModuleInterop`, `allowSyntheticDefaultImports`
- `skipLibCheck`, `incremental`

The output directory defaults to `${configDir}/dist` and is excluded from compilation.

## Releasing

Push a semver tag — the [`publish.yml`](.github/workflows/publish.yml) workflow builds, publishes to npm with provenance, and creates a GitHub Release from commit messages.

```shell
git tag v2.0.0 && git push origin v2.0.0
```

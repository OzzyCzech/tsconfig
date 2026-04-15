# Shared TypeScript Config

Do not repeat yourself! This package provides a shared [TypeScript config](https://www.typescriptlang.org/docs/handbook/tsconfig-json.html)

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

## Usage

Default — Node.js / Bun library:

```json
{
	"extends": "@ozzyczech/tsconfig"
}
```

DOM / browser / React variant:

```json
{
	"extends": "@ozzyczech/tsconfig/dom"
}
```

## Releasing a new version

Push a semver tag — the `publish.yml` workflow will build and publish to npm with provenance, then create a GitHub Release.

```shell
git tag v2.0.0 && git push origin v2.0.0
```
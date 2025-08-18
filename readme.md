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

`tsconfig.json`

```json
{
	"extends": "@ozzyczech/tsconfig"
}
```

## Releasing a new version

```shell
npx np --no-test
```
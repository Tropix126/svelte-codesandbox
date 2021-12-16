# svelte-codesandbox

![Sandbox Component Showcase](https://i.imgur.com/im0orSe.png)

A powerful Svelte wrapper component around the CodeSandbox editor embed. Useful for creating interactive demos and documenting code without throwing together your own REPL.

## Installation

#### npm
```bash
npm install svelte-codesandbox
```

#### pnpm
```bash
pnpm install svelte-codesandbox
```

#### yarn
```bash
yarn add svelte-codesandbox
```

## Usage

#### Basic Usage
```tsx
<script>
    import { Sandbox } from "svelte-codesandbox";
</script>

<Sandbox src="sandbox-id" />
```

#### Customizing the Sandbox
```tsx
<script>
    import { Sandbox } from "svelte-codesandbox";
</script>

<Sandbox
    --sandbox-height="800px"
    src="sandbox-id"
    codemirror
    fontSize={16}
    theme="light"
    highlights={[1, 3]}
    modules={["src/index.js", "src/App.js"]}
/>
```

For an in-depth list of customization options, visit [CodeSandbox's embedding documentation](https://codesandbox.io/docs/embedding).

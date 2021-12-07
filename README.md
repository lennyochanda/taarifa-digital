## Developing

Once you've forked the project and cloned locally, install dependencies with `npm install` (or `pnpm install` or `yarn`), start a development server:

```bash
npm run dev

# or start the server and open the app in a new browser tab
npm run dev -- --open
```

## Building

This project comes with a vercel adapter but you can install an [adapter](https://kit.svelte.dev/docs#adapters) for your target environment. Make sure to change your package.json and svelte config files accordingly. Then:

```bash
npm run build
```

> You can preview the built app with `npm run preview`, regardless of whether you installed an adapter. This should _not_ be used to serve your app in production.

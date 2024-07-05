# SvelteKit web worker cache issue 

## How to reproduce
First, run the following commands to build files.
```
git clone https://github.com/MoonlightOffice/sveltekit-webworker-cache-issue.git

cd sveltekit-webworker-cache-issue

npm i

npm run build
```

Next, take a look at `build/service-worker.js` and try to find file names that start with `/_app/immutable/`. You'll notice that only `/app/immutable/workers/` are not included, while other directories such as `/app/immutable/chunks` and `/app/immutable/entry` are included.

## How I created this project

1. Run `npm create svelte@latest` to create a blank project with Svelte 5 enabled.

2. Change the adapter to `@sveltejs/adapter-static` and add `export const prerender = true` in `+layout.ts`.

3. Add a sample web worker demo in `src/routes` directory.

4. Copy-pasted service worker from [SvelteKit's docs](https://kit.svelte.dev/docs/service-workers#inside-the-service-worker).
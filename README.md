# Vue 3 + TypeScript + Vite

This template should help get you started developing with Vue 3 and TypeScript in Vite. The template uses Vue 3 `<script setup>` SFCs, check out the [script setup docs](https://v3.vuejs.org/api/sfc-script-setup.html#sfc-script-setup) to learn more.

## Recommended IDE Setup

- [VS Code](https://code.visualstudio.com/) + [Volar](https://marketplace.visualstudio.com/items?itemName=Vue.volar) (and disable Vetur) + [TypeScript Vue Plugin (Volar)](https://marketplace.visualstudio.com/items?itemName=Vue.vscode-typescript-vue-plugin).

## Install tailwind

````
npm install -D tailwindcss postcss autoprefixer
````
````
npx tailwindcss init -p
````
add path
````
content: [
    "./index.html",
    "./src/**/*.{vue,js,ts,jsx,tsx}",
  ],
````

add directive to css
````
@tailwind base;
@tailwind components;
@tailwind utilities;
````

## Install heroicons

````
npm i @heroicons/vue
````

## Install dayjs

````
npm i dayjs
````
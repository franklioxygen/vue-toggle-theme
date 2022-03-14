# vue-toggle-theme

A simple implementation of toggle dark mode of Vue3.
It could display user's preference on load, and toggle-able by user.

Please refer to 

- ./src/App.vue
- ./src/assets/base.scss
<img width="167" alt="Screen Shot 2022-03-14 at 3 03 32 PM" src="https://user-images.githubusercontent.com/2637636/158243403-9f5944c2-7d85-441a-8566-98ddea6bfa06.png">


- css
```
[data-theme="dark"] {}
```

- html
```
    <input
      type="checkbox"
      name="mode"
      id="change-theme"
      :checked="isDarkMode()"
    />
```

- Vue
```
<script setup>
import { onMounted } from "@vue/runtime-core";
let switchScheme = (scheme) => {
  document.documentElement.setAttribute("data-theme", scheme);
};
let isDarkMode = () => {
  return (
    window.matchMedia &&
    window.matchMedia("(prefers-color-scheme: dark)").matches
  );
};
onMounted(() => {
  // add event listener for change theme
  document
    .getElementById("change-theme")
    .addEventListener("change", (event) => {
      event.target.checked ? switchScheme("dark") : switchScheme("light");
    });
  //initial mode
  isDarkMode() ? switchScheme("dark") : null;
});
</script>
```



## Recommended IDE Setup

[VSCode](https://code.visualstudio.com/) + [Volar](https://marketplace.visualstudio.com/items?itemName=johnsoncodehk.volar) (and disable Vetur) + [TypeScript Vue Plugin (Volar)](https://marketplace.visualstudio.com/items?itemName=johnsoncodehk.vscode-typescript-vue-plugin).

## Customize configuration

See [Vite Configuration Reference](https://vitejs.dev/config/).

## Project Setup

```sh
npm install
```

### Compile and Hot-Reload for Development

```sh
npm run dev
```

### Compile and Minify for Production

```sh
npm run build
```

### Lint with [ESLint](https://eslint.org/)

```sh
npm run lint
```
# vue-toggle-theme

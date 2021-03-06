#### Packages
- `@changes`: `"nuxt": "^2.15.8"` -> `"nuxt-edge": "latest"`
- `@removed`: `"@nuxt/typescript-build": "latest"`
- `@removed`: `"@nuxtjs/composition-api": "^0.32.0"`

#### @nuxt/composition-api
- `@removed`: `import {} from '@nuxt/composition-api'`
- `@changed`: `useContext()` -> `useNuxtApp()`
<br>*<b>note:</b>* any keys that previously exists in `useContext()` is now moved into `useNuxtApp().nuxt2Context`, so you can't directly use it from `useNuxtApp()`
- `@changes`: route (previously in `useContext()`) is no longer in ref, so you should directly use the value of it, for example:
  - before: `const currentRoute = route.value.name`
  - is now: `const currentRoute = route.name`

#### Miscellaneous
- `$config` & `this.$config` is now separated into 2 types, `app` and `public` (which configured in `nuxt.config.ts -> publicRuntimeConfig`)
<br><b>so,</b> if you want to use any configs that defined in `publicRuntimeConfig` you should use `$config.public`
- Don't know why but seems like you don't need to re-import composable file in every files that need it, for example if you have already imported a composable file in `/layouts/Layout.vue`, then you don't need to re-import it when you want to use it in the child component
- Template refs is not working, the value is encapsulated in `_setupState`
  - before: `someElementRef.value.callTheFunction()`
  - after: `someElementRef.value._setupState.callTheFunction()`

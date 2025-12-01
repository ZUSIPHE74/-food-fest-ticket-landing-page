# food-fest-landing-page

This template should help get you started developing with Vue 3 in Vite.

## Recommended IDE Setup

[VS Code](https://code.visualstudio.com/) + [Vue (Official)](https://marketplace.visualstudio.com/items?itemName=Vue.volar) (and disable Vetur).

## Recommended Browser Setup

- Chromium-based browsers (Chrome, Edge, Brave, etc.):
  - [Vue.js devtools](https://chromewebstore.google.com/detail/vuejs-devtools/nhdogjmejiglipccpnnnanhbledajbpd) 
  - [Turn on Custom Object Formatter in Chrome DevTools](http://bit.ly/object-formatters)
- Firefox:
  - [Vue.js devtools](https://addons.mozilla.org/en-US/firefox/addon/vue-js-devtools/)
  - [Turn on Custom Object Formatter in Firefox DevTools](https://fxdx.dev/firefox-devtools-custom-object-formatters/)

## Customize configuration

See [Vite Configuration Reference](https://vite.dev/config/).

## Project Setup

```sh
npm install
```

### Compile and Hot-Reload for Development

```sh
npm run dev
```

Interactive behaviour
--------------------

The app stores ticket "favourites" in the browser's localStorage (key: `foodfest:favs`). Favouriting persists across reloads — toggle the heart icon on a card to mark as favourite.

Windows PowerShell troubleshooting
---------------------------------

If you run `npm run dev` on Windows PowerShell and see an error like:

"npm.ps1 cannot be loaded because running scripts is disabled on this system"

Then either:

1. Re-run using the Command Prompt (cmd.exe), or call the npm **command file** directly in PowerShell:

```powershell
npm.cmd run dev
```

2. Or enable script execution for the CurrentUser scope (recommended). Open PowerShell and run **once**:

```powershell
Set-ExecutionPolicy -ExecutionPolicy RemoteSigned -Scope CurrentUser
# Then run the dev server:
npm run dev
```

This adjusts PowerShell's execution policy so npm scripts can run. If you are using a managed machine or don't want to change the policy, use `cmd.exe`.

### Compile and Minify for Production

```sh
npm run build
```

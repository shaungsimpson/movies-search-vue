# movie-project
This is a simple movie API vue 3 project built with vite.

## OMDB API Access

In order to get the api working you will need to use an API key, you can [get a free key here](https://www.omdbapi.com/apikey.aspx).

After cloning the repo locally, you can copy the example env file and fill it in.

```bash
cp .example.env .env
```

Then replace this line so that the API key replaces the placeholder text in the .env file.

```sh
VITE_APP_API_KEY="API KEY GOES HERE"
```


> [!WARNING]
> Do NOT commit sensitive details such as API keys to source control.

## Recommended IDE Setup

[VSCode](https://code.visualstudio.com/) + [Volar](https://marketplace.visualstudio.com/items?itemName=Vue.volar) (and disable Vetur) + [TypeScript Vue Plugin (Volar)](https://marketplace.visualstudio.com/items?itemName=Vue.vscode-typescript-vue-plugin).

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

### Run Unit Tests with [Vitest](https://vitest.dev/)

```sh
npm run test:unit
```

### Lint with [ESLint](https://eslint.org/)

```sh
npm run lint
```

# webpack issue repro

### repro steps

```
yarn install # or npm install
yarn webpack # run the build
yarn start # serve from ./dist
```

Then open the browser console and see this error:

```
main.js:1 Uncaught TypeError: r is not a function
    at main.js:1
    at main.js:1
    at main.js:1
```

I think the export from `foo.js` is wrongly being wrongly tree-shaken away or something. Shouldn't including the module via `require.resolve` include all the exports from the module?

If you set `mode: 'development'` in `webpack.config.js` and rebuild, there is no error.
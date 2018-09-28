# react-select tree-shaking

```sh-session
$ yarn
$ yarn build
```

See output:

```
  Asset     Size  Chunks             Chunk Names
main.js  207 KiB       0  [emitted]  main
Entrypoint main = main.js
 [6] (webpack)/buildin/global.js 509 bytes {0} [built]
[14] ./node_modules/create-emotion/dist/index.esm.js + 4 modules 32.1 KiB {0} [built]
     |    5 modules
[29] ./src/index.js + 3 modules 147 KiB {0} [built]
     | ./src/index.js 226 bytes [built]
     | ./src/Comps.js 173 bytes [built]
     |     + 2 hidden modules
    + 27 hidden modules
```

Manually edit `node_modules/react-select/package.json` to include `sideEffects: false`, and run `yarn build` again.

```
  Asset     Size  Chunks             Chunk Names
main.js  102 KiB       0  [emitted]  main
Entrypoint main = main.js
 [8] ./src/index.js + 1 modules 409 bytes {0} [built]
     | ./src/index.js 226 bytes [built]
     | ./src/Comps.js 173 bytes [built]
[35] (webpack)/buildin/global.js 509 bytes [built]
    + 34 hidden modules
```

`102 kb` is the same size as if you remove the unused `export` from `Comp.js`.

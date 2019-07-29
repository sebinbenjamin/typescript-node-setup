## Step 1
Typescript Config - tsconfig.json
Used command tsc --init  to create tsconfig file.
Uncomment `sourceMap: true` and other necessary options.
```
{
    "compilerOptions": {
        "target": "es5",
        "module": "commonjs",
        "outDir": "out",
        "sourceMap": true
    }
}
```

## Step 2
- Start Task `tsc:watch` to automatically transpile typescript file.

- Run `nodemon` on the output js file.

### For debugging code

 - Stop `tsc:watch` task and `nodemon` if run previously. 
 - Add VS Code debugger config, which runs tsc before starting the debugger. 

```
"configurations": [
    {
      "type": "node",
      "request": "launch",
      "name": "Launch Program",
      "program": "${file}",
      "preLaunchTask": "tsc: build - tsconfig.json",      // skip in watch mode
      "outFiles": [
        "${workspaceFolder}/out/**/*.js"
      ]
    }
  ]
```
 - Use the VS Code inbuilt debugger.

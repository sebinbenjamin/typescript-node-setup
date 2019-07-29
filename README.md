### Pre-requisite
 - Install typescript 
    ```npm install -g typescript```
 - Install nodemon (optional) 
    ```npm install -g nodemon``` 

## Step 1 - Initialize tsconfig.
Typescript Config - tsconfig.json
Used command `tsc --init`  to create tsconfig file.
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

## Step 2 - Add Debug tasks
 - Add VS Code debugger config, which runs tsc before starting the debugger. 

```
"configurations": [
    {
      "type": "node",
      "request": "launch",
      "name": "Debug after transpiling TS",
      "program": "${workspaceFolder}/out/index.ts",
      "preLaunchTask": "tsc: build - tsconfig.json",      // skip in watch mode
      "outFiles": [
        "${workspaceFolder}/out/**/*.js"
      ]
    }
  ]
```
 - Use the VS Code inbuilt debugger.

### For normal compilation, without debugging 
- Start Task `tsc:watch` to automatically transpile typescript file.
- Run `nodemon` on the output js file.


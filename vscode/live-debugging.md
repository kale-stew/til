# Live Debugging in VSCode

You're going to need a `launch.json`

- update the `TESTING_LIBRARY` to your preferred suite

```js
// .vscode/launch.json

{
  "version": "0.2.0",
  "configurations": [
    {
      "type": "node",
      "request": "launch",
      "name": "Launch Program",
      "program": "${workspaceRoot}/index.js",
      "envFile": "${workspaceRoot}/.vscode/.env",
      "skipFiles": [
        "${workspaceRoot}/node_modules/**/*",
        "<node_internals>/**/*"
      ]
    },
    {
      "type": "node",
      "request": "launch",
      "name": "Launch File",
      "program": "${file}",
      "envFile": "${workspaceRoot}/.vscode/.env",
      "skipFiles": [
        "${workspaceRoot}/node_modules/**/*",
        "<node_internals>/**/*"
      ]
    },
    {
      "type": "node",
      "request": "launch",
      "name": "Test Spec",
      "program": "${workspaceRoot}/node_modules/TESTING_LIBRARY/bin/_TESTING_LIBRARY",
      "args": [
        "-c",
        "--require",
        "test/setup.js",
        "${relativeFile}",
        "--no-timeouts"
      ],
      "skipFiles": [
        "${workspaceRoot}/node_modules/**/*",
        "<node_internals>/**/*"
      ],
      "cwd": "${workspaceRoot}",
      "runtimeArgs": [
        "--nolazy"
      ]
    }
  ]
}
```

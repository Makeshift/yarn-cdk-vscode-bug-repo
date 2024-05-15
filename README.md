# yarn-vscode-bug-repro

Reproduction steps:

1. Clone this repo
2. Open VSCode and open a terminal panel within VSCode in the repo
3. Initialise yarn and install the `aws-cdk` dependency by running `yarn`
4. Run `echo $NODE_OPTIONS` - it should show that the VSCode bootloader is being injected, something like `--require $HOME/.vscode-server/data/User/workspaceStorage/$UUID/ms-vscode.js-debug/bootloader.js`
5. Run `yarn cdk` - This should hang
6. Unset the `NODE_OPTIONS` var to remove the VSCode bootloader with `unset NODE_OPTIONS`
7. Run `yarn cdk` - CDK will display its help text.

Reproducible with:

```
Version: 1.89.1 (system setup)
Commit: dc96b837cf6bb4af9cd736aa3af08cf8279f7685
Date: 2024-05-07T05:13:33.891Z
Electron: 28.2.8
ElectronBuildId: 27744544
Chromium: 120.0.6099.291
Node.js: 18.18.2
V8: 12.0.267.19-electron.0
OS: Windows_NT x64 10.0.22631

  System:
    OS: Linux 5.15 Ubuntu 23.04 23.04 (Lunar Lobster)
    CPU: (22) x64 AMD Ryzen 9 5900X 12-Core Processor
  Binaries:
    Node: 20.13.1 - /tmp/xfs-c578a5e8/node
    Yarn: 4.0.2 - /tmp/xfs-c578a5e8/yarn
    npm: 10.5.2 - ~/.nvm/versions/node/v20.13.1/bin/npm
    bun: 1.1.3 - ~/.bun/bin/bun
```

with version 1.89.0 of the [JavaScript Debugger](https://github.com/microsoft/vscode-js-debug) extension for VSCode.

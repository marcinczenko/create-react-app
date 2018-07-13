# react-scripts

In order to sync it with upstream follow the steps:

```bash
$ git fetch upstream
$ git checkout next
$ git merge upstream/next
$ git checkout mono
$ git rebase next
```

> Some conflicts may be there when rebasing. Do not panic!

Now in the monorepo where you have your create-react-app as one of the workspaces (or packages), go to top level `node_modules` and open `package.json` of `react-scripts`. Now make sure that you sync the
dependencies version from you `mono` with the dependencies in the original `react-scripts` package. 

> This original `react-scripts` package should have version similar to `2.0.0-next.3e165448`. Make sure you align this version with the version in the `package.json` on the `mono` branch.

Now you are ready to publish.

```bash
$ npm login // optional - if required
$ cd packages/react-scripts
$ npm publish
```

> The actual modification that keeps linter away from other packages is in file `packages/react-scripts/config/paths.js` towards the bottom of the file. Below is the part we commented out:

```javascript
// if (mono.isAppIncluded) {
//   Array.prototype.push.apply(module.exports.srcPaths, mono.pkgs);
// }
```

# original documentation

This package includes scripts and configuration used by [Create React App](https://github.com/facebook/create-react-app).<br>
Please refer to its documentation:

* [Getting Started](https://github.com/facebook/create-react-app/blob/master/README.md#getting-started) – How to create a new app.
* [User Guide](https://github.com/facebook/create-react-app/blob/master/packages/react-scripts/template/README.md) – How to develop apps bootstrapped with Create React App.

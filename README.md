# Try npm workspaces

Install:

```bash
npm i
```

Build:

```bash
npm run build -ws
```

Run the app:

```bash
npm run dev -w app
```

If you do a change in one of the dependencies, you need to rebuild it, and the app too. The easiest way to do it is to rebuild everything with:

```bash
npm run build -ws
```

The versions must match: if the selector for "theme" in the "components" package is `^1.0.0`, the version of "theme" must be `1.0.0` or higher. If you increment the version of `theme` to `2.0.0`, you need to update the dependencies in `components` to `^2.0.0`, or `2.0.0`, or any other matching expression. Once done, don't forget to run:

- check that the versions are correct in the `package.json` files by installing again: `npm i`
- rebuild everything: `npm run build -ws`

The advantage of such setup is that we can update multiple packages in the same PR and test them together. Once merged to main, we can publish all the packages to npm (in order).

References:

- official doc: https://docs.npmjs.com/cli/v10/using-npm/workspaces
- an overview: https://medium.com/@ruben.alapont/npm-workspaces-managing-multi-package-projects-28538fe40d1d
- how to ensure the same dependency in all the workspaces: https://tobiasedwards.co.uk/blog/unifying-dependency-versions-across-npm-workspaces/

Limitations:

- a workspace can access dependencies of another workspace, without the dependency being explicit: https://edrickleong.hashnode.dev/why-you-shouldnt-use-npm-workspaces

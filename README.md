# WebDevStudios NPM Scripts

<a href="https://webdevstudios.com/contact/"><img src="https://webdevstudios.com/wp-content/uploads/2018/04/wds-github-banner.png" alt="WebDevStudios. WordPress for big brands."></a>

This package, when installed, exposes `wds-*` scripts that can be run from your `package.json`'s scripts.

Most of the commands simply run their `@wordpress/scripts` variant, e.g.:

```bash
wds-build
```

Runs:

```bash
wp-scripts build
```

## Why

The reason we do this is by having this layer in between your `package.json` and `@wordpress/scripts` is we can control, ultimately, what your scripts should do.

For instance, for `wds-lint-js` we don't use `@wordpress/scripts`'s prettier command, and instead do `eslint --fix` because that's what WebDevStudio's does.

## Install

```bash
npm install @webdevstudios/npm-scripts --save-dev
```
## Example

```json
"scripts": {
    "build": "wds-build",
    "lint": "run-s lint:js lint:style",
    "lint:js": "wds-format-js && wds-lint-js",
    "lint:style": "wds-format-styles && wds-lint-style",
    "packages-update": "wds-packages-update",
    "start": "wds-start"
}
```

## Changelog 

[See Releases on Github](https://github.com/WebDevStudios/npm-scripts/releases)

## Release Process

1. On `master`, run `npm version PATCH|MINOR|MAJOR` to bump version
2. `git push --tags`
2. `npm run pack`
3. Create [Release](https://github.com/WebDevStudios/npm-scripts/releases) on Github
4. Attach `webdevstudios-npm-scripts-{version}.tgz` to release
5. `npm publish`

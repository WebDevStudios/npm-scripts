# WordPress NPM Scripts

<a href="https://webdevstudios.com/contact/"><img src="https://webdevstudios.com/wp-content/uploads/2018/04/wds-github-banner.png" alt="WebDevStudios. WordPress for big brands."></a>

This package, when installed, allows you to run the commands in `bin/` in your `package.json` scripts.

Most of the `wds-*` commands simply run their `@wordpress/scripts` variant, e.g.:

```
wds-build
```

Runs:

```
wp-scripts build
```

The reason we do this is by having this layer in between your `package.json` and `@wordpress/scripts` is we can control, ultimately, what your scripts should do.

For instance, for `wds-lint-js` we don't use `@wordpress/scripts`'s prettier command, and instead do `eslint --fix`.

## Example

```json
"scripts": {
  "build": "wds-build",
  "format:js": "wds-format-js",
  "format:styles": "wds-format-styles",
  "lint": "run-s lint:js lint:style lint:php",
  "lint:js": "run-s format:js && wds-lint-js",
  "lint:style": "run-s format:styles && wds-lint-style",
  "packages-update": "wds-packages-update",
  "postinstall": "npm run build",
  "start": "wds-start"
}
```

With this in your `package.json` when you run e.g. `npm run build` you can trust you are running the most up to date command we want you to run, which now is `wp-scripts build`.

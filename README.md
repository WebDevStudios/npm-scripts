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

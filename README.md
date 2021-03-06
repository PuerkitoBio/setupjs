# Example Setup For Javascript Development

Run `npm install` in the root directory to install all dependencies. This setup is highly opinionated and personal, YMMV. Hopefully it will stay relevant for a couple weeks. It provides the following:

* ES2015 support via `babel` (including polyfill)
* Type-checking via `flow`
* Linting via `eslint`
* npm- and browserify-based build system (i.e. no gulp/grunt/etc.)
* Templating via `jade`
* CSS preprocessor via `sass`
* Minified production builds for HTML, CSS and JS (via `uglifyjs`)
* Separate javascript bundles for dependencies (e.g. `babel-polyfill` is in a separate file from the app's code)
* Source maps generated for development build (CSS and JS)
* Tests via `mocha`
* Automatic cache-busting for production build via hashes of content in the filenames
* Pre-commit hook that checks linting and type-checking errors

## Directory Layout

- `/` : configuration files
- `/src` : the source files
- `/src/styles` : the sass files
- `/src/js` : the javascript (ES2015 with Flow type annotations) files
- `/src/templates` : the jade templates
- `/src/templates/layouts` : the layout templates ("master" templates from which pages inherit)
- `/src/templates/includes` : includes jade files ("partials")
- `/build` : the generated build files, HTML files are directly in this directory
- `/build/js` : the generated (ES5, stripped of type annotations) javascript files
- `/build/css` : the generated CSS files
- `/scripts` : the bash scripts used for the various `npm run-script` commands
- `/misc` : miscellaneous helper files (e.g. git hook)
- `/test` : test files, run with `npm test`
- `/interfaces` : flow third-party type definitions
- `/decls` : flow type declarations common to the whole project

See the `package.json` file for the various `run-script` commands. Most interesting are probably `npm run build` (set `NODE_ENV=production` for minified builds), `npm run watch` and `npm run test` (or simply `npm test`).

## Editor Support

For vim, install `eslint` and `flow-bin` globally and activate as checkers in syntastic to get errors on save. `flow` is probably too slow for this though.

## Installed Libraries

In addition to the development dependencies, this setup installs the following (personal preferences):

* `redux` (bundled separately from the app's code)
* `redux-thunk` (bundled with `redux`)
* `deku` (bundled separately from the app's code)
* `dscript` (generic hyperscript, bundled with `deku`)
* `bulma` (CSS framework)
* `font-awesome` (linked from CDN in jade template)

## File Sizes

The client-downloaded file sizes are as follows for the production build (minified) and served gzipped:

* CSS (bulma): 13.1KB
* babel-polyfill: 34.4KB
* redux (+redux-thunk): 3.0KB
* deku (+dscript): 7.6KB

For a total (excluding app's code, style and html) of 58.1KB.

## License

The BSD 3-clause license.


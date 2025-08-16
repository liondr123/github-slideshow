<general_rules>
When creating new functions or files, always consider the existing structure and try to place them in relevant, existing directories. If a suitable directory doesn't exist, create a new one that logically groups related files.

Commonly executed scripts:
- `script/setup`: This script handles the initial setup of the development environment, including Homebrew dependencies (macOS), Ruby version management with rbenv, and Ruby gem installation with Bundler. It also updates git submodules.
- `script/cibuild`: This script builds the Jekyll site and runs `htmlproofer` for validation.
- `grunt` commands (within `node_modules/reveal.js`): The `reveal.js` dependency uses `grunt` for various tasks.
    - `grunt test`: Runs tests for `reveal.js` (uses QUnit).
    - `grunt jshint`: Runs JSHint for linting JavaScript files.
    - `grunt sass`: Compiles Sass files to CSS.
    - `grunt autoprefixer`: Adds vendor prefixes to CSS.
    - `grunt cssmin`: Minifies CSS files.
</general_rules>
<repository_structure>
This repository is primarily a Jekyll site that utilizes `reveal.js` for presentations.
- `_config.yml`: Main Jekyll configuration file, including site-wide settings, Jekyll plugins, and `reveal.js` specific configurations.
- `_includes/`: Contains reusable HTML snippets for Jekyll.
- `_layouts/`: Defines the layouts for Jekyll pages.
- `_posts/`: Stores Jekyll blog posts, which in this context appear to be individual slides for the presentation.
- `node_modules/`: Contains Node.js dependencies, most notably `reveal.js`.
- `script/`: Houses shell scripts for setup, building, and other development tasks.
- `Gemfile` and `Gemfile.lock`: Manage Ruby gem dependencies for Jekyll.
</repository_structure>
<dependencies_and_installation>
The project has both Ruby and Node.js dependencies.

Ruby Dependencies:
- Managed with `Bundler` and defined in `Gemfile`.
- Installation: Run `bundle install` after ensuring Ruby is set up (e.g., via `rbenv`).
- The `script/setup` script automates this process, including `rbenv` installation if needed.

Node.js Dependencies:
- Primarily `reveal.js`, managed via `npm` or `yarn`.
- The `package.json` for `reveal.js` is located in `node_modules/reveal.js/package.json`.
- Installation: `npm install` or `yarn install` in the `node_modules/reveal.js` directory, or rely on the `git submodule update --init` command in `script/setup` if `reveal.js` is managed as a submodule.
</dependencies_and_installation>
<testing_instructions>
The primary testing framework identified is `QUnit`, used by the `reveal.js` dependency for its JavaScript tests.

To run tests for `reveal.js`:
- Navigate to the `node_modules/reveal.js/` directory.
- Execute `grunt test`. This command will run `jshint` for linting and then `qunit` for unit tests.

For the main Jekyll site, `htmlproofer` is used as a validation tool during the build process.
- To run `htmlproofer` checks, execute `script/cibuild`. This script builds the Jekyll site and then runs `htmlproofer` against the generated `_site/index.html` with the `--empty-alt-ignore` flag.
</testing_instructions>
<pull_request_formatting>
</pull_request_formatting>


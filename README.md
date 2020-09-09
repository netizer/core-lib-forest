# Core Library for Forest language

Forest is a programming language designed for being embedded in other (host) languages. `core-lib-forest` is its core library. Any core functionality that can be written in Forest, and not in the host language, will, sooner or later, end up in core-lib-forest. Currently the most important parts are:
- Tests - forest-rb doesn't have many tests. Most of them are here.
- Templates - every file in Forest can be embedded in a template (also written in Forest). These templates are stored as part of core-lib-forest.

For more info about Forest, check out https://github.com/netizer/forest-rb

## The structure of core-lib-forest

Most of the code here is written in Groundcover because it compiles to Forest, but at the same time it's a superset of Forest, so we can express everything we want that is possible to express in Forest. The Groundcover files have the extension ".gc" and the forest files have the extension ".forest".

core-lib-forest is just a module. The module system of Forest is not finalised yet, so the structure might change significanty.

Currently the structure looks like this:
- `app.gc` - all the code where we use the library as an application. Running tests, or any other commands that treat the library as the starting point is expressed here.
- `lib.gc` - this file contains information needed when using this code as library. For example information about dependencied.
- `lib/main.gc` - We load all tests in here.
- `lib/**/*.*` - All the other files apart from main.gc are tests. You might ask: Why we store them in `lib` then? Well, tests are kept together with the code in Forest. You might not see that because there are not many things in core-lib-forest just yet. If you think that the idea of keeping tests together with the tested code is crazy, check out [Pyret](https://www.pyret.org/).
- `templates` - when we process a file with a specific `flow` (e.g. `run` or `test`), we wrap the file in one of the templates. The template determines which part of the file is going to be activated for execution.

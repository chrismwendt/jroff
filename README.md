![jroff](https://cloud.githubusercontent.com/assets/4419992/11488319/61d7086e-97a4-11e5-9ea7-2276c409c208.png)

![travis](https://travis-ci.org/roperzh/jroff.svg?branch=master)
[![Code Climate](https://codeclimate.com/github/roperzh/jroff/badges/gpa.svg)](https://codeclimate.com/github/roperzh/jroff)
[![Test Coverage](https://codeclimate.com/github/roperzh/jroff/badges/coverage.svg)](https://codeclimate.com/github/roperzh/jroff/coverage)

## Usage

(**TODO**)

## Contributing

For regular development, you need to have `Node.js >=0.10` installed on
your system, then:

Clone the repository

```console
git clone git@bitbucket.org:roperzh/jroff_final.git
cd jroff_final
```

Install the required dependencies

```console
npm install
```

Build your local copy and run the tests:

```console
make all
```

### Brief explanation of the code organization

`dist`: This folder stores the bundled versions of the code.

`src/core`: As the folder name says, this is the core of the library.
There is no HTML-related code here, only code to parse and build the AST.

`src/generators`: Generators are entities capables of consume the AST
generated by the parser and produce an output. For the moment only an HTML
generator is implemented.

`src/macros`: Implementations of macro commands divided in macro packages.
For the moment only `an` and `doc` packages are supported.
Macros supported by groff are stored in `default.js`.

`src/utils`: Utility functions and stuff.

### Brief explanation of useful make commands

***make dist:*** beautify and build both minified and concatenated versions
of the code.

***make hint:*** run [js-hint](http://jshint.com/) over the test files
and the concatenated non-minified version of the code.

***make beautify:*** run [js-beautify](https://github.com/beautify-web/js-beautify)
over all the JavaScript files.

***make doc:*** build a local documentation based on the current version
of the code, useful to preview the documentation before pushing.
Check the next section for more details.

### Documenting new code

This library uses [jsdoc3](https://github.com/jsdoc3/jsdoc) to generate
the documentation, so all the new code must be documented using jsdoc
tags. An useful reference can be found [here](http://usejsdoc.org/index.html).

Also, due to [limitations](https://github.com/jsdoc3/jsdoc/issues/930) with
jsdoc and UMD it is required to add the `@alias` tag to all functions,
constructors and namespaces.

### Generating the documentation

The Makefile includes an useful command to generate and push the
documentation to GitHub and GitHub pages, you can simply run:

```console
make doc-build
```

**Note:** please make sure to stash or commit all your changes
before building the documentation.

If you want to preview the changes before pushing, you can generate
the documentation with the `doc` task and then and open `docs/index.html`
in your browser.

This is an example using OS X:

```console
make doc
open docs/index.html
```

### Benchmarks

Running benchmarks is complicated, and even more complicated in this specific
case since there aren't other libraries to use as a reference and compare
the results.

In consequence the idea of this benchmarks is to compare different versions
of the library against three arbitrary man pages: `Git`, `Node.js`
and `Ruby`.

This benchmark should be used only as an estimative comparation between
versions or complex features.

If you want to run the benchmarks and compare with the latest stored results:

```console
make bench
```

Alternatively you can store the results of the current benchmark in the
cache file (`benchmarks/benchmarks.json`) with the `-s` flag:

```console
make bench flags='-s'
```
### TODOs

- [x] Performance measures ( https://github.com/bestiejs/benchmark.js )
- [x] Finish the contributing section
- [ ] Add instructions to define new macros
- [x] Create a logo (?
- [ ] Clean up the code
- [x] Add black box tests
- [ ] Finish unit tests
- [x] Fix issues with the parser
- [x] Add missing macros
- [ ] Documentation
  - [x] Implement a build system to document pages
  - [ ] Add documentation to all the code
  - [x] Add instructions in the readme to build the documentation
- [ ] Look for more semantic markup
- [ ] Review the README
- [x] Better way to send arguments to macro calls
- [x] Add CI integration
- [x] Handle scape characters
- [ ] Add support for nested numeric lists
- [x] Add support for `-compact` arguments in lists
- [ ] Add support for `-width` arguments in lists
- [ ] Make clear when the code is using a global variable

### Links

- [About macros](http://www.schweikhardt.net/man_page_howto.html#q5)
- [About the `an` macro](http://linux.die.net/man/7/man)
- [About the `doc` macro](https://www.dragonflybsd.org/cgi/web-man?command=mdoc&section=7)
- [Troff spec](http://cm.bell-labs.com/sys/doc/troff.pdf)

## License

All the code contained in this repository, unless explicitly stated, is
licensed under MIT license.

A copy of the license can be found inside the [LICENSE](LICENSE) file.
# ToC

<!-- vim-markdown-toc GFM -->

* [npm-lib-starter](#npm-lib-starter)
    * [Description](#description)
        * [What does it actually do?](#what-does-it-actually-do)
        * [CI](#ci)
    * [Installation](#installation)
    * [Development](#development)
        * [NPM link](#npm-link)
        * [jsDoc](#jsdoc)
    * [Publishing](#publishing)
        * [Account](#account)
        * [Different needs, different builds](#different-needs-different-builds)
            * [UMD bundles](#umd-bundles)
            * [src/](#src)
            * [commonJS](#commonjs)
            * [ES6-Modules](#es6-modules)
        * [Versioning](#versioning)
        * [Tagging + BETA-releases](#tagging--beta-releases)
        * [Scoped releases](#scoped-releases)
        * [Basic publishing routine](#basic-publishing-routine)
    * [API](#api)
        * [build](#build)
        * [flow](#flow)
        * [lint](#lint)
        * [test](#test)
        * [docs](#docs)

<!-- vim-markdown-toc -->

# npm-lib-starter

## Description

_npm-lib-starter_ is supposed to take away the inital setup for the creation
of npm libraries and modules and create an enjoyable workflow with the integration
of tools like [standardJS](https://standardjs.com/), [Flow](https://flow.org/) and
[Babel](https://babeljs.io/).


### What does it actually do?

The following things can be done inside the initial setup:

* Creates a local project with the following placeholders prefilled:
    * _project name_
    * _maintainer_
    * _email_
    * _description_
    * _project namespace (i.e. GitHub username or org)_
    * _issue tracker URL_
    * _repository URL_
    * _homepage URL_
* Lets you install npm dependencies immediately
* Creates new git repository and creates an initial commit
* Adds remote `origin` with the specified repository url
* Sets upstream to master

Afterwards your project is ready to push to your remote and to be published to
npm. For further information about the publishing process and available scripts
have a look at [API](#api) and [Publishing](#publishing).


### CI

This cookiecutter already includes a `.travis.yml` and a _coveralls_ script.
If you have a [Travis CI](https://travis-ci.org/) and a [Coveralls](https://coveralls.io/)
account you just need to activate your repository inside both systems.
For further information read their respective documentation.


## Installation

This template uses cookiecutter for the initial setup.

To get started you first need to install Python and [Cookiecutter](https://cookiecutter.readthedocs.io/en/latest/installation.html), on your local maschine.

If you want to immediately connect your local repository to a remote (i.e. on GitHub)
create the remote repository before you run the setup script.

You are able to then fill in a _base_url_,  _namespace_ and _project_name_ during the setup procedure.
Given your repository is something like `git@github.com:<yourname>/<project>`, _base_url would
be `github.com`, _namspace_ would be `<yourname>` and _project_name__ would be `<project>`.

Now you can simply run the following command to run the setup script and install the template:

```shell
    cookiecutter gh:4so-fourseasons/npm-lib-starter
```

This will create a new project in its own directory, ask you a few questions and
update certain files according to the answers you give. This will also let you initialize a new git
repository inside the new directory and immediately install npm dependencies.
You can then add your remote repository and make an initial commit + push.


## Development

### NPM link

Before you publish your project you should of course do some manual regression
testing and use it inside another project. You can use [npm-link](https://docs.npmjs.com/cli/link)
for this purpose. Be aware that sometimes the created symlink might mess up
eslint and other linters inside your target project. Just add the path
of the library you are building to the `ignore`-config of your linter or disable your linter
as a whole during testing.


### jsDoc

To document your API we have already included [JSDoc](http://usejsdoc.org/) with
its standard theme. We have also added a pre-commit hook that rebuilds documentation
and adds it to your commit for your convenience. That way you can be sure that your
API-documentation will be up to date. The resulting docs are compiled into the
`docs/`-directory and do also include the main **README.md** from your repository.

If you are using GitHub it is as easy as just activating [GitHub-Pages](https://pages.github.com/)
with the `master, docs/`-setting to publish your documentation.
We have also added a [shields](shields.io)-badge to your README directly linking to your GitHub-Pages
documentation. Pretty nifty, right? =)


## Publishing

While publishing a npm-package is pretty easy in general, there are a few things
to take into consideration before you release your library to the world.


### Account

First of all you need an npm-account of course, so make sure that you get one and create a user inside your CLI
(if you have done this before you can skip these steps):
[How to publish a package](https://docs.npmjs.com/getting-started/publishing-npm-packages#creating-a-user)


### Different needs, different builds

A package might reach your users on quite a number of ways, which is why we
need to serve different builds for different purposes:


#### UMD bundles

A bundled version as well as a minified bundle reside inside the `dist/` directory
of your library. That way users who would like to include your library in a good
old `<scipt/>`-tag are able to do so.

This bundle is created with [rollup.js](https://rollupjs.org/).


#### src/

We also include the `src/` inside our npm-package, because some users might want
to transpile or change our code theirselves.


#### commonJS

To enable our users to include our library via commonJS `require`-statements
we create a commonJS-build, which usually resides inside the `lib/`-directory.

For this purpose we tranpile our source files with babel to commonJS-modules.


#### ES6-Modules

Of course we should also create an ES6-build, which resides inside the `es/`-directory.

For this purpose we tranpile our source files with babel to ES6-modules.


### Versioning

You probably should follow the [semantic versioning specification](https://semver.org/).
To easily do this with an npm-package make use of the [npm version](https://docs.npmjs.com/cli/version)
command.


### Tagging + BETA-releases

If you don't specify a _tag_ when publishing your package npm will always consider it to
be the **@latest**-release and all your users will automatically fetch this new version.
Sometimes it might be benefitial to first test a release or do some a/b-testing with multiple
release-candidates, though. To do this, you can use npms `--tag` flag during the [publishing process](https://docs.npmjs.com/cli/publish).

Running `npm publish --tag beta` for example will give you the possibility to a) publish your library without overwriting
**@latest**, so that users will not automatically download this release and b) allow you to install
this build with the usage of that tag (i.e. `npm i myLib@beta`).

**NOTE:** You can never publish a specific version of your library twice (no matter what tags you give).
That's why it is preferable to create pre-release versions or release-candidates before you make an actual
version release.


### Scoped releases

You might want to release your package under a specific namespace (i.e. to show it belongs to your organization
or to avoid name clashes with other packages of the same name).
To do this make sure that your package _name_ inside package.json uses your user/org-scope (i.e. `@4so-fourseasons/myModule`).

Now you can publicly publish the module via

```shell
npm publish --access public
```

and install it via

```shell
npm i @4so-fourseasons/myModule
```

For further information have a look at [npm-scope](https://docs.npmjs.com/misc/scope)


### Basic publishing routine

A publishing routine could look a bit like this:

1. Make sure your build works
2. Create a release branch
3. Run `npm version` with the respective version bump and automatically generate a version commit
4. Push the branch to your remote
5. Create a release pull/merge request into your production branch (usually master)
6. After all pipelines ran successfuly and your build is merged tag the release and write a useful changelog
7. Locally pull your updated master branch
8. Publish to npm

Feel free to optimize this workflow with automatic deployments, automatic publishing and the like :)

## API

Below you find the most important npm scripts, that are included
in your library by default.


### build

```bash
npm run build
```

Does some cleanup and removes existing `dist/`, `lib/` and `es/`-directories and then creates our respective UMD/CommonJS/ES-builds.


### flow

```bash
npm run flow
```

Runs flow to typecheck your application


### lint

```bash
npm run lint
```

Runs the [standardJS](https://standardjs.com/)-linter.
Of course you could use your own eslint config or even a different linter. We just like standardJS :)

```bash
npm run lint:fix
```

Uses the fix option so standard tries to resolve conflicts automatically.


### test

```bash
npm run test
```

Runs jest once with verbose output.

```bash
npm run test:coverage
```

Runs jest once with minified output and generates coverage.

```bash
npm run test:watch
```

Runs jest in watch mode with minified output.

```bash
npm run test:coveralls
```

Runs jest once generating coverage and handing it over to the coveralls command line tool. This command is also optimized to run
synchronously inside TravisCI and other CI-Runners via the `--runInBand` flag. This is the prefered script to add to your CI-configuration (inside our `.travis.yml` by default)


### docs

```bash
npm run docs
```

Generates api documentation with JSDoc.

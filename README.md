# 11ty-mnml-gh-actions-pages
An Eleventy built website with GitHub Actions &amp; Pages

* [Requirements](#requirements)
* [Usage](#usage)
	* [Tasks](#tasks)
		* [Build](#build)
		* [Clean](#clean)
			* [Why not use the rm -rf command instead of an utility?](#why-not-use-the-rm--rf-command-instead-of-an-utility?)
		* [Debug](#debug)
		* [Dev](#dev)
		* [Dry Run](#dry-run)
		* [Test](#test)
			* [Why no tests?](#why-no-tests?)
			* [Shorthand alias with NPM](#shorthand-alias-with-npm)
		* [Watch](#watch)
	* [Deployment](#deployment)
* [Common Issues](#common-issues)
* [Contact](#contact)
* [Licence](#licence)

## Requirements

This project requires the following to be installed to be able to run locally.

* [GitHub](https://www.github.com) (A GitHub account)
* [Node](https://www.nodejs.org/) (12.x.x or newer)

## Usage

### Tasks

To start with, this project has a few defined tasks in the [package.json](package.json) which allows you to use the commands that are available for the project.

The commands starts with the following in the command line:

``` shell
npm run <task name>
```

#### Build

Build allows you to build the Eleventy site with the `--quiet` flag so that it will not output a lot of noise in the terminal or on the GitHub Actions Workflow process.

``` shell
npm run build
```

#### Clean

Clean is a task that removes the `./_site` folder so that the project can have a clean state from previous compilations that are triggered by the `build` task.

``` shell
npm run clean
```

This task uses the [rimraf](https://www.npmjs.com/package/rimraf) utility which can be used on MacOS, Linux or Windows.

##### Why not use the `rm -rf` command instead of an utility?

Having better operating systems support is the main reason here. Windows cannot do the `rm -rf` command unless wrapped in a Linux environment as in with [WSL](https://docs.microsoft.com/en-us/windows/wsl/about)*. So the project's aim is to be able to work on any operating system platform with Node.

_* Windows Subsystem for Linux_

This task is run first in sequential process on the [dev](#dev) task then the [watch](#watch) task. It can be run on its own as well.

#### Debug

The Debug task is there to help if the project is not compiling the site correctly as expected. A more in-depth explanation can be found at Eleventy's [documentation](https://www.11ty.dev/docs) ([Debugging](https://www.11ty.dev/docs/debugging/)).

``` shell
npm run debug
```

#### Dev

Dev is a task that uses [npm-run-all](https://www.npmjs.com/package/npm-run-all) utility to be able to run sequentially the [clean](#clean) task, then the [watch](#watch) task so that it can be used while developing locally.

This also will spin up a [BrowserSync](https://www.browsersync.io/) instance which will allow access the site locally at `http://localhost:4321` and `http://localhost:3001` if using BrowserSync UI is deemed to be necessary.

One of the advantages of using [BrowserSync](https://www.browsersync.io/) is that every change that is made and is compilied again, there is no need for manual refreshing of the site if it is open in a browser window. This can aid with speeding up the development by seeing the results almost instantaneously.

#### Dry Run

Dry Run is a tasks that allows the project to be compiled with Eleventy without generating the files. This can be useful as a first debugging step if there is an issue with compiling the project files.

``` shell
npm run dry-run
```

#### Test

Test is a task which is purposely left at the default task setting below when creating a `package.json` file:

``` shell
echo \"Error: no test specified\" && exit 1
```

To run tests, run the command below:

``` shell
npm run test
```

##### Why no tests?

The reason behind this decision is that this project is meant to be agnostic much as possible, and the decision for which testing framework to use whenever it suits the project is up to the developer/engineer.

However it is encouraged that tests are implemented as they can save time in the long term. When tests fail, there is something broken, and it can highlight where it is failing. It allows fixes to be made quickly instead of employing a process of elimination which can be time-costly.

##### Shorthand alias with NPM

There is an alias command for `npm run test` which is part of [NPM](https://docs.npmjs.com/cli/test.html) which can save time typing.

``` shell
npm t
```

This will run the same command as `npm run test` albeit with 4 less characters to type in. 😂

#### Watch

The watch task is an Eleventy task which will refresh and serve the project site locally with [BrowserSync](https://www.browsersync.io/). See Eleventy documentation ([Command Line Usage](https://www.11ty.dev/docs/usage/#re-run-eleventy-when-you-save)) for more information.

``` shell
npm run watch
```

This task is usually run sequentially in the [dev](#dev) task after the [clean](#clean) task has been completed. This task can also be run on its own.

### Deployment
TBD - Explainer of GitHub Actions Workflow, how to set it up and viewing pages via GitHub Pages.

## Common Issues
TBD

----

## Contact

If you have any questions or comments about this project, please [raise an issue](https://github.com/j-mes/11ty-mnml-gh-actions-pages/issues) in this repository.

----
## Licence

This software is published by [James Loveridge](https://github.com/j-mes/11ty-mnml-gh-actions-pages) under the [MIT licence](LICENSE)
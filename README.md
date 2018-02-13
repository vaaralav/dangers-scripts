<div align="center">
<h1>dangers 🛠📦</h1>

<p>CLI toolbox for common scripts for my projects</p>
</div>

<hr />

## The problem

I do a bunch of open source and want to make it easier to maintain so many
projects.

## This solution

This is a CLI that abstracts away all configuration for my open source projects
for linting, testing, building, and more.

## Table of Contents

<!-- START doctoc generated TOC please keep comment here to allow auto update -->

<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->

* [Installation](#installation)
* [Usage](#usage)
  * [Overriding Config](#overriding-config)
* [Inspiration](#inspiration)
* [Other Solutions](#other-solutions)
* [Contributors](#contributors)
* [LICENSE](#license)

<!-- END doctoc generated TOC please keep comment here to allow auto update -->

## Installation

This module is distributed via [npm][npm] which is bundled with [node][node] and
should be installed as one of your project's `devDependencies`:

```shell
yarn add --dev dangers
# Or
npm install --save-dev dangers
```

## Usage

This is a CLI and exposes a bin called `dangers`. I don't really plan on
documenting or testing it super duper well because it's really specific to my
needs. You'll find all available scripts in `src/scripts`.

This project actually dogfoods itself. If you look in the `package.json`, you'll
find scripts with `node src {scriptName}`. This serves as an example of some
of the things you can do with `dangers`.

### Overriding Config

Unlike `react-scripts`, `dangers` allows you to specify your own
configuration for things and have that plug directly into the way things work
with `dangers`. There are various ways that it works, but basically if you
want to have your own config for something, just add the configuration and
`dangers` will use that instead of it's own internal config. In addition,
`dangers` exposes its configuration so you can use it and override only
the parts of the config you need to.

This can be a very helpful way to make editor integration work for tools like
ESLint which require project-based ESLint configuration to be present to work.

So, if we were to do this for ESLint, you could create an `.eslintrc` with the
contents of:

```
{"extends": "./node_modules/dangers/eslint.js"}
```

> Note: for now, you'll have to include an `.eslintignore` in your project until
> [this eslint issue is resolved](https://github.com/eslint/eslint/issues/9227).

Or, for `babel`, a `.babelrc` with:

```
{"presets": ["dangers/babel"]}
```

Or, for `jest`:

```javascript
const {jest: jestConfig} = require('dangers/config')
module.exports = Object.assign(jestConfig, {
  // your overrides here

  // for test written in Typescript, add:
  transform: {
    '\\.(ts|tsx)$': '<rootDir>/node_modules/ts-jest/preprocessor.js',
  },
})
```

> Note: `dangers` intentionally does not merge things for you when you start
> configuring things to make it less magical and more straightforward. Extending
> can take place on your terms. I think this is actually a great way to do this.

## Inspiration

This is inspired by `react-scripts` and `kcd-scripts`.

## Other Solutions

This is forked from [`kcd-scripts`](https://github.com/kentcdodds/kcd-scripts).

## Contributors

Thanks goes to these people ([emoji key][emojis]):

<!-- ALL-CONTRIBUTORS-LIST:START - Do not remove or modify this section -->

<!-- prettier-ignore -->
| [<img src="https://avatars.githubusercontent.com/u/1500684?v=3" width="100px;"/><br /><sub><b>Kent C. Dodds</b></sub>](https://kentcdodds.com)<br />[💻](https://github.com/vaaralav/dangers/commits?author=kentcdodds "Code") [📖](https://github.com/vaaralav/dangers/commits?author=kentcdodds "Documentation") [🚇](#infra-kentcdodds "Infrastructure (Hosting, Build-Tools, etc)") [⚠️](https://github.com/vaaralav/dangers/commits?author=kentcdodds "Tests") | [<img src="https://avatars2.githubusercontent.com/u/22251956?v=4" width="100px;"/><br /><sub><b>Suhas Karanth</b></sub>](https://github.com/sudo-suhas)<br />[💻](https://github.com/vaaralav/dangers/commits?author=sudo-suhas "Code") [🐛](https://github.com/vaaralav/dangers/issues?q=author%3Asudo-suhas "Bug reports") [⚠️](https://github.com/vaaralav/dangers/commits?author=sudo-suhas "Tests") | [<img src="https://avatars0.githubusercontent.com/u/1402095?v=4" width="100px;"/><br /><sub><b>Matt Parrish</b></sub>](https://github.com/pbomb)<br />[💻](https://github.com/vaaralav/dangers/commits?author=pbomb "Code") [⚠️](https://github.com/vaaralav/dangers/commits?author=pbomb "Tests") | [<img src="https://avatars3.githubusercontent.com/u/1319157?v=4" width="100px;"/><br /><sub><b>Mateus</b></sub>](https://github.com/mateuscb)<br />[💻](https://github.com/vaaralav/dangers/commits?author=mateuscb "Code") [⚠️](https://github.com/vaaralav/dangers/commits?author=mateuscb "Tests") | [<img src="https://avatars1.githubusercontent.com/u/2344137?v=4" width="100px;"/><br /><sub><b>Macklin Underdown</b></sub>](http://macklin.underdown.me)<br />[💻](https://github.com/vaaralav/dangers/commits?author=macklinu "Code") [⚠️](https://github.com/vaaralav/dangers/commits?author=macklinu "Tests") | [<img src="https://avatars0.githubusercontent.com/u/8571541?v=4" width="100px;"/><br /><sub><b>Ville Vaarala</b></sub>](https://vaaralav.com)<br />[📖](https://github.com/vaaralav/dangers/commits?author=vaaralav "Documentation") [💻](https://github.com/vaaralav/dangers/commits?author=vaaralav "Code") |
| :---: | :---: | :---: | :---: | :---: | :---: |

<!-- ALL-CONTRIBUTORS-LIST:END -->

This project follows the [all-contributors][all-contributors] specification.
Contributions of any kind welcome!

## LICENSE

MIT

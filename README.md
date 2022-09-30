# Cypress Starter Kit

A starter kit extended from rightsaidjames/cypress-starter-kit

## Getting Started

### Install NVM

To **install** or **update** nvm, you should run the [install script][2]. To do that, you may either download and run the script manually, or use the following cURL or Wget command:
```sh
curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.39.1/install.sh | bash
```
```sh
wget -qO- https://raw.githubusercontent.com/nvm-sh/nvm/v0.39.1/install.sh | bash
```

Running either of the above commands downloads a script and runs it. The script clones the nvm repository to `~/.nvm`, and attempts to add the source lines from the snippet below to the correct profile file (`~/.bash_profile`, `~/.zshrc`, `~/.profile`, or `~/.bashrc`).

<a id="profile_snippet"></a>
```sh
export NVM_DIR="$([ -z "${XDG_CONFIG_HOME-}" ] && printf %s "${HOME}/.nvm" || printf %s "${XDG_CONFIG_HOME}/nvm")"
[ -s "$NVM_DIR/nvm.sh" ] && \. "$NVM_DIR/nvm.sh" # This loads nvm
```

## Install dependencies and run locally

- Copy the `cypress.config.js` file into your project's root directory.
- Copy over the `cypress/` directory
  - If you decide to put the `cypress/` directory in a subfolder, adjust the relevant `cypress.config.js` values accordingly. You will also need to adjust the relative paths (e.g. `../node_modules`) in the `tsconfig.json` file.
- Browse to your project's root directory from the command line, then run `npx cypress open` to download Cypress to your machine and start the UI Test Runner. 
  - If you don't intend to use [Component Testing](https://docs.cypress.io/guides/component-testing/writing-your-first-component-test), you can jump straight [End-to-end testing mode](https://docs.cypress.io/guides/end-to-end-testing/writing-your-first-end-to-end-test) by setting the `--e2e` and `--browser` command line options, e.g. `npx cypress open --e2e --browser chrome`
  - Select `sample-test.cy.js` from the list of tests, then watch them run and (hopefully!) pass.
  - You can stop the UI Test Runner simply by closing its window(s), or by typing `Ctrl + C` at the command line.
- Update the `baseUrl` in `cypress.json` to your project's local/integration environment, then start [writing tests](https://docs.cypress.io/guides/getting-started/writing-your-first-test.html)!
  - Tests that are currently open in the UI Test Runner will automatically restart whenever a relevant file is modified, so you can see your tests pass or fail in real time.
- You can also kick off a headless test run of the Sample test suite using `npx cypress run`.

### Handling user credentials

When working with user credentials, even on a non-production site, you should avoid committing them to Git/GitHub. Instead, you can distribute an `auth.json.dist` file with sensitive data removed, then share the necessary info via a password manager or another form of secure data store. Users can make a copy of the .dist file, rename it to `auth.json` then fill in the required values.

To prevent yourself and others from committing sensitive data, you can add the relevant fixture files to your `.gitignore` file, like so:
```
cypress/fixtures/auth.json
```

Sensitive data can also be populated using [Environment Variables](https://docs.cypress.io/guides/guides/environment-variables.html), then accessed using [Cypress.env()](https://docs.cypress.io/api/cypress-api/env.html#Syntax).

### Adding Cypress to your project

To permanently add Cypress to a project that is already using npm or yarn, run _one_ of the following commands to install Cypress as a development dependency:

```
npm install cypress --save-dev
yarn add cypress -D
```

If the project does not have a package.json, you will first need to run `npm init` or `yarn init`.

From there, add the following to the scripts section of your `package.json`:
```
"cypress": "cypress run --e2e",
"cypress:open": "cypress open --e2e"
```

This will allow you to launch the UI Test Runner using `npm run cypress:open` and the CLI Test Runner using `npm run cypress` (or their Yarn equivalents).

When a new version of Cypress becomes available, you can update it within your repo using `npm install --save-dev cypress@x.y.z` or `yarn upgrade cypress@x.y.z`, where `x.y.z` is the version of Cypress (e.g. `6.8.0`) you want to install.

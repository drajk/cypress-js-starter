# Cypress Starter Kit

A starter kit extended from rightsaidjames/cypress-starter-kit

## Getting Started

### Install NVM (Node version manager)

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

Use correct node version locally.
```
nvm use
```

Install dependencies
```
yarn
```

Run tests
```
yarn start
```

### Handling user credentials

When working with user credentials, even on a non-production site, you should avoid committing them to Git/GitHub. Instead, you can distribute an `auth.json.dist` file with sensitive data removed, then share the necessary info via a password manager or another form of secure data store. Users can make a copy of the .dist file, rename it to `auth.json` then fill in the required values.

To prevent yourself and others from committing sensitive data, you can add the relevant fixture files to your `.gitignore` file, like so:
```
cypress/fixtures/auth.json
```

Sensitive data can also be populated using [Environment Variables](https://docs.cypress.io/guides/guides/environment-variables.html), then accessed using [Cypress.env()](https://docs.cypress.io/api/cypress-api/env.html#Syntax).

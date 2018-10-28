# Kommunity Back-End Server
Kommunity is an online app for joining, starting and building online communities.<br/>
This repository is the back-end server for kommunity app. 

Check product [documentation](https://docs.google.com/document/d/1P9znOKfQIHDP3BVS5ptvFgzSLmL0vo4WTAZrcKatFBA) for details.

# Instructions
1. Fork this repo
2. Click on `Clone or download` button and copy url
3. Clone your own fork
```bash
# Replace MYFORK_URL with what you just copied
git clone MYFORK_URL
```

## Install dependencies
Locate this repository's folder on your terminal and install dependencies.
``` bash
npm install
npm install -g nodemon
npm i -g babel-cli
```

## Install mysql
Download and install MySQL Community Server

Installer: https://dev.mysql.com/downloads/mysql/

## Install NVM (node version manager)
Windows: https://github.com/coreybutler/nvm-windows/releases

Mac: https://github.com/creationix/nvm/blob/master/README.md#installation

- nvm install 8.11.4
- nvm use 8.11.4

### Fix NVM

Windows? do:
- open node_modules/pre-push/index.js
- find `if (!this.npm)`
- right after if block, put:
`this.npm += ".cmd";`

## Import sample database and data

Import current version:
```bash
npm run import-db
```

Or Import specific version:
```bash
npm run import-db v0.0
```

### How to fix import-db path issue on mac environment

```bash
/usr/local/mysql/bin/mysql -u root -p < scripts/db/v0.0/kommunity.app.db.v0.0.sql
```
For details check this [link.](https://stackoverflow.com/questions/10577374/mysql-command-not-found-in-os-x-10-7)

### Database versions:
v0.0 (Current)

## Run Back-End Server
```bash
npm run start
```

## Git instructions for developing new features
Locate this repository's folder on your terminal.

```bash
# Create a new feature branch
git checkout -b BRANCH_NAME

# Make changes in the code base ...

# Check for formatting
npm run lint

# Check for flow types
npm run flow

# Run unit tests
npm run test

# If all checks (lint, flow, test) are passing, add updated files to staging
git add src/server.js

# Commit your changes
git commit -m "added new auth method"

# When you are ready to create a PR, push your changes to your fork
git push -u my-fork BRANCH_NAME

# Go to github, open your forked repository page
# Click on `New pull request` button
# Make sure you see base: dev, and original repo name on the left
#   And BRANCH_NAME, and your fork's name on the right.
# Hit `Create pull request` button

# Once PR is created, make sure Travis build passes. Then ask other developers to review your code.
```

## Adding new flow type definition
In order to avoid flow type errors, you can fetch definitions for popular modules from flow-typed.

```bash
npm run flow-typed-add express@4
```
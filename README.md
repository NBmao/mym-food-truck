# mym-food-truck

This project is for engineering-assessment of https://github.com/peck/engineering-assessment

## Set up dev environment

Install following tools:

-   Git: https://git-scm.com/download
-   EditorConfig: http://editorconfig.org
-   ESLint: https://eslint.org/docs/user-guide/getting-started
-   node and npm: https://nodejs.org/

Get the repo cloned to local using Git.

#### Up and run

```
* Install dependencies managed by tnpm

```

tnpm install

NOTE: \* If you met any package install issue on Windows caused by leaking VSBuild tool, please install MS Vistual Studio.
Or try below command to istall the build dependences.
npm install --global --production windows-build-tools

    * A 'clean' install may help to solve the package version issues. The steps are:
      1. Remove node_modules folder
      2. tnpm install

```

* start localhost development

```

tnpm run develop

NOTE:
_ If you met perssion issue (mostly on Windows), opening your terminal with admin user or using sudo on Mac/Linux should fix.
_ For eVR windows environment, you need to set the environment "APP_TYPE" to enable eVR plugins, replace above command to "npm run evr-develop:win"

```

* Open Floorplan at http://localhost:8000 for global and http://localhost:8000?brand=ezhome for EasyHome China

#### Work in homestyler-tools-core repo
If you are editing goog classes you only need to refresh browser to have your changes take effect.
But if you are editing ES6 code，you will need to build core you should keep 'watching' this file to have your changes take effect in real-time.
Just open an console an cd into homestyler-tools-core folder and run:
```

webpack --debug --watch

```
or
```

tnpm run watch

```

## Build

* Node, Java and Python is required in build scripts:
    * node and npm: https://nodejs.org/
        * Mac: it's better to install node by brew on OS X
        * Linux/Unix: you can use nvm to do the verison management: https://github.com/creationix/nvm
    * Python 2:
        http://www.python.org/download/releases/2.7/

## Test
* trun `npm test` to execute test scripts
* local build - for setting up a local QA testing environment with release build
    * use `npm run build` to make sure latest code has been built
    * use `npm run evr-develop:win` for eVR build
    * use `npm run start-local-build` to start the local build
    * open the local build at http://[your ip address]:8001/?brand=ezhome

## Build development libraries
* In order to support debugging librarise in nodejs environment, we provide a way to build an unminified library with below steps:
    * 1. cd homestyler-tools-core folder and run 'npm run build-dev'
    * 2. cd homestyler-tools-web folder and run 'npm run build-publish-libraries-dev'
    * 3. The development library will be generated at: ./homestyler-tools-web/platform/publish/dist/sercicefunction.js
    * 4. Copy this file to you own project under path: ./Users/lory/repo/dawn/node_modules/@juran/homestyler-web-libraries/dist/sercicefunction.js

* NOTE：
    * 1. The development libraries are not compressed and minified souce code, DON'T publish it to npm server.
    * 2. Only for those who have access right to Core repo can build this library locally. And these libraries are only for local debug purpose, DON'T pass them to any other people or 3rd parties.

## Tips && FAQ
### Folder structure
* `build/` build & deploy scripts
* `node_modules/` npm managed folder for installing dependency packages
* `platform/` platform specific applications
    * `ios/` iOS app prototype
    * `node-data-service/` data service node app, a sandbox service plugin
* `test/` test cases and test config
* `web/` main web app source code
    * `lib/` 3rd party libs that can't be managed by npm
    * `partner/` customizations for partner
    * `plugin/` plugins that implements functional workflow
    * `ui/` ui widgets
    * `viewer/` content 3d viewer app

### API Doc
https://git.autodesk.com/pages/HBP/homestyler-tools-web/doc/api/

[Read more about debugging tips](doc/tips.md)
```


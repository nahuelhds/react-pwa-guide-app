# react-pwa-guide-kit-v2

**Important:** This repo is a fork from [codebusking/react-pwa-guide-app](https://github.com/codebusking/react-pwa-guide-app) and it updates the main packages to their latest versions and add some others:
- **Updated** Webpack 4 and all the plugins used in the config.
- **Updated** to Babel 7
- **Added** [React Hot Loader](https://github.com/gaearon/react-hot-loader) for realtime coding experience
- **Updated** to React 16.5 & PropTypes
- **Removed** React Tap Event Plugin as it is deprecated since React 16.4. See [https://github.com/zilverline/react-tap-event-plugin](https://github.com/zilverline/react-tap-event-plugin)
- **Added** [Loadable Component](https://github.com/smooth-code/loadable-components) for code splitting and in replacement of the `asyncComponent` method.
- **Updated** to Material UI 3.3.0
- **Updated** to Firebase 5.5.4
- **Added** [Cloud Firestore](https://firebase.google.com/docs/firestore/?hl=es-419) for the database implementation in the *Users* component.

A pull request has been created in order to integrate these changes to the original repo.

> This is a guide kit is designed to show how to make a Progressive Web App(PWA) and PWA features in React.js development environments. Customized and opinionated tools and build process are optimized to achive high-performed web application which is audited by strict auditor, [Lighthouse](https://github.com/GoogleChrome/lighthouse). Moreover, this guide kit is also backed by Firebase for hosting, realtime database (cloud firestore), and also push notification.

# Demo

[Demo](https://react-pwa-hello-world-v2.firebaseapp.com/#/) is working on firebase hosting. Please take a look.

# Features

- **Material Design and AppShell**: Responsive, fit any form factor, desktop but the first is mobile. AppShell architecture implemented wearing material design got bressed by [material-ui.com](https://material-ui.com)
- **ES6 via Babel**: You can use ES6 feature with same babel-preset to [create-react-app](https://github.com/facebookincubator/create-react-app) and dynamic module importing
- **Webpack**
  - **Remarkable configurations**: Webpack configuration file has been written in configurable, optimzied and easy settings
  - **Developing Progressive Web App**: You can check them of optimized bundling for PWA including code-splitting, multiple chunk and [preload](https://www.npmjs.com/package/preload-webpack-plugin). As developing, reloading changes instantly by webpack-dev-server, also it is working well with [service worker](https://github.com/ragingwind/sw-precache-webpack-dev-plugin)
- **HTTPS**: Deploying to Firebase Hosting to run perfectly on HTTPS with PWA features
- **Web Push**: Web Push demo also is branded at this app by Firebase Push Messaging
- **Service Worker**: Generating service worker scripts is completly intergrated in build process with Webpack 2 and plugins
- **Web Manifest**: Have a look how to installable webapp work by Web Manifest
- **Realtime Database**: We featured firebase to show PWA how to work with fetched data and cached data via service worker
- **Server Side Rendering**: Deprecated in favour of using code splitting and react-router 4 ~~Presenting intial page in short time is an important issue. This guide kit includes
simple server side code for demonstration. Buidling PWA for Server Side Rendering version landed You can take a look what is different between both of versions~~
- **React Lite Support**: To achieve minimal vundle size at initializing time of the app, we support for building with react-lite. Simple, you can get another version of app running on `react-lite` if you could add the additional argument on build command when you build `-- --env.lite`

# Getting Started

## Setup

To use filrebase cli tool, you must setup firelbase cli and then logged into firebase by `firebase login`. To do this please refer to [firebase cli guide](https://firebase.google.com/docs/cli/). And then you need to create a new project on firebase and get the intialize codes from firebase, which are API_KEY, MESSAGING_SENDER_ID, DATABASE_URL, to save at .env. If you're not familiar with a brand new filrebase? you can have a look for [official guide](https://firebase.google.com/docs/web/setup)

```sh
# install dependencies
yarn install

# firebase init, input with following answers
#   > select `firestore and hosting only`
#   > select `your project` or `create one`
#   > input `build` as your public directory, which is default build path
#   > answer `no` for configuration as a single-page app
#   > no overwrite any files in source
firebase init

# copy into .env and update values in the file with the intialize value you get from firebase in compliance with loading env as you build
cp .env.example .env
```

## Build

We support three versions of build, production, development(debug) and ssr. All of build files will be in `./build`

```sh
# build in production
npm run build

# build in debug
npm run build:debug
```

## Run PWA on Server

```sh
# starting app by webpack-dev-server
npm start
```

## Deployment when you ready for production

You need to check that configuration again. You must have a project on firebase, this project have the suitable settings for firebase generated by fireblase cli and .env file must be exist with the initialize code from firebase

```sh
# make sure that run `yarn build` before you try to deploy the app to firebase
npm run deploy
```

## Testing Firebase Cloud Messaging for Push

This guide-kit use Push Messaging built on top of Firebase Cloud Messaging. `Notification` page will show you peer token to send push message to current opened tab. To do this, [`fcm-cli`](https://github.com/ragingwind/fcm-cli) is a really simple and powerful tool for testing FCM on terminal. [This video will cover how to deal with fcm-cli and FCM](https://goo.gl/Jx4poC) (*Korean*)

### Local Testing
Registering a Service Worker without a trusted SSL Connection will fail with:  [Failed to register a ServiceWorker: An SSL certificate error occurred when fetching the script](http://goo.gl/lq4gCo).

`webpack-dev-server --https` will use a self signed certificate, which is not trusted.
Using Google Chrome, use the following flag to ignore `--unsafely-treat-insecure-origin-as-secure=https://0.0.0.0:8080`

# Lighthouse Audit Result
Audit result is [here](https://gist.github.com/ragingwind/6bff6223e98e0a5a54cf46077c4f9336), you can review the result with Lighthouse [viewer](https://googlechrome.github.io/lighthouse/viewer/)

![](https://cloud.githubusercontent.com/assets/124117/25270127/6c90d66c-26ba-11e7-962e-f7356c82b3f0.png)

# License

MIT @CODEBUSKING

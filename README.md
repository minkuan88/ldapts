LDAPts
======

[![NPM version](https://img.shields.io/npm/v/react-native-ldapts.svg?style=flat)](https://npmjs.org/package/react-native-ldapts)
[![node version](https://img.shields.io/node/v/react-native-ldapts.svg?style=flat)](https://nodejs.org)
[![Known Vulnerabilities](https://snyk.io/test/npm/react-native-ldapts/badge.svg)](https://snyk.io/test/npm/react-native-ldapts)

LDAP client for React Native based on [LDAPts](https://github.com/ldapts/ldapts).

## Note
This is forked from [LDAPts](https://github.com/ldapts/ldapts) with some
dependency changes to allow usage in React Native

It requires certain react native compatible libraries to be installed in order for this to work.

### Required dependencies
1. [react-native-tcp](https://github.com/PeelTechnologies/react-native-tcp)
2. [node-libs-react-native](https://www.npmjs.com/package/node-libs-react-native#usage)
3. [react-native-get-random-values](https://github.com/LinusU/react-native-get-random-values)

```shell
npm install --save react-native-tcp node-libs-react-native react-native-get-random-values
```

Add the following into `metro.config.js`
```javascript
// metro.config.js
module.exports = {
  resolver: {
    extraNodeModules: require('node-libs-react-native'),
  },
};
```

Add the following to the top of the entry `index.js` for react native
```javascript
import 'node-libs-react-native/globals';
import 'react-native-get-random-values';
// ...
import App from './App.ts';
```

### Known Issues
- There seems to be a duplicated dependency issue with the react-native-tcp library that was used on iOS where multiple TcpSockets is getting linked.

  - In order to get it to work, 
    1. Go to xcode
    2. into project navigator, click on Pods folder
    3. then select TcpSockets in targets
    4. Go to Build Phases > Compile sources
    5. remove reference to CocoaAsyncSocket

- TLS doesn't work now as I couldn't find any react-native compatible tls library to swap with. 

## Usage
See [LDAPts README](https://github.com/ldapts/ldapts#readme) on how to use the libaray

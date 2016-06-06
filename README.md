# Demo for an odd turf.js bug
## Bug description
The part that led me down this direction is a desire to use [turfjs](http://turfjs.org), along with [react-native-maps](https://github.com/lelandrichardson/react-native-maps) to do some simple spatial analysis kinds of things.

However, turfjs depends on [jsts](https://github.com/bjornharrtell/jsts) which seems to depend on [babel.js](https://babeljs.io)' ES2015, and some sort of presets associated with that.

In the searching I've been doing, it seems to be the case that babel creates a set of assumptions (reflected through presets?) that do not carry over into react-native, and jsts needs builds on top of babel. When you include the `babel-preset-es2015` settings, there seems to be some sort of override of the `typeof()` function that doesn't translate into react-native properly.

## Bug replication
### Setting up the environment
```
npm install
```

### Running the project

To see the first stage bug, run this like you would any other react-native application.

```
react-native run-ios
```
or
```
react-native run-android
```

To see the second order bug (which may be the root cause), first install babel-preset-es2015
```
npm install babel-preset-es2015
```
then run it like you would any other react-native application (see above).

# LiveReload

## Motivation
While working on a Cordova project recently, I went through the painful steps of constantly having to issue a `cordova run android` after every single little
change I made to the project, which would take a long to deploy to the emulator/device and slow down my development.

Web developers have been using different flavors of 'LiveReload' to palliate this difficulty.
Some part of the cordova community also relies on the same (for example, ionic). 

LiveReload watches for changes in your files, and automatically refreshes the browser, saving you from having to manually refresh the browser/webview yourself.

This improves developer's workflow, and saves a lot of time.

LiveReload is such an ingrained part of the modern developer's development process that I thought it should be made part of the core of Cordova, thus improving discoverability and making it readily available to developers who wish to use it.

## Two Approaches
So, I've thrown together a prototype version so that anyone could try it out and give feedback:
[cordova livereload in core](https://github.com/MSOpenTech/cordova-lib/commits/LiveReload).

Also, Parashu has put together a different implementation : 
[cordova livereload as a plugin] (https://github.com/axemclion/cordova-plugin-browsersync).

## Approach 1 (As part of Cordova Core)
[Link to code](https://github.com/MSOpenTech/cordova-lib/commits/LiveReload)

###Advantages
- Easily discoverable as it's in cordova-lib
- Easily available: nothing to do except add a flag : 'cordova run android --liverelad'
- Dependencies only get installed on user needing the livereload features (Lazy install & require)
- Support for multiple platforms. 'cordova run android windows --livereload'
- Support for UI sync across multiple platforms (scrolls, typing, etc...)

###Disadvantages
- Code is part of Cordova core, so can be construed as pushing Browser-Sync based livereload against other implementations (e.g: livereload package)

## Approach 2 (As a Cordova Plugin)
[Link to code] (https://github.com/axemclion/cordova-plugin-browsersync)

###Advantages
- More modular as code is in a plugin
- Can integrate well with third-party workflows (gulp, grunt, etc...)
- 

###Disadvantages

##How to run the prototypes

###How to run the cordova core-based implementation
- Grab the branch from here : [https://github.com/MSOpenTech/cordova-lib/commits/LiveReload](https://github.com/MSOpenTech/cordova-lib/commits/LiveReload)
- Create a project
- Change the CSP policy to allow the cordova app to connect to websocket servers and allow inline execution of scripts. Replace the default CSP policy in index.html by the following :

```<meta http-equiv="Content-Security-Policy" content="default-src *; style-src * 'unsafe-inline' 'unsafe-eval'; script-src 'self' 'unsafe-inline' 'unsafe-eval' *;">```
 
- From within the project, run : 'cordova run <platform> --livereload'

###How to run the cordova plugin-based implementation

##Please, provide your feedback :
- Do you think it makes sense to bring in LiveReload ?
- Which approaches would you prefer moving forward with ?
- Any other thoughts ?

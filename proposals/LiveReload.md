Problem
Most Web developement workflows today have a quick edit-refresh-preview loop, enabling rapid application development. While Cordova is based on Web technologies, the cordova run step after every little HTML or CSS change is still slow and takes a considerable amount of time to deploy to the emulator or device.
Some livereload-related offerings : https://scotch.io/tutorials/a-quick-guide-to-using-livereload-with-gulp .
Adding the "live reload" capability in Cordova would increase developer efficiency. Note that varieties of LiveReload already in many downstream Cordova distributions.

Prototypes
Browsersync is a popular livereload library that enables refreshing the browser/webview when HTML/CSS/JS or images change, mirrors clicks and scrolls across multiple devices and even does incremental CSS or DOM updates. Here is a prototype implementation that I put together into cordova-lib using BrowserSync and can be started easily using --livereload with the cordova run command : `cordova run android –livereload`
An alternative approach here implements a similar functionality using a Cordova plugin. Here is another plugin that implements livereload using LiveReload instead of browserSyc.

Design Questions
What would be the best approach to add this functionality into Cordova ? 
1. In cordova-lib as prototyped above ? 
2. As a Plugins with hooks that start browserSync? 
3. As a plugin with hooks that uses LiveReload ? 
4. A plugin that is a part of the default template 
5. Any other suggestions

Trying to list the goals from our implementation
1.	Live reload should be discoverable, quick to get started and easy to use. It should be available to all developers in a standard way.
2.	It should integrate well with existing workflows and not come in the way of existing solutions that already have live reload.
3.	It should work for most major platforms. Note that the above examples change the <content src=> to a http:// server. This has a different behavior from the default Cordova app.
4.	Though the above examples depend on browsersync, there are other equally good solutions like LiveReload, Amok, etc. Should we depend on BrowserSync? Or will using a plugin approach give us the flexibility of using alternate solutions

Here’s a link to the corresponding cordova-discuss proposal : https://github.com/omefire/cordova-discuss/commits/LiveReload
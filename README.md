# TiBrowser Widget [![Appcelerator Titanium](http://www-static.appcelerator.com/badges/titanium-git-badge-sq.png)](http://appcelerator.com/titanium/) [![Appcelerator Alloy](http://www-static.appcelerator.com/badges/alloy-git-badge-sq.png)](http://appcelerator.com/alloy/)
This is a widget for the [Alloy](http://projects.appcelerator.com/alloy/docs/Alloy-bootstrap/index.html) MVC framework of [Appcelerator](http://www.appcelerator.com)'s [Titanium](http://www.appcelerator.com/platform) platform.

It provides an in-app browser, with back, forward, and refresh buttons, and options to open the current page in the default browser, or copy the current url into the clipboard.

![iOS](https://raw.githubusercontent.com/jdanthinne/tiBrowser/master/docs/capture-ios.png)
![Android](https://raw.githubusercontent.com/jdanthinne/tiBrowser/master/docs/capture-android.png)

## Get it [![gitTio](http://gitt.io/badge.png)](http://gitt.io/component/be.grincheux.tiBrowser)
Download this repository and consult the [Alloy Documentation](http://docs.appcelerator.com/titanium/latest/#!/guide/Alloy_XML_Markup-section-35621528_AlloyXMLMarkup-ImportingWidgets) on how to install it, or simply use the [gitTio CLI](http://gitt.io/cli):
`$ gittio install be.grincheux.tiBrowser`

## Usage
#### In a view
```xml
<Alloy>
  <Widget id="browser" src="be.grincheux.tiBrowser" url="http://www.google.com" color="#f00" tintColor="#fff" autoOpen="true" />
</Alloy>
```
If *autoOpen* is omitted or *false*, don't forget to add the following code to your controller:
```javascript
$.browser.open();
```
#### In a controller
```javascript
Alloy.createWidget("be.grincheux.tiBrowser", {
  url: "http://google.com",
  color: Alloy.Globals.primary,
  tintColor: "#fff",
  autoOpen: true
});
```
Or you can set options after creating the widget if needed.
```javascript
var browser = Alloy.createWidget("be.grincheux.tiBrowser");
browser.setUrl("http://google.com");
browser.setColor("#f00");
browser.setTintColor("#fff");
browser.open();
```
## Arguments
#### url (*string*)
The url to be loaded in the browser.
#### data (*object*)
The data object with its properties to be read on your local HTML file.
Your HTML must have a JavaScript function called `loadExternalData` which receives the data object as parameter.
```
<html>
<head>
    <script type="text/javascript">
        function loadExternalData(data) {
            // At this point, data is a String. We need to parse to convert to an Object
            var obj = JSON.parse(data);
            alert(obj.key + ' - ' + obj.whatever);
        }
    </script>
</head>
</html>
```
#### color (*string*)
The main color of the browser (background color of the title bar).
#### tintColor (*string*)
The tint color of the title bar.
#### toolbarTintColor (*string*)
The tint color of the toolbar.
#### autoOpen (*bool*)
If set to *true*, the window will open on widget creation. Otherwise, you have to use the *open()* methods.
## Available methods
#### open()
Opens the browser window.
#### setUrl (*string* url)
Sets the url for the loaded in the webview.
#### setColor (*string* color) - iOS
Sets the main color of the browser (background color of the title bar).
#### setTitleColor (*string* color) - iOS
Sets the color of the title bar.
#### setTintColor (*string* color) - iOS
Sets the tint color of the title bar.
#### setToolbarTintColor (*string* color) - iOS
Sets the tint color of the toolbar.

## Changelog
* 1.3.6: Add functionality to send parameter to a local HTML file
* 1.3.5: Added *setToolbarTintColor* method
* 1.3.4: Fix iOS icons when launching in landscape orientation
* 1.3.3: Handle orientation changes
* 1.3.2: Added *setTitleColor* method
* 1.3.1: Fixed iOS/Android differences
* 1.3: Fixed images path
* 1.2: Added *autoOpen* argument
* 1.1: Added public methods
* 1.0: Inital commit

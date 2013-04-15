Icenium-iOS-Enterprise-Distribution
===================================

This is a short guide outlining the steps to publish In-House iOS apps if built in Icenium. I could not find any definitive documentation how on to do this (generating the appropriate .plist file was the problem).
This tutorial assumes you already have your iOS Development Program Enterprise account, and a server to host it on.


1. Build your app: Follow the steps already outlined in [Icenium's docs](http://docs.icenium.com/working-with-devices/apple-ios-devices/how-to-build-your-app-for-appstore). This will leave you with an .ipa file.

2. Move your .ipa file to your server
    
3. Create your .plist file: Usually this would be created in XCode after building the app. Since we're using Icenium, we have to manually create the plist file and enter in the values. Create a new file with the extension .plist in the same directory as your .ipa. Paste [the following](https://gist.github.com/hramos/774468) into that file. Edit the appropriate values.

4. Create a link to your .plist file
```
<a href="itms-services://?action=download-manifest&url=http://www.myserver.com/myapps/manifest.plist">
  Download MyApp
</a>
```

5. If you're hosting on IIS, you'll need to set the MIME types:
```
.ipa    : application/octet-stream
.plist  : text/xml
```

6. Your app is now ready to download from a phone's browser.

Additional Information:

* [Distributing Enterprise Apps for iOS Devices] (https://developer.apple.com/library/ios/#featuredarticles/FA_Wireless_Enterprise_App_Distribution/Introduction/Introduction.html)

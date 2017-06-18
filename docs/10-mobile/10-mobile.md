## Lab 10: Mobile App (Phonegap)

1. In this Lab we will build, customize and install an Android app that uses the Cordova In-App Browser to provide a rich UI. Download and unzip topseed-mobile-master.zip from <a href='https://github.com/topseed/topseed-mobile' target='_blank'>here</a> to your location of choice on your developer machine. Open the project in VS Code. Download and install the Phonegap Desktop App from <a href='https://github.com/phonegap/phonegap-app-desktop/releases' target='_blank'>here</a>. Run the app, add the '/topseed-mobile' folder as a Project, and click the '>' button. A message 'Server is running on ...' should come up. Click on the URL to open the App in a browser. The app is configured to show a splash screen and then display the content from https://m.appthings.io. 

2. Let us customize the app for your needs. As you do this, Phonegap Desktop App will watch for changes in the /www folder of the project and refresh the browser view on each change.
Replacing the logo used on the splash screen (at /www/css/index.css) and the icons used by the phone operating system with your own (see /config.xml 'icon' values) is a labor of love and we will skip over it here.
However, we will make the app display the content you published to the CDN in Lab 3. 
In /www/js/index.js, replace the URL following 'window.open' with the homepage URL of the helloworld app you deployed in Lab 3, i.e. your equivalent of 'https://staging.mydomain.com/page/one/index.html'. If you only deployed to the CDN, use your equivalent of https://1234567890.rsc.cdn77.org/page/one/index.html'. If you only deployed to Zeit.co, use your equivalent of  'https://demos-oosnsyzlphl.now.sh/page/one/index.html'. If you never deployed, you can use the published version of this tutorial at 'https://docs.topseed.io/tutorial/0-agenda/index.html'.

3. To allow the in-app browser to navigate to the newly configured URL, in /config.xml, replace 'm.appthings.io'  \<allow-navigation href="https://m.appthings.io/*" /\> with your equivalent. The app should now display your site at the 
Phonegap Desktop App Server URL.

4. To install the customized app on an Android phone, create an account and login at <a href='https://build.phonegap.com' target='_blank'>https://build.phonegap.com</a>. You will be prompted to create an Adobe ID if you don't have one. 
Create a zip file of the contents of the project folder /topseed-mobile.
On the <a href='https://build.phonegap.com/apps' target='_blank'>'Apps' tab </a>, click the '+ new app' button and upload the zip file. The site will take a few moments to build the app. Meanwhile, also log into <a href='https://build.phonegap.com' target='_blank'>https://build.phonegap.com</a> on your mobile phone. Once the build has completed, follow the prompts to download, install and run the version for your phone's operating system (we assume Android here). 

5. See <a href='http://docs.phonegap.com/' target='_blank'>http://docs.phonegap.com/</a> for further information about phonegap, and details how to deploy to Apple iOS,and how your app can access phone-specific APIs, such as address book, location information etc. We would use a service worker to support offline-browsing as needed.

6. We have used the Cordova In-App Browser to render app content from a CDN. As shown in Lab 6, the app is able to securely obtain data from separate API servers. Because we have ensured that the app has a smooth 'single page application feel' (using topseed-turbo), we were able to deliver a quality mobile app without requiring Android SDK/iOS development skills. 




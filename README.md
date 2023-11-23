# Kivmob-bugs-fixed-
# Allows developers to monetize their Kivy mobile applications using Google AdMob.
  * No need to change internal Android project manifest templates or Java code.
  + Supports banner, interstitial, and rewarded video ads.

For more information, please read the official [documentation](http://kivmob.com/).
## this repo helps you integrate ads in your kivy android app without errors. all bugs fixed just follow the instructions

# for installation 

- Installation

* You can install KivMob with the following command.
```
pip3 install https://github.com/chimenmagoodness/Kivmob-bugs-fixed-/archive/refs/heads/main.zip
```
Note: if you have the previous kivmob package installed, then you have to Uninstall it first before carring out the above command

```
$ mkdir MykivmobAppFolder
you can call it what ever
$ cd MykivmobAppFolder
$ touch main.py
$ buildozer init
```
## You can write your code, but here is an Example
```py
from kivmob import KivMob
from kivy.app import App
from kivy.uix.button import Button

class KivMobApp(App):

      def show_ads(self, *args):
        self.ads.show_banner()
        self.ads.show_interstitial()

    def build(self):
        self.ads = KivMob('Your APPID here') # Looks like this 'ca-app-pub-4268254501946298~4518311108'
        self.ads.new_banner("Your banner ADS ID", top_pos=False) #Looks like this ca-app-pub-4268254501646298/4026871184 you can set the top_pos to True or False
        self.ads.load_interstitial('Your Interstitial ADS ID') #Looks like this ca-app-pub-4268254501946298/8517487982
        self.ads.request_interstitial()
        return Button(text='Show Interstitial',
                      on_release=lambda a:self.show_ads())
                      
    def on_resume(self):
        self.ads.request_interstitial()

KivMobApp().run()
```

## Find and Replace the following in your buildozer.spec file.

```
requirements = python3, kivy, android, jnius, https://github.com/chimenmagoodness/Kivmob-bugs-fixed-/archive/refs/heads/main.zip
...
android.permissions = android.permission.INTERNET, android.permission.ACCESS_NETWORK_STATE
android.api = 33
android.minapi = 21
android.sdk = 33
android.ndk = 25b
android.gradle_dependencies = com.google.firebase:firebase-ads:21.4.0, androidx.appcompat:appcompat:1.6.1, androidx.activity:activity:1.6.1
android.enable_androidx = True
p4a.branch = master
android.meta_data = com.google.android.gms.ads.APPLICATION_ID=Your APPID # Example ca-app-pub-3940256099942544~3347511713
```

## Finally, build and launch the application. 

```
$ buildozer android debug deploy run
```

## Note Using TestIDS might cause compiling errors so use real IDS and you ads will be live












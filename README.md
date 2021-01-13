# To Add Platform

```
ionic capacitor add android
ionic capacitor add ios
```

# Installing / Updating Plugins

After installing plugin npx cap sync

When, will updating the plugins npx cap update

https://capacitorjs.com/docs/cordova/using-cordova-plugins

# Hot Reload Configuration

Ionic memiliki antarmuka hot reload untuk semua framework yang tersedai seperti angular,react & vue
`npm install -g @ionic/cli native-run`

Selanjutnya, gunakan script dibawah untuk memulai proses Live Reload:

```
ionic cap run android -l --external
ionic cap run ios -l --external
```

# Generate Icon & Splashscreen Files

npm i -g cordova-res

pastikan sudah bkin folder resources dan berisi icon.png 1024x1024 splash.png 2732x2732

kemudian untuk generate file nya cordova-res ios --skip-config --copy && cordova-res android --skip-config --copy

# Build Production

ionic capacitor build android/ios

end then

## Android

https://www.joshmorony.com/deploying-capacitor-applications-to-android-development-distribution/

## iOS

https://www.joshmorony.com/deploying-capacitor-applications-to-ios-development-distribution/

# App Versioning

So, Capacitor is neat! The android and ios configs are actually committed to source control. To update version number,
simply update the following files:

Android - android/app/build.gradle (you're looking for the versionName variable)<br>
iOS - ios/App/App/Info.plist \*(you're looking for the CFBundleShortVersionString key)

# Notes

## Android

- Download File dengan capacitor sudah menambahkan <access origin="*" /> secara default tapi tidak kompabilitas dengan
  cordova untuk membuatnya kompetibel kemudian untuk simpan file android gunakan File.externalRootDirectory

- Untuk android 9 perlu edit AndroidManifest di tag
  <application>
  android:requestLegacyExternalStorage="true"

- Lakukan installasi dibawah untuk mengatasi url cors agar di izinkan meng akses/download/upload file domain luar

```
npm install cordova-plugin-whitelist
npx cap sync
``` 

## iOS

- Download file untuk ios 11 disimpan di File.applicationStorageDirectory

## Desktop

- Sidebar secara default ionic tidak menyediaka fungsionalitas show/hide sidebar untuk desktop, baca lebih lanjut
  mengenai custom toggle menu sidebar untuk sidebar dekstop di src/app/views/components/atoms/Menu.vue
  readmore: https://github.com/ionic-team/ionic-framework/issues/18692

- Sidebar Size (width), dapat di atur di custom.css
- Page transition untuk desktop saya disabled, bisa dilihat di src/app/views/layouts/Admin.vue
  ```
  <ion-router-outlet id="main-content" :animated="!!Capacitor.isNative"></ion-router-outlet>
  ```
  Jika tidak native alias web maka dia akan men disable animasi page 
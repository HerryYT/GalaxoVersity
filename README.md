# GalaxoVersity

Galaxy Life was a space-themed real-time strategy castle defense game developed by Ubisoft. However, it was shut down in March 2016 and isn't playable anymore.

GalaxoVersity aims to code a working community server for Galaxy Life: Pocket Adventures (the mobile version of Galaxy Life) and to revive the game again eventually.

To avoid any copyright problems, we are going to use the original client (the app) without any modifications and code the server completely from scratch. However to do that, we'll first have to start by reverse engineering the Galaxy Life: Pocket Adventures app, to figure out how it communicated with the servers. The server will be written in Java.

If you have any knowledge in Java/Android reverse engineering or programming, in general, you're welcome to help. Right now we're just collecting all the information we can get about the inner workings of the client, so just make a pull request where you add anything you found out.

The latest version of GL:PA is 1.7.0, so we are going to use that. I won't upload it for obvious copyright reasons; however, it's easy to find on Google. To confirm you've downloaded the correct file you can check it's checksum:
* MD5: 8a038b758d66fba205c4aec2e7315332
* SHA1: f05ca57582ece97856b66589b4c07b0aeb733a40
* SHA256: be3f0b8da0b461da2ba00b596507eb2afb93e8bdfed8093cd8ab5e1609a29f13

There are numerous tools for decompiling Android APKs, one of which is JADX: https://github.com/skylot/jadx It has the advantage that you can directly open the apk without somehow converting it first. However no program is perfect, so we should also try other tools to get the best results.

The entry point of the APK is `iStarNativeActivity` in the package `com.digitalchocolate.igalaxy` where `onCreate(Bundle)` gets called first. We can start reversing there.

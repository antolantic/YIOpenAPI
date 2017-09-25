# YI Open API

Fork of the original YITechnology/YIOpenAPI, without embedded third party tools and a spellchecked Readme.

* All changes are related to getting the Jva examples working on a decent development environment without embedding tools already available on every platform, easily installed and kept up-to-date using a package manager.Just one responsibility less to worry about.

It all compiles and generates APK's, that's it for now (25 September 2017)

## Prerequisites

* Java 8+
* Recent Gradle installation. 

If you can open a CLI, command prompt or terminal and successful execute gradle, means that you have a functional workstation able to execute at least the Java examples.




## Removed

* Embedded Gradle Wrapper. This project expects a recent, stable and standalone Gradle installation. This can be accomplished using a package manager like (Mac)ports for *BSD or macOS, Homebrew also for macOS, Scoop for Windows and finally RPM, APK, *.tar.gz or who knows what for Linux.
  * Binary Windows (only?) helpfile
  * Properly something more

## Changed

* De-compiled the helpfile into a set of normal html files and images.

  * Removed the. cht file and added the html files. (Reason I was unable to enlarge the font size and the text was barely readable on high res screen)

* Spellchecked README.md

## Todo and Status:

* Gradle path is currently hardcoded
* Still must load the APK onto my phone to verify that it works.
* Adding Java unit tests.

## Almost original Yi Open API Readme

This repository contains the libraries, samples and documentation for using the SDK. It also contains the design diagrams, firmware's, reference specs for building hardware systems.

The following is the tree structure of this repository:

* /sdk -- mobile SDK for Android and iOS separately
* /sdk/bin -- firmware and config file for features provided in SDKs to work
* /sdk/java -- Android SDK
* /sdk/java/doc -- documentation
* /sdk/java/libs -- SDK library for building your applications
* /sdk/java/samples -- samples demonstrating the use of SDK APIs
* /sdk/swift -- iOS SDK
* /sdk/swift/doc -- documentation
* /sdk/swift/libs -- SDK library for building your applications
* /sdk/swift/samples -- samples demonstrating the use of SDK APIs
* /spec -- reference specs
* /vr -- documents, design diagrams, and firmwarere's for 6-camera VR rig
* /vr/bin -- firmware's
* /vr/design -- design diagrams (CAD)
* /vr/doc -- documents

## SDK Features

The SDK's provide APIs to support the following 4 areas

* Camera control (start/stop recording video, capture photo, turn on/off viewfinder, etc.)
* Camera settings (datetime, video resolution, photo size, video standard, etc.)
* Camera state (record started/completed, video finder started etc.)
* Media management (browse files stored on media, download, delete file)

## Control VR/360/multi-camera system via Wi-Fi

If you have a VR/360 rig or a multi-cameras system, you can have the cameras connected to a Wi-Fi network or a hotspot, and then control the cameras from your application (built using the YI Open API SDK), by following the steps below: 

1. Update firmware (/sdk/bin/{country code}/firmware.bin)
   * Copy firmware.bin onto a microSD card
   * Start the camera with the microSD card
   * Wait until the sound of starting music

1. Setup config file (/sdk/bin/{country code}/sta.conf)
   * Provide correct SSID and password for accessing the Wi-Fi network or the hotspot
   * Give each camera a different device name
   * Set the correct country code (e.g. CN for China, US for United States etc)
   * Save the changes to sta.conf and copy it onto the microSD card
   * Start the camera with the microSD card

1. turn on Wi-Fi on camera
   * Go to camera settings -> Wi-Fi
   * Pick the Wi-Fi frequency matching to the one broadcasting from your Wi-Fi network or hotspot
   * Turn on Wi-Fi (note that the ON button is green)

1. Tryout YI360Demo sample (/sdk/{java, swift}/samles/YI360Demo)
   * Build and launch the sample app

## Live video

Interested in doing live video in your application using your YI 4K Action Camera? Try out our API for live video support. This is how it works:

1. Update firmware (see above for details).

1. Call buildLiveVideoQRCode to generate an binary array and save it as an image. the information needed would include SSID, password, resolution, bitrate, duration, RTMP URL, and the size of the QR code image in pixels. 

1. Start your YI 4K Action Camera and choose Live mode (at the bottom of the shooting mode selection screen), you will be prompted to provide the QR code to scan.

1. Scan the QR code image using the camera. few seconds later, your live video stream from the camera will be pushed to the RTMP URL that you provided.

## Build your VR camera

YI 4K action cameras are perfect building blocks for VR camera. Its video capturing/encoding spec, image quality, battery life and geometry are all great for VR camera. That's why Google chose to work with YI to use YI 4K Action Camera to build their next version of JUMP VR camera.

Now we have a reference design for you as well. And the following is all what you need:

1. Introduction. Please refer to the doc below:    https://github.com/YITechnology/YIOpenAPI/blob/master/vr/doc/Build%20hardware%20synchronized%20360%20VR%20camera%20with%20YI%204K%20action%20cameras.pdf 

1. Design. Please find the CAD design diagrams here:   https://github.com/YITechnology/YIOpenAPI/tree/master/vr/design

1. Firmware. To be able to control the 6 cameras on the rig and get them working together using a controller camera, you need update the cameras with the firmware's found here:   https://github.com/YITechnology/YIOpenAPI/tree/master/vr/bin

1. Synchronization cable. For the cable that could be used for doing hardware synchronization of all cameras on the rig, please find its reference spec here:  https://github.com/YITechnology/YIOpenAPI/blob/master/spec/Multi-endpoint%20Micro%20USB%20Cable.pdf

## Join the YI Open API community

* Website: https://www.facebook.com/groups/YIOpenAPI/

## Sign up for YI Open API email updates and news

* Website: http://www.yiopen.com/

## License

The YI Open API SDKs are licensed as described in LICENSE. To download and use YI Open API SDKs, you hear by agree YI Technologies, Inc. End User License Agreement (EULA) as described in EULA.

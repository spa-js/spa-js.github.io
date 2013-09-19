---
layout: default
title: Worklight
category: bp
---


# Worklight

## Introduction
I know we don't want Worklight specific guidance here, but I wanted a place to put notes, tips, etc for now.



## Source Code ignore list
The following list of directories and file should be added to SCCS "ignore" lists:

	/apps/{AppName}/android/native/assets/www
	/apps/{AppName}/android/native/bin
	/apps/{AppName}/android/native/gen

	/apps/{AppName}/blackberry/native/www
	/apps/{AppName}/blackberry10/native/build
	/apps/{AppName}/blackberry10/native/www

	/apps/{AppName}/i*/native/build
	/apps/{AppName}/i*/native/cordova
	/apps/{AppName}/i*/native/cordovaLib
	/apps/{AppName}/i*/native/WorklightSDK
	/apps/{AppName}/i*/native/www
	/apps/{AppName}/i*/package

	/apps/{AppName}/windowsphone*/native/Bin
	/apps/{AppName}/windowsphone*/native/obj
	/apps/{AppName}/windowsphone*/native/www

	/bin

The other issue with source code control and Worklight is the "native" folders. Almost 100% of it can (and should) be be ignored. The exceptions are anything you manually change, such as the android_manifest.xml (think thats the name, or close to it). A common practice / issue when sharing projects amongst a team is that things don't work unless you delete the "native" folder, thus losing any custom settings. What I found is that these files you change can (and should!) be copied over to the "nativeResources" directory, so that they get copied into "native" on each build.  WL Development thought this was a slippery slope to recommend, but I still think it has merit.


## Changing Native files
Here is a little known trick if you need to alter any files located under an environment's "native" folder. Copy that file into the "nativeResources" folder first, and edit that file instead. It will get copied into the "native" folder on each build. The reasons this is smart to do, is two-fold. First, its obvious which native files have been customized.  Second, you won't loose the changes should a developer need to wipe out and recreate the native folder, which sometimes needs to be done when importing projects into Eclipse.


## Exporting projects
When exporting a project to a zip archive, DO NOT include the following files and dirs:

	/bin
	/jslib
	/apps/{APP}/android/bin/{APP}.apk
	/apps/{APP}/ipad/package
	/apps/{APP}/iphone/package



## Worklight Image Sizes                                  w x h

	common/images/icon.png                               128 x 128
	common/images/thumbnail.png                           90 x 90
	common/images/favicon.ico                             16 x 16

	----------------------------------------------------------------------------------

	android/native/res/drawable/icon.png                  48 x 48
	android/native/res/drawable/push.png                  25 x 25

	android/native/res/drawable-hdpi/icon.png             72 x 72
	android/native/res/drawable-hdpi/push.png             24 x 38
	android/native/res/drawable-hdpi/settings.png         72 x 72

	android/native/res/drawable-hdpi-v11/push.png         36 x 36

	android/native/res/drawable-ldpi/icon.png             36 x 36
	android/native/res/drawable-ldpi/push.png             12 x 19
	android/native/res/drawable-ldpi/settings.png         36 x 36

	android/native/res/drawable-ldpi-v11/push.png         18 x 18

	android/native/res/drawable-mdpi/icon.png             48 x 48
	android/native/res/drawable-mdpi/push.png             16 x 25
	android/native/res/drawable-mdpi/settings.png         48 x 48

	android/native/res/drawable-mdpi-v11/push.png         24 x 24

	android/native/res/drawable-xhdpi/icon.png             96 x 96

	android/native/res/drawable-xhdpi-v11/push.png         48 x 48

	----------------------------------------------------------------------------------
	[Applies for both ipad and iphone trees]

	ipad/Resources/Default-iphone.png                    320 x 480    (Splash)
	ipad/Resources/Default@2x-iphone.png                 640 x 920    (Splash, retina)
	ipad/Resources/Default-Landscape-ipad.png           1024 x 768
	ipad/Resources/Default-Landscape@2x-ipad.png        2048 x 1496
	ipad/Resources/Default-Portrait-ipad.png             768 x 1024
	ipad/Resources/Default-Portrait@2x-ipad.png         1536 x 2008
	ipad/Resources/Icon.png                               57 x 57
	ipad/Resources/Icon@2x.png                           114 x 114
	ipad/Resources/Icon-72.png                            72 x 72
	ipad/Resources/Icon-72@2x.png                        144 x 144  @ 72dpi
	ipad/Resources/Icon-small.png                         29 x 29
	ipad/Resources/Icon-small-50.png                      50 x 50
	ipad/Resources/ITunesArtwork.png                     512 x 512

	----------------------------------------------------------------------------------

	blackberry/native/icon.png                            80 x 80
	blackberry/native/splash.png                         200 x 38

	----------------------------------------------------------------------------------



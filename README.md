# SGAREnvironment v0.3.8

## ABSTRACT

A pluggable AR (Augmented Reality) environment that can be used by any
[MKAnnotation](http://developer.apple.com/library/ios/documentation/MapKit/Reference/MKAnnotation_Protocol/Reference/Reference.html).

## USAGE

*Note*: this library is being converted to a framework, which should simplify
the following steps somewhat.

1. Run ./build_dist
2. Add /path/to/SGAREnvironment-v*.*.*/Headers to the "Header Search Paths" setting.
3. Add /path/to/SGAREnvironment-v*.*.*/$(PLATFORM_NAME) to "Library Search Paths" setting.
4. Add the following frameworks: OpenGLES, MapKit, CoreLocation, CoreMotion, CoreGraphics, QuartzCore, UIKit, AVFoundation and Foundation.
5. Go to your target's info and add "-all_load -ObjC -l SGAREnvironment" to the "Other Linker Flags" setting under the Build tag. This will inform the linker to load the categories from the static library.
6. Import SGAREnvironment.h in your pre-compiled header file or wherever you plan on accessing the library.

## BUILD REQUIREMENTS

iOS SDK 4.0+ (*3.1 may work, although you'll probably have to create a custom
Build*)

Frameworks:

* CoreLocation
* Foundation
* MapKit
* OpenGLES
* CoreGraphics
* QuartzCore
* UIKit
* AVFoundation
* CoreMotion

## PACKING LIST

### Documentation

All the HTML files generated by HeaderDoc.

* `SGAREnvironment.html` - The table of contents for the entire documentation structure.

### Static Libraries

* `libSGAREnvironment.a` - The static library built for the iPhone Device.
* `libSGAREnvironment-sim.a` - The static library built for the iPhone Simulator.

### Headers

* `SGAnnotationView.h` - Defines a subclass of UIView that displays SGAnnotations in the
SGARView.
* `SGAnnotationViewContainer.h` - Defines a subclass of UIView that contains a set of SGRecordAnnoationViews.
* `SGARNavigationViewController.h` - Defines a subclass of UIImagePickerViewController that displays the SGARView.
* `SGARResponder.h` - Defines the protocol that receives gestures from the SGARView.
* `SGARView.h` - Defines a subclass of UIView that renders SGAnnotations in an augmented reality environment.
* `SGEnvironmentConstants.h` - Defines constants that are used in the augmented reality environment.
* `SGRadar.h` - Defines a subclass of UIView that displays SGAnnotationViews in a radar-ish manner.
* `SGSAREnvironment.h` - Contains all the header files for the augmented reality source files.

### Images

The default images used in the SDK. Feel free to override these with your own.
They aren't very pretty at the moment.

* `SGBluePin.png` - A blue pin.
* `SGBottomInspectorBackground.png` - The bottom image of a non-customizable SGAnnotationView.
* `SGCloseButton.png` - The close button image of a non-customizable SGAnnotationView.
* `SGDefaultContainer.png` - The default SGAnnotationViewContainer image.
* `SGDefaultProfilePicture.png` - The default profile picture used in SGAnnotationView.
* `SGDefaultRadarCurrentLocation.png` - The image that represents the devices current location on the SGRadar.
* `SGDefaultRadarTargetImage.png` - The default target image for SGRecordAnnotation on the SGRadar.
* `SGGlassTargetBackground.png` - The default target background for SGAnnotationView.
* `SGMiddleInspectorBackground.png` - The middle, stretchable portion of a non-customizable SGAnnotationView.
* `SGRedPin.png` - A red pin.
* `SGTopInspectorBackground.png` - The top image of a non-customizable SGAnnotationView.

## CHANGES FROM PREVIOUS VERSIONS

Version 0.3.8

* The prefix file was in charge of importing important frameworks. We need to
move those imports into the header files because the prefix might not be the
same in other projects.

Version 0.3.7

* Fixed an issue where the bearing wasn't being calculated properly for certain
earth quadrants

Version 0.3.6

* Added support for iOS4

Version 0.3.5

* Refactored and polished up some of the code in order to
move the project into a public repository

Version 0.3.4

* Touch events will now return the nearest SGAnnotationView in the
AR environment

Version 0.3.3

* Fixed an issue where touch events weren't being triggered
for SGAnnotationViews within the AR environment

Version 0.3.2

* Prefixed all methods in the SGARResponder with AR.

Version 0.3.1

* Restructured project.

Version 0.3.0

* Upgraded SGLocationService to use version 0.1 of the SimpleGeo API
* Models have been updated to reflect the new GeoJSON format returned
from SimpleGeo queries
* Added a new NSDictionary and NSArray category to help access key specific
to GeoJSON format
* Replaced updateRecordWithGeoJSONDictionary: with updateRecordWithGeoJSONObject:
* Removed userDefinedProperties from SGRecordAnnotation and replaced it with
properties
* Reworked the SGGeoJSONEncoder

Version 0.2.3

* Updated the default container images.
* Updated SGRadar to present target images that are on the border of
the radar.
* Update SGLayerMapView to load more records based on a time interval.
* Added media as a filter type.

Version 0.2.1

* Allow filtering by types in nearby requests.

Version 0.2.0

* Added reverse geocoding.
* Implemented the new SimpleGeo endpoints that allow multiple records to be
added and retrieved.

Version 0.1.9

* SGLayer objects will now update records as they are recieved from the SGLocaitonService.
* SGRecord defines a new property that stores user defined properties.
* SGOAuth objects can be restored from a save point.
* Nearby searchs can be done using a Geohash or a lat/lon coordinate paired with a radius.

Version 0.1.8

* First version.

- - - -

Copyright (c) 2010-2011 SimpleGeo, Inc. All rights reserved.

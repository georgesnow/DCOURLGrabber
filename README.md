# Overview

DCOURLGrabber uses AppleScript to get the URL from most popular browsers.

It monitors when the user switches apps and takes note of which browser was last active. When asked, it then returns the URL from the active tab of that browser.

# Features

* Works with Chrome, Safari, Firefox, Opera & Chrome Canary.
* Easy to extend using AppleScript.

# Status

DCOURLGrabber is used by [Tapetrap](http://www.dangercove.com/tapetrap).

# Setup

## Via [cocoapods](http://cocoapods.org)

Simply add the following line to your Podfile:

    pod 'DCOURLGrabber', :git => 'git@github.com:DangerCove/DCOURLGrabber.git'

Then run `pod install` and you're set.

## Manually

Clone this repo and add both the source files and AppleScripts to your project.

# Usage

## Get URL from specific bundle ID

To simply retrieve the URL from a browser (Chrome) you have running, use the following:

    DCOURLGrabber *grabber = [[DCOURLGrabber alloc] init];
    NSURL *url = [grabber grabURLFromBundleID:@"com.google.Chrome" withError:&grabError];
    if(grabError) {
        NSLog(@"Failed to retrieve URL: %@", grabError);
    } else {
        NSLog(@"Got URL: %@", url.absoluteString);
    }

## Retrieve URL by monitoring app switches

First setup monitoring like this:

    DCOURLGrabber *grabber = [[DCOURLGrabber alloc] init];
    [grabber startMonitoring];

Then simply grab the URL when you want, like so:

    NSURL *url = [grabber grabURLWithError:&grabError];
    if(grabError) {
        NSLog(@"Failed to retrieve URL: %@", grabError);
    } else {
        NSLog(@"Got URL: %@", url.absoluteString);
    }

# Known Issues

* Firefox only supports a rather unelegant way of getting the URL via AppleScript. 

# Contributions and Things to add

Things I'd like to add:

* None at the moment. Maybe more browsers or other apps that work with URLs?

# License

New BSD License, see `LICENSE` for details.

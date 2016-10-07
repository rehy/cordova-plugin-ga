cordova-plugin-ga
=================

Cordova (PhoneGap) 3.0+ Plugin to connect to Google's native Universal Analytics SDK

Prerequisites:
* A Cordova 3.0+ project for iOS, Android and/or Windows Phone 8
* A Mobile App property through the Google Analytics Admin Console
* (Android) Google Play Services SDK installed via [Android SDK Manager](https://developer.android.com/sdk/installing/adding-packages.html)

## Installing

```bash
cordova plugin add cordova-plugin-ga
```

The plugin.xml file will add the Google Analytics SDK files for Android and/or iOS. Make sure to review the Google Analytics [terms](https://www.google.com/analytics/terms/us.html) and [SDK Policy](https://developers.google.com/analytics/devguides/collection/protocol/policy)

## JavaScript Usage
In your 'deviceready' handler, set up your Analytics tracker:

* `window.ga.startTrackerWithId('UA-XXXX-YY')` where UA-XXXX-YY is your Google Analytics Mobile App property

To track a Screen (PageView):
* `window.ga.trackView('Screen Title')`

To track a Screen (PageView) w/ campaign details:
* `window.ga.trackView('Screen Title', 'my-scheme://content/1111?utm_source=google&utm_campaign=my-campaign')`

To track a Screen (PageView) and create a new session:
* `window.ga.trackView('Screen Title', '', true)`

To track an Event:
* `window.ga.trackEvent('Category', 'Action', 'Label', Value)` Label and Value are optional, Value is numeric

To track custom metrics:
* `window.ga.trackMetric('key', Value)` Value is optional

To track an Exception:
* `window.ga.trackException('Description', Fatal)` where Fatal is boolean

To track User Timing (App Speed):
* `window.ga.trackTiming('Category', IntervalInMilliseconds, 'Variable', 'Label')` where IntervalInMilliseconds is numeric

To add a Transaction (Ecommerce)
* `window.ga.addTransaction('ID', 'Affiliation', Revenue, Tax, Shipping, 'Currency Code')` where Revenue, Tax, and Shipping are numeric

To add a Transaction Item (Ecommerce)
* `window.ga.addTransactionItem('ID', 'Name', 'SKU', 'Category', Price, Quantity, 'Currency Code')` where Price and Quantity are numeric

To add a Custom Dimension
* `window.ga.addCustomDimension('Key', 'Value', success, error)`
* Key should be integer index of the dimension i.e. send `1` instead of `dimension1` for the first custom dimension you are tracking.
* e.g. `window.ga.addCustomDimension(1, 'Value', success, error)`

To set a UserId:
* `window.ga.setUserId('my-user-id')`

To set a specific app version:
* `window.ga.setAppVersion('1.33.7')`

To set a anonymize Ip address:
* `window.ga.setAnonymizeIp(true)`

To set Opt-out:
* `window.ga.setOptOut(true)`

To enabling Advertising Features in Google Analytics allows you to take advantage of Remarketing, Demographics & Interests reports, and more:
* `window.ga.setAllowIDFACollection(true)`

To enable verbose logging:
* `window.ga.debugMode()`

To enable/disable automatic reporting of uncaught exceptions
* `window.ga.enableUncaughtExceptionReporting(Enable, success, error)` where Enable is boolean

## Why fork

This is a fork of [cordova-plugin-google-analytics](https://github.com/danwilson/google-analytics-plugin), which was not active maintained before. Since the project is more active, this fork is less relevant now.

### Difference from upstream

- Remove `window.analytics`
- Export `window.GA`, but the newly added `window.ga` is recommended.

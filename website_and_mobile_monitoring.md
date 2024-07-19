# Monitoring websites

## Concepts

Website monitoring, often called End-User Monitoring (EUM), or Real-User Monitoring (RUM), is an important tool to understand digital user experience.

Instana supports website monitoring by analyzing actual browser request times and route loading times. It allows detailed insights into the web browsing experience of users, and deep visibility into application call paths.

Loaded asynchronously into the website, the agent reports its findings to Instana in the form of beacons. This beacon data can be found in an aggregated form within the website dashboards in the Instana UI. The dashboards help explore behavior and speed of websites. They are accessible to a wide audience and to answer the most common questions. More specific questions and hypotheses can be answered by using analyze capabilities.

## Installation

The Instana website monitoring solution works by using a lightweight JavaScript agent, which is embedded into the monitored website. To install the JavaScript agent, access the **Websites** section in the Instana UI to start tracking website performance data. The Instana UI guides you through the installation process.

### Wordpress Monitoring

If you want to use website monitoring with Wordpress, use the [WP Instana EUM plug-in](https://www.ibm.com/links?url=https%3A%2F%2Fwordpress.org%2Fplugins%2Finstana-eum%2F).

For more information about Wordpress, see [What is Wordpress](https://www.ibm.com/topics/wordpress).

### Enable Subresource Integrity (public preview)

Instana website monitoring provides you with the option to enable Subresource Integrity (SRI) for the tracking script. Users can enable or disable SRI for their tracking script and also choose a specific version of the agent with SRI. In the tracking script, the Javascript agent version is added, and a new field integrity can be seen with a base64-encoded sha384 hash.

## Dashboards

Getting started with Instana website monitoring involves entering your website name and copying over a JavaScript snippet. For more information about getting monitored a website, see the [installation section](https://www.ibm.com/docs/en/instana-observability/current?topic=instana-monitoring-websites#installation).

## Speed

In the speed tab you can view the throughput, latency, and metrics that describe page load times.

## Resources

Third-party resources, like scripts and images, are often responsible for slow page loading. On the resource tab, you can find a table that shows you all the resource providers that are actively used by your website.

After you click a specific origin, you can see more detailed information, including load time breakdowns and caching performance. You can see changes in caching statistics over time and how it relates to loading times.

## HTTP Requests

On the HTTP Requests tab, you can analyze which of your HTTP requests are slow or problematic. If you select a specific origin, you see an insight into HTTP Method Breakdown, throughput and latency, and error rates and latency breakdown.

## Errors

Errors can occur in critical processes. For example, in a process to checkout purchased items in an online storefront, duplicate charge payment errors might occur. As a result, the customer can be dissatisfied and the business needs make provisions such as to process a credit card refund.

Although seeing uncaught errors in traces is helpful, sometimes you don’t care about a single issue. When many teams are involved, or many errors occur, it is much more useful to get an overview of the situation. In the Instana UI, you have the complete error breakdown, with the following information:

*   What errors are occurring and how many errors exist
*   Number of affected users
*   In which browsers the errors occur
*   In which operating systems the errors occur
*   In which pages the errors occur

Insights into affected users are available as user information is made available to the JavaScript agent. For more information, see [Identifying Users](https://www.ibm.com/docs/en/SSE1JP5_current/src/pages/website_monitoring/api.html#identifying-users).

## Pages

Often it's important to isolate specific pages and analyze their performance. This view is also a great one to find your page with the most traffic, or the slowest response times.

After you select a specific page, you can see all the metrics just for this single page.

For more information on how to enable Instana to track page transitions in addition to page loads, see Page.

## Smart Alerts

View a list of all your configured Smart Alerts. Click an alert to view its configuration, modify it, or view its revision history. If required, you can also disable or remove the alert.

For more information about how to add an alert, see [Smart Alerts](https://www.ibm.com/docs/en/SSE1JP5_current/src/pages/website_monitoring/smart_alerts.html).

## Analyze

Similar to Instana analyze capabilities for traces and call, the analytics view for website monitoring data can be used to answer specific questions that aren't covered by any preconfigured dashboards. A single piece of website monitoring data is called a _beacon_. A few _beacon_ types exist, that is, page loads, HTTP requests, resources, and JavaScript errors. For convenience purposes, each beacon type has its own main navigation item within the analytics view.

Beacon data can be used to filter and group. The default grouping depends on the selected beacon type. Grouping can be removed to inspect the individual beacon that match filters.

## Grouped View

Within the grouped analytics view, beacon data is grouped by a certain tag. By default, beacon data is grouped as follows:

Page loads by page name (beacon.page.name).

Resources by resource origin (beacon.http.origin).

HTTP requests by call target origin (beacon.http.origin).

JavaScript errors by error message (beacon.error.message).

The following screen capture shows page loads grouped by browser name (beacon.browser.name), with a chart that is displaying the distribution of page load times (mean) across browsers for a website called Robotshop.

## Metric Selection

The analyze table shows a default set of metrics for every beacon type that are helpful in most cases. To answer more specific questions, Instana supports the selection of metrics for these tables. The selection of metrics enables analysis by using different aggregations, for example percentiles, and separate metrics, like the TCP/SSL times.

The combination of filtering, grouping, metric selection and charting is enough that all the tables and charts that are found within the website dashboards can be rebuilt in the analytics view.

## Ungrouped View

The ungrouped view is accessible after the grouping criteria is removed. It lists every beacon that matches the provided filters. The ungrouped view is also the gateway to the page load view.

## Page Load View

Similar to the trace view for traces and calls, the page load view is the highest detail level within Instana. A page load is defined as the retrieval of the initial HTML document and everything that follows that until the next full-page navigation.

The page load view is designed to give you a quick overview about the page load that occurred. Additionally, you can see every piece of data that is received by Instana for the page load, which means that context is always available when you are analyzing problems. For example, when you are analyzing JavaScript errors, this view adds an understanding of what happened before.

The page load view is modeled after common web developer tools' network tabs. Filtering and searching is possible to handle even much data. Even navigation to backend traces is possible to gain a full understanding why something is behaving the way that it is!

## Trace View Integration

Enabling website monitoring for your websites also enhances the trace views. The trace views are enriched with website monitoring data as the following screen capture shows.

## Geographic Data

Instana maps end-user IP addresses to geographic details based on the GeoLite2 database, which is provided by [MaxMind](https://www.ibm.com/links?url=https%3A%2F%2Fwww.maxmind.com). The IP addresses are collected by using the reverse proxy server.

For self-hosted installation, make sure that you configure the URL of the end-user [Monitoring endpoint](https://www.ibm.com/docs/en/SSE1JP5_current/src/pages/self_hosted/docker_based/end_user_monitoring.html#monitoring-endpoint) as the agent [reporting URL](https://www.ibm.com/docs/en/SSE1JP5_current/src/pages/website_monitoring/api.html#reporting-url). Otherwise, the IP addresses are not collected, and the related geographic details information is not available.

# Monitoring mobile applications

Instana supports mobile app monitoring by analyzing actual URL request times, which provides detailed insights into the app experience of users, and deep visibility into application call paths. The Instana app monitoring uses an iOS or Android agent. The agent is installed as a dependency on mobile apps.

End-User Monitoring (EUM) or Real-User Monitoring (RUM), is a vital tool for understanding the digital user experience with mobile apps.

## Installing the agent for mobile app monitoring

To install the iOS agent, use Swift Package Manager (through Xcode) or CocoaPods.

### iOS

To install the iOS agent, use Swift Package Manager (through Xcode) or CocoaPods.

#### Configuring the Instana iOS agent

Make sure that the following prerequisites are met before you install the iOS agent:

*   iOS 11 or later
*   Swift 5.1 or later

To add Swift Package Manager, complete the following steps:

1.  Open Xcode.
2.  Open your Xcode project.
3.  Select menu **File** > **Add Package Dependencies...**.
4.  In the window that pops up, enter the repository `https://github.com/instana/iOSAgent` in the **Search or Enter Package URL** field. Then, select `**iosagent**` from the search result, and click `**Add Package**`.

To add CocoaPods, complete the following steps:

*   Within your `Podfile` specification, add the commands:
```
pod 'InstanaAgent', '~> 1.6.8'
```
*   Download the dependencies, run `pod install`.

In the command, replace `1.6.8` with the latest iOS agent version that is listed in [https://cocoapods.org/pods/InstanaAgent](https://www.ibm.com/links?url=https%3A%2F%2Fcocoapods.org%2Fpods%2FInstanaAgent).

For more information about the setup process, see the [iOS agent API](https://www.ibm.com/docs/en/SSE1JP5_current/src/pages/mobile_app_monitoring/ios_api.html).

### Android

The Android agent is composed by a Gradle plug-in and an SDK library. Apply the plug-in to your application module and add the SDK as a dependency.

Make sure that the following prerequisites are met before you install the Android agent:

*   Android 4.1+ (API level 16+)
*   Java 8+
*   Gradle 7.3.3+
*   AndroidX
*   targetSdk 33+

#### Adding the Instana Android plug-in

To add the Instana Android plug-in complete the following steps:

*   In your project-level build.gradle file, add the following code:
```
buildscript {
   ext {
        instanaAgentVersion = "6.0.13"
    }
   repositories {
        google()
        mavenCentral()
    }
   dependencies {
      classpath "com.instana:android-agent-plugin:$instanaAgentVersion"
    }
}
```
*   In your module (app-level) Gradle file (usually `app/build.gradle`) after you apply the `com.android.application` plug-in, add the following code:
```
apply plugin: 'com.android.application'
apply plugin: 'com.instana.android-agent-plugin'
```
#### Adding Instana Android SDK

To add the Instana Android SDK, complete the following steps:

  

*   In your project-level build.gradle file, add the following code:
```
allprojects {
    repositories {
        google()
        mavenCentral()
    }
}
```
*   In your module (app-level) Gradle file (usually `app/build.gradle`), add the following code:
```
dependencies {
    implementation 'com.instana:android-agent-runtime:$instanaAgentVersion'
}
```
*   If your `minSdkVersion` is earlier than 24, in your module (app-level) Gradle file (usually `app/build.gradle`), add the following code:
```
android {
    compileOptions {
        sourceCompatibility JavaVersion.VERSION\_1\_8
        targetCompatibility JavaVersion.VERSION\_1\_8
    }
}
```
*   Optional: Request READ\_PHONE\_STATE permission. When a user accesses the internet through a cellular network, the Instana agent can report the specific type of cellular network.

  

To enable reporting of the cellular network type, your app needs to request the READ\_PHONE\_STATE permission. For more information about requesting permissions, see the Request App Permissions section in the official Android documentation.

  

If your app doesn't request the permission or if the user declines the permission, the Instana agent does not report the cellular network type. In your class, which extends Application, replace YOUR\_REPORTING\_URL and YOUR\_APP\_KEY with the configuration values you find in your Instana Dashboard:
```
class MyApplication : Application() {
    override fun onCreate() {
        super.onCreate()
        Instana.setup(
            this,
            InstanaConfig(
                key = "YOUR\_APP\_KEY",
                reportingURL = "YOUR\_REPORTING\_URL"
            )
        )
    }
}
```
Basic initialization is completed in this step. For a complete list of initialization options, view tracking, and other options, see the Android agent API.

### Adding the Instana React Native agent

The React Native agent brings support for both Android and iOS platforms.

Review the prerequisites that are listed in [Instana React Native Agent](https://www.ibm.com/links?url=https%3A%2F%2Fgithub.com%2Finstana%2Freact-native-agent%2Fblob%2Fmaster%2FREADME.md).

### Adding the dependency

To configure the Instana React Native agent, complete the following steps:

1.  Add dependence, run the following command in your project's root:

```
npm install @instana/react-native-agent --save
```
  

1.  In your class `App.js` file, replace `YOUR_INSTANA_APP_KEY` and `YOUR_INSTANA_REPORTING_URL` with the configuration values you find in your Instana Dashboard:

```
export default class App extends Component {
  componentDidMount() {
    Instana.setup(YOUR\_INSTANA\_APP\_KEY, YOUR\_INSTANA\_REPORTING\_URL, null);
  }
}
```
  

Basic initialization is completed in this step. For a complete list of initialization options, view tracking, and other options, see the [React Native agent API](https://www.ibm.com/docs/en/SSE1JP5_current/src/pages/mobile_app_monitoring/react_native_api.html).

  

#### Considerations for using Read Native agent

*   To prevent the Instana agent-tracing communication with the Metro bundler, add `http://localhost:8081` to the ignored URLs list:
```
Instana.setIgnoreURLsByRegex(\['http://localhost:8081.\*'\]);
```
  

*   To support iOS apps, your project must contain at least one Swift file (it can be empty). If you don't have any Swift files, open your Xcode Project in `<YourReactNativeProject>/ios` then add an empty Swift file. Xcode creates the Bridging Header for you.
*   To support Android apps, use the Instana Android plug-in version appropriate for your React Native version:
*   For React Native 0.63.3 or earlier, use Instana Android plug-in 1.5.3
*   For React Native 0.63.4 or later, use Instana Android plug-in 5.2.2

Enable automatic HTTP monitoring:

Your project must contain at least one Swift file. The Swift file can be empty.

If you don't have any Swift files, open your Xcode Project in `<YourReactNativeProject>/ios` then add an empty Swift file. Xcode creates Bridging Header for you.

  

### Android

Follow these steps to enable automatic HTTP monitoring:

*  In your `/android/build.gradle` file, add the following code:
```
buildscript {
    ext {
        INSTANA\_ANDROID\_PLUGIN\_VERSION = "6.0.12"
    }
    dependencies {
        classpath "com.instana:android-agent-plugin:$INSTANA\_ANDROID\_PLUGIN\_VERSION"
    }
}
```    
*  In your `/android/app/build.gradle` file, add the following code:

```
apply plugin: 'com.android.application'
apply plugin: 'com.instana.android-agent-plugin'
```
    

### fetch(url)

If your app uses `fetch` to complete network requests, you might find your app crashes on runtime whenever `fetch` is used: `No virtual method toString(Z)Ljava/lang/String;`

This problem is fixed by the React Native issues ([27250](https://www.ibm.com/links?url=https%3A%2F%2Fgithub.com%2Ffacebook%2Freact-native%2Fissues%2F27250) and [28425](https://www.ibm.com/links?url=https%3A%2F%2Fgithub.com%2Ffacebook%2Freact-native%2Fissues%2F28425)). If you encounter this problem, you can apply the following workaround.

In your Android module-level Gradle file (usually `app/gradle.build`), add the following code:

```
dependencies {
    implementation "com.squareup.okhttp3:okhttp:4.3.1"
    implementation "com.squareup.okhttp3:okhttp-urlconnection:4.3.1"
}
```
  
`Execution failed for task ':app:transformClassesWithDexBuilderForDevDebug'`

If you upgraded to React Native 0.63.4 from a previous version, check that you are using,

*   The compatible Instana Android plug-in version that is listed at [https://www.npmjs.com/package/@instana/react-native-agent](https://www.ibm.com/links?url=https%3A%2F%2Fwww.npmjs.com%2Fpackage%2F%40instana%2Freact-native-agent).
*   For Gradle 7.3.3 and later, refer to `distributionUrl=https\://services.gradle.org/distributions/gradle-7.3.3-bin.zip` in `android/gradle/wrapper/gradle-wrapper.properties`
*   For Android Gradle plug-in 7.2.2 and later, refer to `classpath("com.android.tools.build:gradle:7.2.2")` in `android/build.gradle`

### Flutter

The Flutter agent brings support for both Android and iOS platforms.

Make sure that the following prerequisites are met before you configure the Flutter agent:

*   Flutter version 1.20.0 or later
*   Dart version between 2.12.0 and 3.0.0

#### Adding the package to your app

The Instana agent Flutter package is available from [pub.dev](https://www.ibm.com/links?url=https%3A%2F%2Fpub.dev%2F).

To add the package to your app, complete the following steps:

*  Open the `pubspec.yaml` file located inside the app folder, and then add `instana_agent:` in `dependencies`.    
*  Install the package, by using one of the following methods:
*   From the console: Run `flutter pub get`
*   From Android Studio or IntelliJ: Click **Packages get** in the action ribbon of `pubspec.yaml`
*   From VS Code: Click **Get Packages** in the action ribbon of`pubspec.yaml`

#### Initializing the Instana agent

Import the package in your dart files:

```
import 'package:instana\_agent/instana\_agent.dart';
```
  

Stop and restart the app, if necessary.

Set up Instana as soon as possible. For example, in `initState()`, add the following code:

```
@override
  void initState() {
    super.initState();
    InstanaAgent.setup(key: 'YOUR-INSTANA-KEY', reportingUrl: 'YOUR-REPORTING\_URL');
  }
```
  

If you want to build apps for iOS, set up a platform version in `${appFolder}/ios/Podspec` with a minimum value of `11.0`.

##Tracing View changes

After the Instana agent is initialized, add `InstanaAgent.setView('Home');`:

```
import 'package:instana\_agent/instana\_agent.dart';

\[...\]

InstanaAgent.setView('Home');
```
  

#### Tracing HTTP requests

After the Instana agent is initialized, start capturing HTTP requests:

```
import 'package:instana\_agent/instana\_agent.dart';

\[...\]

InstanaAgent.startCapture(url: 'https://example.com/success', method: 'GET').then((marker) => marker
    ..responseStatusCode = 200
    ..responseSizeBody = 1000
    ..responseSizeBodyDecoded = 2400
    ..finish());
```
  

Create your own `InstrumentedHttpClient` extending `http.BaseClient` as shown in the following example:

```
class \_InstrumentedHttpClient extends BaseClient {
   \_InstrumentedHttpClient(this.\_inner);

   final Client \_inner;

   @override
   Future<StreamedResponse> send(BaseRequest request) async {
      final Marker marker = await InstanaAgent.startCapture(url: request.url.toString(), method: request.method);

      StreamedResponse response;
      try {
         response = await \_inner.send(request);
         marker
            ..responseStatusCode = response.statusCode
            ..responseSizeBody = response.contentLength
            ..backendTracingID = BackendTracingIDParser.fromHeadersMap(response.headers);
      } finally {
         await marker.finish();
      }

      return response;
   }
}

class \_MyAppState extends State<MyApp> {

   \[...\]

   Future<void> httpRequest() async {
      final \_InstrumentedHttpClient httpClient = \_InstrumentedHttpClient(Client());
      final Request request = Request("GET", Uri.parse("https://www.ibm.com/products/instana"));
      httpClient.send(request);
   }

   \[...\]
}
```

# Terminology

###  What is the difference between page views, loads, and transitions?

Single-page applications and multi-page applications work differently from a technical perspective. This difference is essential to judge performance and thus, user experience. These terms help to communicate how a website is used. communicate how a website is used.

*   Page load: The retrieval of the initial HTML document and all subsequent actions until the next navigation in the browser. For example, a navigation that requires a new HTML document to be loaded. Typically the website content is rendered as HTML on the server and then delivered to the user. A multi-page application has only page loads. An example of a multi-page application website is Wikipedia.
*     
    
*   Page transitions: Websites might change the content that the users are looking at with JavaScript. In contrast to page loads, page transitions do not use classical browser navigation. Typically new website content is loaded with JavaScript and then turned into HTML. This HTML is then placed into the document to enrich or replace the existing document. Single-page applications use this technique. For single-page applications, the number of page transitions are larger than page loads. An example of a website that implements this architecture is Instana.
*   A page transition is triggered when the page name is changed by using [API](https://www.ibm.com/docs/en/SSE1JP5_current/src/pages/website_monitoring/api.html#page).
*   Page view: The term page view is introduced to judge general activity on a website irrespective of the architecture that is implemented. Page views are the sum of the page loads and page transitions.

###  What is a beacon?

The JavaScript agent transmits small monitoring payloads to the Instana servers that model specific events that occur within the lifecycle of a page view of a website (for example, page loading, resource retrieval, and HTTP requests). The term beacon comes from the [W3C Beacon specification](https://www.ibm.com/links?url=https%3A%2F%2Fwww.w3.org%2FTR%2Fbeacon%2F).

###  What is an origin?

Origins are a central part of the web security mechanisms. For more information about origins, see [cross-origin resource sharing](https://www.ibm.com/links?url=https%3A%2F%2Fdeveloper.mozilla.org%2Fen-US%2Fdocs%2FWeb%2FHTTP%2FCORS) (CORS). The combination of the scheme (also called a protocol), hostname, and port form an origin. See the following example URL:

https://shop.example.com/articles/hoverboard/ratings

  

The preceding URL has the origin `https://shop.example.com`.

\- Scheme: \`https\`
- Hostname: \`shop.example.com\`
- Port: 443 (based on the default for the HTTPS protocol)

Two origins are the same when all three parts (scheme, hostname, and port) are equal. The following examples are all unequal to each other:

*   `https://shop.example.com`
*   `http://shop.example.com`
*   `https://example.com`
*   `http://example.com`

Same-origin and cross-origin calls or resource sharing is a terminology that is frequently used when you mention origins. The web security mechanism [same-origin policy](https://www.ibm.com/links?url=https%3A%2F%2Fdeveloper.mozilla.org%2Fen-US%2Fdocs%2FWeb%2FSecurity%2FSame-origin_policy) and the [cross-origin resource sharing](https://www.ibm.com/links?url=https%3A%2F%2Fdeveloper.mozilla.org%2Fen-US%2Fdocs%2FWeb%2FHTTP%2FCORS) mechanisms are commonly known. When the source origin (the origin of the HTML document) and the target origin (the origin of an API server) are different, a call is considered to be cross origin and not same origin.

The concept of origins must not be confused with the similar, but notably different in implementation and intention [concept of sites](https://www.ibm.com/links?url=https%3A%2F%2Ftools.ietf.org%2Fhtml%2Fdraft-ietf-httpbis-rfc6265bis-02%23section-5.2).

## Metrics

### 

Most of the website metrics are received from the various W3C specifications. Specifically

*   [Resource Timing](https://www.ibm.com/links?url=https%3A%2F%2Fwww.w3.org%2FTR%2Fresource-timing-2%2F),
*   [Navigation Timing](https://www.ibm.com/links?url=https%3A%2F%2Fwww.w3.org%2FTR%2Fnavigation-timing%2F),
*   [Paint Timing](https://www.ibm.com/links?url=https%3A%2F%2Fwww.w3.org%2FTR%2Fpaint-timing%2F) and
*   [Network Information API](https://www.ibm.com/links?url=https%3A%2F%2Fwicg.github.io%2Fnetinfo%2F%23effective-connection-types)

Instana uses common web terminology from the web vitals project.

*   [Largest Contentful Paint (LCP)](https://www.ibm.com/links?url=https%3A%2F%2Fweb.dev%2Flcp%2F)
*   [First Input Delay (FID)](https://www.ibm.com/links?url=https%3A%2F%2Fweb.dev%2Ffid%2F)
*   [Cumulative Layout Shift (CLS)](https://www.ibm.com/links?url=https%3A%2F%2Fweb.dev%2Fcls%2F)
*   [Time to First Byte (TTFB)](https://www.ibm.com/links?url=https%3A%2F%2Fweb.dev%2Ftime-to-first-byte%2F)

Instana adheres to this terminology as much as possible. Instana uses the following metrics:

*   onLoad Time: This timing exists for each page load and models the time until a navigation is complete (that is, the loading spinner stops). It is defined as `loadEventEnd - fetchStart` (see navigation timing). Within the user interface, onLoad Time and onLoad Event Time are distinguished to be explicit about the differences in terminology between the Instana user interface and the navigation timing specification.
*   DOM: A variation of the timing defined in navigation timing. This metric is defined as `domContentLoadedEventStart - domLoading` (see navigation timing). It is considered a more useful timing breakdown than the navigation timing's processing time. See the following diagram to understand DOM time.
*   Children: A variation of the timing defined in navigation timing. This metric is defined as `loadEventEnd - domContentLoadedEventStart` (see navigation timing). It is considered a more useful timing breakdown than navigation timing's onLoad times. See the following diagram to understand Children time.

For users of the Instana web REST API, an [API endpoint](https://www.ibm.com/docs/en/SSE1JP5_current/src/pages/website_monitoring/web_api_examples.html#listing-all-supported-website-monitoring-metrics) is displayed to learn about the technical metric IDs (`metricId`). The metric IDs that is referenced in this endpoint's response can be used to query metrics with various Instana [website monitoring web REST APIs](https://www.ibm.com/links?url=https%3A%2F%2Finstana.github.io%2Fopenapi%2F%23tag%2FWebsite-Metrics).

 Why are some website metrics not always available or have weird values?

The most important factors are user interaction and web browser support.

User interaction is required for some metrics within the time frame in which the metrics are collected, for example, First-Input Delay. Without user interaction, no metric value is available.

The second important factor is web browser support. Some metrics require web browser features that are not widely supported yet, for example, the modern [web vitals](https://www.ibm.com/docs/en/instana-observability/current?topic=websites-website-monitoring-faq#what-do-the-website-metrics-mean). Unsupported web browser feature means that some websites as a whole, some pages, or single page loads might not contain any information about a metric (for example, about Cumulative Layout Shift). Varying web browser support can also create some confusing situations. For example, First-Contentful Paint (FCP) is more widely supported than Largest-Contentful Paint (LCP). As a result, statistical aggregations across a set of observations cause smaller LCP than FCP values. Although observing for a single page load is difficult, statistical aggregations can occur for a set of page loads given a difference in web browser support as the following examples shows.

*   Observed First-Contentful Paint values: `1000 ms`, `1400 ms`, `1600 ms`. Mean: `1333ms`.
*   Observed Largest-Contentful Paint values: `1000 ms`, `UNSUPPORTED METRIC`, `1600 ms`. Mean: `1300ms`.

### Why are the recorded timings for some of my HTTP calls so unusually huge?

Instana website monitoring records the time between the start of the request (`XMLHttpRequest#send`) and the success event (`XMLHttpRequest#onreadystatechange`) with `readyState === 4`. The following factors affect the time between the preceding two events:

*   HTTP redirects
*   DNS lookup time
*   Time to establish TCP or TLS connections
*   Server response times
*   Request queuing times
*   Latency and throughput
*   Request and response sizes
*   Page throttling

For page throttling, browsers might decide to throttle down or even stop processing for web pages that are not visible. Page throttling is most likely the reason for huge timings. For more information, see [Google's blog post about this subject](https://www.ibm.com/links?url=https%3A%2F%2Fdevelopers.google.com%2Fweb%2Fupdates%2F2017%2F03%2Fbackground_tabs) or the respective [Mozilla Developer Network Page Visibility API page](https://www.ibm.com/links?url=https%3A%2F%2Fdeveloper.mozilla.org%2Fen-US%2Fdocs%2FWeb%2FAPI%2FPage_Visibility_API%23Policies_in_place_to_aid_background_page_performance).

###  Why is the geographic information missing?

Instana's website monitoring collects the geographic information based on IP-address/ or Geo-location mapping. The IP address information is collected by using the reverse proxy server. If the geographic information is missing on the website monitoring user interface, you can check whether the reporting URL of the JavaScript agent is configured to bypass the reverse proxy server and send data to the internal monitoring endpoint (usually `2999`) directly.

The reverse proxy server is installed automatically as part of the Instana self-hosted (on-premises) setup. For more information, see [Exposing the monitoring endpoint to end-users](https://www.ibm.com/docs/en/SSE1JP5_current/src/pages/self_hosted/docker_based/end_user_monitoring.html#exposing-the-monitoring-endpoint-to-end-users).

##  Data collection

###  How are you gathering this information?

Instana's website monitoring is based on an open-source library called [weasel](https://www.ibm.com/links?url=https%3A%2F%2Fgithub.com%2Finstana%2Fweasel). Weasel gathers the information from the [Browser Navigation Timing API](https://www.ibm.com/links?url=https%3A%2F%2Fwww.w3.org%2FTR%2Fnavigation-timing) and transmits it in an efficient form. For more information about weasel, see its source code on GitHub.

###  Which browsers are supported?

The JavaScript agent supports all commonly used browsers. However, some APIs and JavaScript language features aren't supported in older browsers. In those cases, the JavaScript agent might not be able to collect all wanted data points, such as navigation, resource, and paint timing information.

In old browsers (all browsers before Internet Explorer 6), the JavaScript agent can fail to load. As a result, no data is collected.

###  How do you handle browsers that do not support the navigation timing API?

For browsers that do not support the navigation timing API, Instana provides approximate timings. These timings are not reliable, and so do not rely on them for these traces too much. When Instana must resort to approximations for page load times, the values are excluded from statistics, that is, approximations are not part of aggregated page load times like mean, min, and max.

###  What kind of `ineum` calls can I make?

For more information about the global `ineum` function, see [website monitoring API documentation](https://www.ibm.com/docs/en/SSE1JP5_current/src/pages/website_monitoring/api.html).

###  Why am I blocked by AdBlock or similar browser extensions?

While most of the ad-blocking extensions are created not to display advertisements, most of them evolve into extensions that prevent website owners from tracking their users. The Instana monitoring script ends up in many of the ad-blocking extensions. If you have control over your users, you can ask them to allow the EUM script in their ad-blocking extension.

###  How does backend correlation work with Ajax calls?

For more information about backend correlation mechanisms, see [Backend correlation](https://www.ibm.com/docs/en/SSE1JP5_current/src/pages/website_monitoring/backend_correlation.html).

###  What errors might occur with an HTTP request?

The JavaScript agent runs on the web browser that issues HTTP requests. The JavaScript agent collects the common HTTP errors that include [client error with HTTP response code 4XX](https://www.ibm.com/links?url=https%3A%2F%2Fdeveloper.mozilla.org%2Fen-US%2Fdocs%2FWeb%2FHTTP%2FStatus%23client_error_responses) and [server error with HTTP response code 5XX](https://www.ibm.com/links?url=https%3A%2F%2Fdeveloper.mozilla.org%2Fen-US%2Fdocs%2FWeb%2FHTTP%2FStatus%23server_error_responses), which are identified with the HTTP response code. The agent can also detect the following errors when the web browser handles the incomplete HTTP requests:

*   [Timeout](https://www.ibm.com/links?url=https%3A%2F%2Fxhr.spec.whatwg.org%2F%23the-timeout-attribute)
*   [Request aborted](https://www.ibm.com/links?url=https%3A%2F%2Fxhr.spec.whatwg.org%2F%23the-abort\(\)-method)
*   [Open XHR object error](https://www.ibm.com/links?url=https%3A%2F%2Fxhr.spec.whatwg.org%2F%23the-open\(\)-method)
*   [Non-HTTP error](https://www.ibm.com/links?url=https%3A%2F%2Fxhr.spec.whatwg.org%2F%23events)

###  Which HTTP headers are used?

The JavaScript agent makes use of the following HTTP headers to achieve backend correlation.

*   Request Headers (to the backend):
*   `X-INSTANA-T`
*   `X-INSTANA-S`
*   `X-INSTANA-L`
*   Response Headers (to the front end):
*   `Server-Timing`

###  Why is there no data for GoogleBot and others?

Due to bots that manipulate JavaScript APIs to return predictable or reproducible results, the Instana JavaScript agent and servers identify and block data collection for various bots. Blocking data collection has a positive impact when scraping the web, but unfortunately causes problems when wanting to monitor user experiences. For example, the GoogleBot's JavaScript API:

*   `Date.now()` does not return the current time in milliseconds, but instead some seemingly fixed timestamps. As a result, durations recorded by diffing two timestamps that are acquired by `Date.now()` cannot be trusted.
*   `Math.random()` and `crypto.getRandomValues()` return values out of a pool of pre-defined values. This causes problems with client-side generated IDs, such as causing the wrong backend correlation references.

###  Which HTTP endpoints do users make calls to (for SaaS)?

You needn't configure anything for correct data transmission to Instana's SaaS platform. The Instana user interface always presents the correct tracking snippet, which includes the necessary URLs. For more information about endpoints, see [website monitoring endpoints](https://www.ibm.com/docs/en/SSE1JP5_current/src/pages/setup_and_manage/endpoints_and_keys.html#endpoints-for-website--mobile-app-agents).

###  Is it possible to proxy the HTTP endpoints (for SaaS)?

Do not attempt proxying of the HTTP endpoints. Instana does not provide support for any proxy setups or for any issues that might arise due to the usage of a proxy. If you still want (or have) to do setup proxy, you might find the following tips helpful:

*   Set proper `Host` HTTP headers.
*   Respect the difference between the `eum.instana.io` and `eum-{region}.instana.io` servers.
*   Make sure that Instana servers are aware of the user IPs. Send an `X-FORWARDED-FOR` header to Instana servers with the user's IP. Alternatively, send a `X-REALER-IP` HTTP header (not `X-REAL-IP`) to the Instana servers that contains the user's IP.
*   Pass through all the HTTP headers that the Instana servers include in the response body.
*   Don't do any caching in the proxy.

###  Are you collecting any data from WebSockets?

Instana's JavaScript agent does not collect any information about WebSockets. WebSockets have no semantic model that Instana can effectively monitor aside from messages flowing between client and server. Because WebSocket messages have arbitrary formats (just character sequences or bytes), Instana cannot deduce any type of request, response, success, or failure state.

Although you can theoretically transmit every message transmitted or received with WebSockets to Instana's servers, such transmission has several problems:

*   High probability of collection of sensitive data that must never land in a monitoring system.
*   Large amounts of data are collected from every user, which results in overhead for users.
*   Typically a low signal-to-noise ratio in the collected data.
*   Lack of standardized semantic model in the data means that Instana cannot optimize access to the data for you.

For these reasons, Instana does not automatically collect any data about WebSockets. However, some customers implement request or response and subscription mechanisms on WebSockets. For more information, see [custom event API](https://www.ibm.com/docs/en/SSE1JP5_current/src/pages/website_monitoring/api.html#reporting-custom-events). With the [custom event API](https://www.ibm.com/docs/en/SSE1JP5_current/src/pages/website_monitoring/api.html#reporting-custom-events), you can realize backend correlation for WebSocket-based request or response systems.

###  Why is eum.js the initiator of all XMLHttpRequest and Fetch calls?

Instana JavaScript agent instruments the `XMLHttpRequest` and `fetch` APIs of the web browsers to learn about calls that websites are making. This instrumentation causes the JavaScript agent (eum.js) to appear as the initiator within the web browser developer tools as the following screenshot shows. The Instana JavaScript agent seems to be making these calls. However, these calls are actually made by the website that Instana monitors.

Instana's JavaScript agent communicates directly only with servers that are defined within the JavaScript snippet that are shown by the Instana user interface or as adapted for on-premises deployments.

 What happens for users with bad internet or network connections?

Two cases can occur:

1.  Website visitors might not be able to download our JavaScript agent. In these cases, no data can be collected.
2.  Data transmission requests from your website visitors to our servers might not be working. Instana does not reattempt delivery in these cases, nor does Instana store the data for later delivery.

###  Why does your script tag carry the `defer` attribute?

Questions about JavaScript snippet, its structure, and Instana's chosen approach are frequently asked. The snippet is carefully designed to balance the customers' needs. The following section provide some insights into these questions.

####  Tradeoffs

Website monitoring means the collection of all relevant data with the smallest potential end-user impact, which is a tradeoff. The tradeoff is the easiest to note with the JavaScript snippet that users embed on their websites. The following concerns led to the current design.

#####  Comprehensive JavaScript Initialization Process Monitoring

Modern single-page applications run JavaScript as part of their initialization process. Frequently, this initialization process includes HTTP requests. Customers expect to see detailed monitoring data for this initialization process. While a subset of the monitoring data can be collected post-factum, some critical bits (for example, detailed HTTP request insights and backend correlation) can be collected only if the agent runs before the website JavaScript.

#####  Avoiding HTML parser blocking

#####  Resilience against server failures

In addition to HTML parser-blocking, the failed retrieval of a JavaScript file can have dramatic consequences on the HTML document loading experience, such as blocking of the various events that occur as part of the HTML document parsing, loading, and execution processes, and through this broken website.

#####  Synchronous JavaScript agent API calls

Instana's JavaScript agent provides an API through which it can be configured, page names set, custom events raised and much more. For ease of use, the API's usage is straightforward and decoupled from the JavaScript agent's loading procedure.

#####  Good overall experience

Instana has a large variety of users with different skills and varying levels of expertise in web development and web monitoring specifics. The solution must satisfy various use cases.

#####  Mapping tradeoffs to our approach

At Instana, use a script tag that carries the `defer` attribute. This attribute avoids HTML parser blocking while enabling most of Instana customers to gain comprehensive JavaScript initialization process monitoring. In some scenarios, an `async` script tag is sufficient. In other scenarios, a parser-blocking, synchronously downloading and running script is sufficient. Considering most modern web frameworks and approaches to their loading procedures, the `defer` attribute is the most effective.

Another concern is resilience against server failures. When Instana's JavaScript agent cannot be loaded, elaborate JavaScript-loading mechanisms can balance the agent. Cloudflare is one of Instana's partners that has a highly resilient content delivery network (CDN) with advanced mechanisms for increased resilience ([Cloudflare Always Online](https://www.ibm.com/links?url=https%3A%2F%2Fdevelopers.cloudflare.com%2Fcache%2Fhow-to%2Falways-online%2F)). The combination of a great CDN partner, their Always Online technology, and generous cache-control headers that include [stale content](https://www.ibm.com/links?url=https%3A%2F%2Ftools.ietf.org%2Fhtml%2Frfc5861) all address this risk without a constant overhead caused by complicated JavaScript loading mechanisms.

####  Removing or replacing the `defer` attribute

As mentioned in the previous sections, the decision to use `async` over `defer`, or to use neither boils down to the tradeoff criteria listed. All three loading mechanisms are perfectly acceptable for Instana's JavaScript agent. However, the availability of Instana's instrumentations and hooks and the availability of monitoring data are affected. If you want to tweak the loading behavior, check the following:

Are you assigning `window.fetch` to a local variable and then carrying on using this variable to make HTTP requests? Check that the Instana agent is loaded before you assign `window.fetch`. Alternatively, you can change the code to always use the global. [apollo-link-http](https://www.ibm.com/links?url=https%3A%2F%2Fwww.apollographql.com%2Fdocs%2Flink%2Flinks%2Fhttp%2F) is a library that uses this pattern.

*   Are you making HTTP requests before the [DOMContentLoaded](https://www.ibm.com/links?url=https%3A%2F%2Fdeveloper.mozilla.org%2Fen-US%2Fdocs%2FWeb%2FAPI%2FWindow%2FDOMContentLoaded_event) event is raised? You might gain increased insights by removing the defer attribute.

###  Enable debug logging for the JavaScript agent

Instana's JavaScript supports debug logging that you can use to gain extra insights into misconfiguration, data transmission, limits, and more. To enable debug logging for the JavaScript agent, change the URL to the JavaScript agent within the monitoring snippet.

Edit the monitoring snippet and replace the file references from `eum.min.js` to `eum.debug.js`, as shown in the following snippet.

<!-- before -->
<script defer crossorigin="anonymous" src="https://{{hostname}}/eum.min.js"></script>

<!-- after -->
<script defer crossorigin="anonymous" src="https://{{hostname}}/eum.debug.js"></script>

  

###  Are there any limits to the amount of data collected?

The JavaScript agent has a data collection limit per browser tab to protect Instana systems and users from misconfiguration and circular monitoring patterns. The limits are as follows:

*   Any transmitted beacon (except for page resources, rules apply in addition to the more specific rules mentioned later)
*   max per 10s: 128
*   max per 10 min: 4096
*   max per page load: 8096
*   Page changes
*   max per 10s: 32
*   max per 10 min: 128
*   Custom events
*   max per 10s: 32
*   max per 10 min: 128
*   HTTP call beacons that are initiated by using `window.fetch`
*   max per 10s: 32
*   max per 10 min: 256
*   HTTP call beacons that are initiated by using `window.XMLHttpRequest`
*   max per 10s: 32
*   max per 10 min: 256

##  Sensitive data

###  Are you collecting data that can uniquely identify users?

By default, the Instana JavaScript agent does not include data that can uniquely identify users. Also, the Instana JavaScript agent also does not apply techniques such as device or browser fingerprinting.

User-specific data can be made available to Instana by using the [user API](https://www.ibm.com/docs/en/SSE1JP5_current/src/pages/website_monitoring/api.html#identifying-users).

###  What are you doing with the user data transmitted to Instana?

The [user API](https://www.ibm.com/docs/en/SSE1JP5_current/src/pages/website_monitoring/api.html#identifying-users) can be configured by customers to transmit user identifying information to Instana. This information is used only to provide the features visible within the product. Instana does not interpret this data in any other way, nor is it correlated across multiple customers.

###  Is it possible to delete user data after it is transmitted to Instana?

Instana supports infrequent deletion requests, for example, to comply with GDPR. If you expect frequent or periodic deletion requests, instead transmit anonymized data to Instana (for example, hashed user IDs).

###  Are IPs anonymized?

IPs are anonymized. By default, the last octet of IPv4 addresses and the last 80 bits of IPv6 addresses are set to zeros. Stricter anonymization rules can be configured by using the configuration tab in a website's dashboard within the Instana user interface.

###  How do you gain access to user IPs?

The JavaScript agent does not have access to IP addresses. User IP addresses are accessed through the network connections that they establish to the servers. The data that is received from the JavaScript agents is enriched by the servers with [anonymized IP addresses](https://www.ibm.com/docs/en/SSE1JP5_current/src/pages/website_monitoring/faq.html#are-you-anonymizing-ips).

###  Does Instana use cookies?

The website monitoring itself does not directly use cookies. However, Instana's Content-Delivery Network (Cloudflare) sets a cookie that is named `__cfduid` for security purposes. For more information about the `__cfduid` cookie, see the [Cloudflare FAQ article](https://www.ibm.com/links?url=https%3A%2F%2Fdevelopers.cloudflare.com%2Ffundamentals%2Freference%2Fpolicies-compliances%2Fcloudflare-cookies%2F%2312345682).

###  Does Instana use `localStorage` or `sessionStorage`?

By default, the Instana JavaScript agent does not use the `localStorage` and `sessionStorage` technologies. However, `localStorage` is used when you turn on [session tracking](https://www.ibm.com/docs/en/SSE1JP5_current/src/pages/website_monitoring/api.html#session-tracking). By default, the session tracking feature is unavailable in the Instana JavaScript agent.

###  Where does Instana store website monitoring data?

Where the website monitoring data is stored depends on the specific Instana installation. Generally, the data is stored in either the Amazon or Google cloud within either their European or US region. You can identify where your data is stored based on the [reportingUrl](https://www.ibm.com/docs/en/SSE1JP5_current/src/pages/website_monitoring/api.html#reporting-url) shown in the Instana tracking snippet and the [list of reporting endpoints for JavaScript agents](https://www.ibm.com/docs/en/SSE1JP5_current/src/pages/setup_and_manage/endpoints_and_keys.html#endpoints-for-website--mobile-app-agents).

###  Does CDN (Cloudflare) store user data?

Users download the JavaScript agent by using the Content-Delivery Network (CDN) provided by Cloudflare. Cloudflare keeps user data (including IP addresses) for a small amount of time within their logs. For more information, see [Cloudflare FAQ](https://www.ibm.com/links?url=https%3A%2F%2Fdevelopers.cloudflare.com%2Ffundamentals%2Freference%2Fpolicies-compliances%2Fcloudflare-cookies%2F%2312345682).

##  Impact of web security

###  I have a Content-Security-Policy in place, is there anything I need to do?

The Instana JS agent is asynchronously loaded from `eum.instana.io` and can be loaded with HTTP(S). Check that loading scripts from this domain is possible.

Data is transmitted to Instana with [image loads](https://www.ibm.com/links?url=https%3A%2F%2Fgithub.com%2Finstana%2Fweasel%2Fblob%2F2cc83d998c188ceb52198c26ec48a6f3dea590c3%2Flib%2Ftransmission.js%23L32-L33), HTTP GET, and POST requests (with `XMLHttpRequest`). The origins that are used for data transmission are displayed in the tracking snippet.

The following Content-Security-Policy definition shows what is required for Instana's SaaS product:

script-src \*.instana.io;
img-src \*.instana.io;
connect-src \*.instana.io;

  

###  What is the impact of same-origin policy on website monitoring?

The [same-origin policy](https://www.ibm.com/links?url=https%3A%2F%2Fdeveloper.mozilla.org%2Fen-US%2Fdocs%2FWeb%2FSecurity%2FSame-origin_policy) is one of the most fundamental website security concepts. Every website is subject to the policy because all web browsers enforce it. As a website monitoring provider, Instana cannot control your website or browser security. Instana can work only within the imposed security constraints. Unfortunately, this restricts Instana monitoring abilities.

*   Browsers restrict access to error messages and stack traces to scripts of the same origin.
*   Browsers restrict allowed HTTP headers for cross-origin requests. Therefore, backend correlation is not always possible.

To unlock these features when multiple origins are involved, you can use [cross-origin resource sharing (CORS)](https://www.ibm.com/links?url=https%3A%2F%2Fwww.w3.org%2FTR%2Fcors%2F). CORS is a mechanism with which small controlled holes are opened within the same-origin policy security mechanism. The following image describes in detail what needs to be done to address the same-origin policy-imposed restrictions.

For more information about Instana backend correlation mechanisms and how web security is impacting these correlation mechanisms, see [Backend correlation](https://www.ibm.com/docs/en/SSE1JP5_current/src/pages/website_monitoring/backend_correlation.html).

 Why are detailed resource retrieval breakdowns not always available?

The availability of insights into network times, caching statistics, and asset sizes rely on [resource timing capabilities](https://www.ibm.com/links?url=https%3A%2F%2Fwww.w3.org%2FTR%2Fresource-timing-2%2F). These capabilities are available in [most modern web browsers](https://www.ibm.com/links?url=https%3A%2F%2Fcaniuse.com%2F%23feat%3Dresource-timing) when allowed by the same-origin policy.

To enable insights into resources of cross-origin resources (for example, origin `https://cdn.example.com:443` for an HTML document that is loaded from `https://example.com:443`), you can use the `Timing-Allow-Origin` HTTP header. The following image shows how to set the header. Also, for more information, see the [resource timing specification](https://www.ibm.com/links?url=https%3A%2F%2Fwww.w3.org%2FTR%2Fresource-timing-2%2F%23sec-timing-allow-origin).

 How can I gain insights into Script Errors?

Websites that embed many third-party scripts typically encounter a steady number of script errors. `Script Error` indicates JavaScript error in third-party scripts. For security purposes, web browsers restrict access to third-party scripts' JavaScript errors by replacing the real error message with `Script Error` and clearing the stack trace.

On the web, you can use the following ways to gain insights into `Script Error`:

*   You can instruct web browsers to expose error messages and stack traces by indicating that the third-party script does not contain sensitive data.
*   You can use [loopholes](https://www.ibm.com/docs/en/SSE1JP5_current/src/pages/website_monitoring/api.html#insights-into-script-errors) in the web security model (discouraged and not guaranteed to work).

You are recommended to use the first option because this is the designed and proper way to achieve `Script Error` insights. To implement the first option, do the following actions:

*   Add a `crossorigin="anonymous"` attribute to script tags.
*   Make sure that the HTTP response carrying the script's source is sending a `Access-Control-Allow-Origin` response header.

 Why do I see same-site cookie warnings when I use the JavaScript agent?

When you analyze same-site cookie warnings, you must differentiate between the following two cases:

*   Users signed into Instana's product (either SAAS or self-hosted), which have cookies set related to their sign in and Instana product usage.
*   Your website visitors who have no affiliation with Instana and are, typically, not aware of Instana.

For the former group (that is, Instana users), Instana and its partners are setting cookies. Web browsers transmit these cookies to Instana servers as part of website monitoring. Instana servers never expect these cookies to exist for website monitoring. Therefore, blocking of cookies by web browsers is not an issue. The only cookie that is used for website monitoring is [the one by Cloudflare](https://www.ibm.com/docs/en/SSE1JP5_current/src/pages/website_monitoring/faq.html#are-you-making-use-of-cookies).

For the latter group (that is, your website's visitors), the SameSite cookie has no known issues. Instana's [CDN provider](https://www.ibm.com/docs/en/SSE1JP5_current/src/pages/website_monitoring/faq.html#are-you-making-use-of-cookies) sets a cookie with a valid `SameSite=Lax` cookie configuration.

Check for potential SameSite cookie issues by using an incognito or private browser window. Through this incognito or InPrivate browser window, you can experience your website like a visitor.

##  Should I use Instana for my business-analytics use cases?

Some business analytics use cases can be addressed with the data that is collected by Instana. Instana focuses on delivering a best-in-class performance product, and as such, not a replacement for a dedicated business analytics product.

##  JavaScript stack trace translation

###  What is JavaScript stack trace translation?

The JavaScript stack trace translation provides clear and more actionable stack traces within Instana.

Before:
at http://shop-demo-app.instana.io/static/js/main.b1510333.chunk.js:1:1559

After:
at ProductDetails.js 26:11

  

The problem with untranslated stack trace lines is that the errors aren't actionable. Developers work with many (typically small) files. For performance reasons, these files are shipped to user browsers in a bundled and minified format that result in file names, lines, and column numbers in stack traces that are not human-readable or actionable.

With a translated stack trace, it's clear that the error occurring at `…/main.b1510333.chunk.js:1:1559` is in fact `at ProductDetails.js 26:11`.

###  How does JavaScript Stack Trace Translation work?

The translation works by using [source maps](https://www.ibm.com/links?url=https%3A%2F%2Fwww.html5rocks.com%2Fen%2Ftutorials%2Fdevelopertools%2Fsourcemaps%2F). Source maps enable us to translate unactionable stack traces to actionable stack traces. More specifically, they allow us to translate references to files, names, lines, and columns to their actual source code counterparts.

To achieve this, Instana runs the following steps:

1.  The JavaScript agent reports JavaScript errors to Instana's servers. For example, let's assume the stack trace contains the line `at http://shop-demo-app.instana.io/static/js/main.b1510333.chunk.js:1:1559`.
2.  Instana's servers attempt to download the JavaScript file to identify the [source map responsible for this file](https://www.ibm.com/links?url=https%3A%2F%2Fdeveloper.mozilla.org%2Fen-US%2Fdocs%2FTools%2FDebugger%2FHow_to%2FUse_a_source_map).
3.  The HTTP response is parsed, and Instana looks for [references to source maps](https://www.ibm.com/links?url=https%3A%2F%2Fdeveloper.mozilla.org%2Fen-US%2Fdocs%2FTools%2FDebugger%2FHow_to%2FUse_a_source_map).
4.  When a source map file is referenced, Instana downloads the source map file by using an HTTP GET request or searches in the [uploaded source map files by the user](https://www.ibm.com/docs/en/SSE1JP5_current/src/pages/website_monitoring/js_sourcemap_upload.html).
5.  When the download or the lookup is successful, the source map file is used to translate the file, name, line, and column references.

See the following steps for the stack trace line `at http://shop-demo-app.instana.io/static/js/main.b1510333.chunk.js:1:1559`.

1.  An error is reported to Instana's servers.
2.  Instana's servers issue an HTTP GET request to `http://shop-demo-app.instana.io/static/js/main.b1510333.chunk.js`.
3.  The source map reference `//# sourceMappingURL=main.b1510333.chunk.js.map` is located in the JavaScript file.
4.  The source map file `http://shop-demo-app.instana.io/static/js/main.b1510333.chunk.js.map` is downloaded by using an HTTP GET request or can be found in the uploaded source map files.
5.  The source map is parsed, and the stack trace made readable.

###  How exactly does Instana retrieve files from our servers?

When Instana learns about the stack trace, it automatically issues HTTP requests to retrieve the JavaScript and source map files. The following call shows the closest representation of the calls made:

curl -H 'Accept: \*/\*' \\
  # Use a fake user-agent to bypass simple bot blockers
  -H 'User-Agent: Mozilla/5.0 (Macintosh; Intel Mac OS X 10\_14\_6) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/76.0.3809.100 Safari/537.36' \\
  {{url of JavaScript or source map files}}

  

You can use the previous command to identify what kind of configuration Instana needs to download the JavaScript and source map files from your servers. The HTTP requests are issued from servers that are running inside AWS (Amazon Web Services) or Google Cloud. Advanced bot detection mechanisms might block requests coming from AWS or Google Cloud. Therefore, consider configuring extra headers that Instana needs to send to your servers to circumvent bot detection mechanisms.

###  How can I make sure that the Instana servers can establish a TCP or TLS connection?

The Instana servers are issuing requests from AWS or Google Cloud servers. Therefore, the JavaScript and source map files are accessible from the internet. Also you need to make sure that your server has a working TLS configuration with a complete certificate chain. You can check for any TLS issues by using the free [SSL Test from SSL Labs/Qualys](https://www.ibm.com/links?url=https%3A%2F%2Fwww.ssllabs.com%2Fssltest%2F) or by running the following commands:

openssl s\_client -showcerts -connect {{YOUR\_DOMAIN\_HERE}}:443

  

###  How can I upload source map files to Instana?

# For information about uploading source map files to Instana, see [uploading source map files to Instana](https://www.ibm.com/docs/en/SSE1JP5_current/src/pages/website_monitoring/js_sourcemap_upload.html).

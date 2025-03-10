# Changelog

## 3.6.3 (2021-10-12)

* Bump Jackson from 2.9.1 for critical vulnerability fixes
  [#170](https://github.com/bugsnag/bugsnag-java/pull/170)

## 3.6.2 (2020-11-10)

* Fix JVM hang when System.exit or bugsnag.close is not called
  [#157](https://github.com/bugsnag/bugsnag-java/pull/157)

## 3.6.1 (2019-08-15)

* Prevent potential ConcurrentModificationException when adding callback
  [#149](https://github.com/bugsnag/bugsnag-java/pull/149)

## 3.6.0 (2019-07-08)

* Allow a BugsnagAppender to be created from an existing client
  [#147](https://github.com/bugsnag/bugsnag-java/pull/147)

## 3.5.1 (2019-05-31)

* Remove use of daemon threads, fixing potential resource leak
  [#143](https://github.com/bugsnag/bugsnag-java/pull/143)

## 3.5.0 (2019-05-07)

* Migrate version information to device.runtimeVersions
  [#141](https://github.com/bugsnag/bugsnag-java/pull/141)

## 3.4.6 (2019-04-16)

* Swallow Throwables thrown when configuring bugsnag appender
  [#140](https://github.com/bugsnag/bugsnag-java/pull/140)

## 3.4.5 (2019-04-04)

* Migrate non-standard device fields to metaData.device
  [#131](https://github.com/bugsnag/bugsnag-java/pull/131)

* Set thread name to aid debugging
  [#138](https://github.com/bugsnag/bugsnag-java/pull/138)

* Merge internal checkstyle rules
  [#137](https://github.com/bugsnag/bugsnag-java/pull/137)

## 3.4.4 (2019-01-15)

* Remove unnecessary `@Configuration` annotation
  [#130](https://github.com/bugsnag/bugsnag-java/pull/130)

## 3.4.3 (2019-01-07)

* Support other methods of configuring a TaskScheduler when setting ErrorHandler on scheduled tasks
  [#126](https://github.com/bugsnag/bugsnag-java/pull/126)

## 3.4.2 (2018-11-29)

* Ensure session counts are thread safe
  [#122](https://github.com/bugsnag/bugsnag-java/pull/122)
  
 * Prevent application hangs due to session flushing
[#121](https://github.com/bugsnag/bugsnag-java/pull/121)

## 3.4.1

(Skipped, duplicate of 3.4.0)

## 3.4.0 (2018-11-13)

- Enhanced support for Spring applications with the new `bugsnag-spring` notifier
- The ability to report throwables to Bugsnag with the [logback](https://logback.qos.ch/) appender `BugsnagAppender`  

Two artifacts are now available for this platform:

- `bugsnag-java` - intended for plain Java applications
- `bugsnag-spring` - provides enhanced support for Spring applications

It is recommended that you migrate to `bugsnag-spring` if you develop a Spring application, as it enhances the quantity and quality of error reports which are sent automatically. Full upgrade instructions can be found [here](UPGRADING.md).

No upgrade steps are required for `bugsnag-java` in this release.

* Added `BugsnagAppender` that can report throwables from existing log statements to Bugsnag, using [logback](https://logback.qos.ch/)
* [Spring] Automatically report exceptions thrown when processing MVC/REST requests
* [Spring] Automatically report exceptions thrown in scheduled tasks
* [Spring] Added `BugsnagAsyncConfig` class to simplify capture of uncaught exceptions in async tasks
* [Spring] Automatically attach request metadata to reports
* [Spring] Automatically attach Spring version information to reports
* [Spring] Automatically track sessions for each MVC request

See [UPGRADING](UPGRADING.md) for upgrade details and [the docs](https://docs.bugsnag.com/platforms/java/spring) for further information on new functionality.

## 3.3.0 (2018-09-26)

* Capture trace of error reporting thread and identify with boolean flag
  [#87](https://github.com/bugsnag/bugsnag-java/pull/87)

## 3.2.1 (2018-08-21)

* Add null check when disconnecting HttpUrlConnection
[#92](https://github.com/bugsnag/bugsnag-java/pull/92)

* Make constructors public for SyncHttpDelivery
[#97](https://github.com/bugsnag/bugsnag-java/pull/97)

## 3.2.0 (2018-07-03)

This release introduces automatic tracking of sessions, which by
default are captured for each HTTP request received via the Servlet API. To disable this data collection, call `bugsnag.setAutoCaptureSessions(false)`.

If you wish to use a custom strategy for tracking sessions, call `bugsnag.startSession()` in the
appropriate place within your application.
  [Jamie Lynch](https://github.com/fractalwrench)
  [#70](https://github.com/bugsnag/bugsnag-java/pull/70)

**Deprecation notice**: `setEndpoints(String notify, String session)` is now the preferred way to configure custom endpoints,
if you are using Bugsnag On-Premise.

## 3.2.0-beta (2018-06-14)

**Important**: This is a beta release which introduces automatic tracking of sessions, which by
default are captured for each HTTP request received via the Servlet API. To disable this data collection, call `bugsnag.setAutoCaptureSessions(false)`.

If you wish to use a custom strategy for tracking sessions, call `bugsnag.startSession()` in the
appropriate place within your application.
  [Jamie Lynch](https://github.com/fractalwrench)
  [#70](https://github.com/bugsnag/bugsnag-java/pull/70)

**Deprecation notice**: `setEndpoints(String notify, String session)` is now the preferred way to configure custom endpoints,
if you are using Bugsnag On-Premise.

## 3.1.6 (2018-05-03)
* Make preemptive copy of map filtering specified keys
  [Leandro Aparecido](https://github.com/lehphyro)
  [#77](https://github.com/bugsnag/bugsnag-java/pull/77)
* Add setter for overriding error class
  [Jamie Lynch](https://github.com/fractalwrench)
  [#78](https://github.com/bugsnag/bugsnag-java/pull/78)

## 3.1.5 (2018-03-08)

* Update MetaData filtering to handle different versions of Jackson correctly 
[#76](https://github.com/bugsnag/bugsnag-java/pull/76)

## 3.1.4 (2018-01-19)

* Remove dependency on Guava
* Update Gradle wrapper

## 3.1.3 (2017-11-30)

* Cache hostname to avoid excessive thread spawning

## 3.1.2 (2017-11-03)

* Fixes JDK 7 support by using Android Guava
* Fixes bad artefact packaging caused by bug in gradle

## 3.1.1 (2017-10-11)

### Bug Fixes

* Allow overriding the context set by the servlet callback
  [#63](https://github.com/bugsnag/bugsnag-java/pull/63)

## 3.1.0 (2017-90-22)

### Enhancements

* Track difference between handled and unhandled exceptions
  [#59](https://github.com/bugsnag/bugsnag-java/pull/59)

## 3.0.2 (04 Jan 2017)

### Bug Fixes

* Use deprecated method to ensure we don't break with older versions of jackson
  [William Starling](https://github.com/foygl)
  [#54](https://github.com/bugsnag/bugsnag-java/pull/54)

## 3.0.1 (11 Nov 2016)

### Bug Fixes

* Stop AsyncHttpDelivery from indefinitely blocking exit
  [William Starling](https://github.com/foygl)
  [#50](https://github.com/bugsnag/bugsnag-java/pull/50)

### Enhancements

* Improve Spring compatibility
  [William Starling](https://github.com/foygl)
  [#49](https://github.com/bugsnag/bugsnag-java/pull/49)

## 3.0.0 (31 Oct 2016)

Major rewrite/update of the notifier. Changes include:

* Uses [Jackson](https://github.com/FasterXML/jackson-databind) for streaming JSON serialization
* Logs internally using `org.slf4j.Logger`
* `Severity` is now an enum instead of a `String`
* Request information is automatically collected in Servlet API apps
* JVM runtime, O/S, and locale diagnostics are collected
* The `Client` object has been renamed to `Bugsnag`
* The `Event` object has been renamed to `Report`
* `Report` object is now exposed for ease of attaching diagnostics to error reports
* Targets Java 1.6
* Callbacks now support Java 8 lambda syntax 
* Chaining support added to `Report` methods
* Can now add a Callback to `Bugsnag.notify` calls
* Can now change the API key on a per-report basis using Callbacks
* Error report delivery is now fully swappable via the `Delivery` interface

See [UPGRADING](UPGRADING.md) for upgrade details.

## 2.0.0 (25 Mar 2016)

This is a major release for the release of the potentially breaking change of
sending exception reports asynchronously by default.

### Bug Fixes

* Fix potential `NullPointerException` when passing `null` to `Bugsnag.notify()`
  [Delisa Mason](https://github.com/kattrali)
  [#38](https://github.com/bugsnag/bugsnag-java/pull/38)

### Enhancements

* Send payloads to Bugsnag asynchronously by default
  [Mike Bull](https://github.com/bullmo)
  [#36](https://github.com/bugsnag/bugsnag-java/pull/36)

## 1.4.0 (9 Mar 2016)

### Bug Fixes

* Truncate large payloads to avoid Bad Request errors due to size
  [Duncan Hewett](https://github.com/duncanhewett)
  [#35](https://github.com/bugsnag/bugsnag-java/pull/35)

### Enhancements

* Use TLS by default when connecting to Bugsnag
  [Duncan Hewett](https://github.com/duncanhewett)
  [#34](https://github.com/bugsnag/bugsnag-java/pull/34)

## 1.3.0 (28 Jan 2016)

This release includes an update to the `org.json` dependency.

### Enhancements

* Add configurable connection and read timeouts
  [Lauri Lehtinen](https://github.com/llehtinen)
  [#25](https://github.com/bugsnag/bugsnag-java/pull/25)

* Send the hostname with error reports
  [Mike Bull](https://github.com/bullmo)
  [#23](https://github.com/bugsnag/bugsnag-java/issues/23)
  [#30](https://github.com/bugsnag/bugsnag-java/pull/30)

1.2.8
-----
-   Revert method chaining support in Client

1.2.7
-----
-   Add support for sending thread state information with `setSendThreads`
-   Allow chaining of methods on Client

1.2.6
-----
-   Expose `beforeNotify` callback stack to child classes

1.2.5
-----
-   Add support for `beforeNotify` callback

1.2.4
-----
-   Remove hostname as it causes issues with android

1.2.3
-----
-   Prepare 'severity' feature for release

1.2.2
-----
-   Expose the ExceptionHandler class to allow removal of auto-notification

1.2.1
-----
-   Add hostname to device information

1.2.0
-----
-   Included device and app fields. Transmit appState and deviceState.

1.1.0
-----
-   Reduced memory usage, allow streaming errors from a file

1.0.5
-----
-   Expose the `Configuration` class

1.0.4
-----
-   Added support for `setIgnoreClasses` to set which exception classes
    should not be sent to Bugsnag.

1.0.3
-----
-   Fixed compatibility with Java 1.5

1.0.2
-----
-   Add metrics tracking

1.0.1
-----
-   Allow changing of notifier name/version
-   Reduced jar size

1.0.0
-----
-   Initial release

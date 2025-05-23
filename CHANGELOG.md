# 8.1.0
- Add a utility to detect App Clips and make a semantic check for background
  URL sessions. (#220)

# 8.0.2
- Fix default logging level regression introduced in 8.0.0 (no value set);
  default value is restored to `GULLoggerLevelNotice`. (#207)

# 8.0.1
- Add missing copyright to source file. (#206)
- Removed an extraneous `#undef GUL_LOGGING_FUNCTION`. (#205)

# 8.0.0
- Remove swizzling support for `application:didReceiveRemoteNotification:`.
  Use `application:didReceiveRemoteNotification:fetchCompletionHandler:` instead. (#162)
- Remove `GULHeartbeatDateStorable`, `GULHeartbeatDateStorage`,
  `GULHeartbeatDateStorageUserDefaults` APIs. (#164)
- Remove '+ [GULAppEnvironmentUtil isIOS7OrHigher]' API. (#165)
- Remove '+ [GULAppEnvironmentUtil hasSwiftRuntime]' API. (#166)
- Fix an issue where ObjC associated objects were sometimes set with a
  non-const key, potentially resulting in undefined behavior. (#141)
- Add nullabilty annotations to public headers. (#169)
- Remove references to deprecated CTCarrier. (#106)
- [changed] **Breaking change**: Minimum supported versions have
  updated for the following platforms:
    - | Platform  | GoogleUtilities 8.0|
      | ------------- | ------------- |
      | iOS  | **12.0**  |
      | tvOS  | **13.0**  |
      | macOS  | **10.15**  |
      | watchOS  | 7.0  |
- Remove dependency on `FBLPromises`. The following public API have
  been removed:
  - `- [NSURLSession gul_dataTaskPromiseWithRequest:]`
  - `GULURLSessionDataResponse`
  The following promise-based public API have been replaced with
  completion handler-based alternatives.
  - `- [GULKeychainStorage getObjectForKey:objectClass:accessGroup:]`
  - `- [GULKeychainStorage setObject:forKey:accessGroup:]`
  - `- [GULKeychainStorage removeObjectForKey:accessGroup:]`
  - Update underlying GULLogger implementation from `asl` to `os_log`.
  - Remove `GULLoggerEnableSTDERR` API.

# 7.13.3
- Rename parameter placeholder in `GULSecureCoding` unarchiving API to avoid
  conflict with keyword. (#152)
- Reorganize privacy manifests for SwiftPM so that each library target has its
  own privacy manifest, as opposed to transitively depending on a common one.
  (#150)

# 7.13.2
- Remove synchronization delay for `GULUserDefaults` to better match
  `NSUserDefaults` behavior. (#148)

# 7.13.1 (SwiftPM Only)
- Attempt to fix validation error due to invalid module name. (#146)

# 7.13.0
- Add privacy manifest. (#128)

# 7.12.1 (SwiftPM Only)
- Fix improperly formatted target name that blocks App Store submission. (#140)

# 7.12.0
- Added a logging level getter, `GULGetLoggerLevel`. (#138)

# 7.11.6
- Fix visionOS build on Xcode 15.1 Beta 1.

# 7.11.5
- Replace 'TARGET_OS_XR' with 'TARGET_OS_VISION' for compatibility with
  Xcode 15 Beta 5.

# 7.11.4
- Fix Xcode 15 Beta 4 runtime warning. (#114)

# 7.11.3 (SwiftPM Only)
- Calling `+[GULAppEnvironmentUtil applePlatform]` now returns 'visionos' when
  running on visionOS.

# 7.11.2 (SwiftPM Only)
- Fix build errors on the visionOS platform. (#108)

# 7.11.1
- Fix Xcode 14.3 build warnings.

# 7.11.0
- Add a new POST API in GULNetwork to support HTTP headers. (#99)
- Fix iOS 12 deprecation warnings. (#98)

# 7.10.0
- Added Network Utility. (#91)
- Added a few utility functions for Firebase Performance and FirebaseSession SDKs. (#89, #90)

# 7.9.0 (Swift PM)
- Don't use underscores in SPM target names. This fixes an App Store submission
  issue for SPM builds that dynamically link (firebase-ios-sdk/#9912). (#83)

# 7.8.0
- Update `+ [GULAppEnvironmentUtil deploymentType]` API to fall back to
  `unknown` instead of `cocoapods`. (#79)
- Prevent keychain access from prompting user for permissions on macOS. Using
  GoogleUtilities's keychain wrapper API **on macOS** now requires that the
  target be signed with a provisioning profile that has the Keychain Sharing
  capability enabled. (#75)

# 7.7.1
- Swift Package Manager only release. Unify OCMock dependency with Firebase
  repo. (https://github.com/firebase/firebase-ios-sdk/issues/9591)

# 7.7.0
- Do not dispose a swizzler's generated class when `GULGeneratedClassDisposeDisabled`
  environment variable is set. (#66)

# 7.6.0
- Add proper device model parsing for macOS and Catalyst. (#59)
- Deprecate `hasSwiftRuntime` method. (#62)

# 7.5.2
- Do not dispose a swizzler's generated class when using the Zombies instrument. (#57)

# 7.5.1
- `GULHeartbeatDateStorage`: replace `NSFileCoordinator` with in-process synchronization mechanism. (#51)
# 7.5.0
- Bump Promises dependency. (#8334)

# 7.4.3
- Include all object classes when using archiver. (#42)

# 7.4.2 (Swift PM)
- Fix warnings in Xcode 13 beta 1. (#41)

# 7.4.1
- Improve heartbeat date storage's version compatability. (#37)

# 7.4.0
- Change heartbeat directory name and refactor file. (#19)
- Introduce user defaults based heartbeat storage. (#23)
- Support iOS 9 with Swift Package Manager.

# 7.3.1
- Add explicit dependency on Security framework to Environment subspec. (#12)

# 7.3.0
- Fix conflicting internal constant name and move it out of the public header. (#7635)

# 7.2.2
- Fix warnings introduced with Xcode 12.5. (#8)

# 7.2.1
- Fix GoogleUtilities namespacing (SPM only release). (#7)

# 7.2.0
- `NSURLSession` promise extension public API. (#7097)

# 7.1.1
- Fix `unrecognized selector` for isiOSAppOnMac on early iOS 14 betas. (#6969)

# 7.1.0
- Added `NSURLSession` promise extension. (#6753)
- `ios_on_mac` option added to `GULAppEnvironmentUtil.applePlatform()`. (#6799)
- Fixed completion handler issue in `GULAppDelegateSwizzler` for
  `application(_:didReceiveRemoteNotification:fetchCompletionHandler:)` method.  (#6863)

# 7.0.0
- All APIs are now public. All CocoaPods private headers are transitioned to public. Note that
  GoogleUtilities may have more frequent breaking changes than Firebase. (#6588)
- Fixed writing heartbeat to disk on tvOS devices. (#6658)
- Refactor `GULSwizzledObject` to ARC to unblock SwiftPM support. (#5862)

# 6.7.1
- Fix import regression when mixing 6.7.0 with earlier Firebase versions. (#6047)

# 6.7.0 -- M75
- Lazily access filesystem outside of `GULHeartbeatDateStorage` initializer. (#5969)
- Update source imports to use repo-relative headers. (#5824)
- Source cleanups to remove pre-iOS 8 code. (#5841)

# 6.6.0 -- M69
- Keychain utilities and Keychain based key-value storage added to
  `GoogleUtilities/Environment`. (#5329)

# 6.5.2
- Fixed an issue where GoogleUtilities misidentified Catalyst as a
  simulator runtime environment. (#5048)

# 6.5.1
- Standardized import paths. (#4655)

# 6.5.0
- Swizzler changes.

# 6.4.0
- Add function to gul secure encoding to encode multiple classes. (#4282)
- Add heartbeat feature. (#4098)
- Support UISceneDelegate changes in Auth. (#4380)

# 6.3.1
- Fix GULMutableDictionary keyed subscript methods. (#3882)
- Update Networking to receive data for POST requests. (#3940)
- Fix crash in GULLogBasic. (#3928)

# 6.3.0
- GULSecureCoding introduced. (#3707)
- Mark unused variables. (#3854)

# 6.2.5
- Remove test-only method and update tests to include Catalyst. (#3544)

# 6.2.4
- Fix `GULObjectSwizzler` dealloc thread-safety. (#3300, #3183)

# 6.2.3
- Revert "Fix `GULMutableDictionary` thread-safety." (#3322)

# 6.2.2
- Add explicit Foundation import for headers.
- Fix headers import. (#3277)
- Fix README. (#3305)
- Fix `GULMutableDictionary` thread-safety. (#3322)

# 6.2.1
- Fix Xcode 11 build warning. (#3133)

# 6.2.0
- Stop conditional compilation for GoogleUtilities testing. (#3058)

# 6.1.0
- Added `GULAppDelegateSwizzler` macOS support. (#2911)

# 6.0.0
- GULAppDelegateSwizzler - proxy APNS methods separately. (#2835)
- Cocoapods 1.7.0 multiproject support. (#2751)
- Bump minimum iOS version to iOS 8. (#2876)

# 5.7.0
- Restore to 5.5.0 tag after increased App Store warnings. (#2807)

# 5.6.0
- `GULAppDelegateSwizzler`: support of remote notification methods. (#2698)
- `GULAppDelegateSwizzler`: tvOS support. (#2698)

# 5.5.0
- Revert 5.4.x changes restoring 5.3.7 version.

# 5.4.1
- Fix GULResetLogger API breakage. (#2551)

# 5.4.0
- Update GULLogger to use os_log instead of asl_log on iOS 9 and later. (#2374, #2504)

# 5.3.7
- Fixed `pod lib lint GoogleUtilities.podspec --use-libraries` regression. (#2130)
- Fixed macOS conditional check in UserDefaults. (#2245)
- Migrate to clang-format 8.0.0. (#2222)

# 5.3.6
- Fix nullability issues. (#2079)

# 5.3.5
- Fixed an issue where GoogleUtilities would leak non-background URL sessions.
  (#2061)
- Fixed a crash caused due to `NSURLConnection` delegates being wrapped in an
  `NSProxy`. (#1936)

# 5.3.4
- Fixed a crash caused by unprotected access to sessions in
  `GULNetworkURLSession`. (#1964)

# 5.3.3
- Fixed an issue where GoogleUtilities would leak instances of `NSURLSession`.
  (#1917)

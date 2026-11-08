# mesibo iOS SDK

mesibo frameworks for iOS, distributed with Swift Package Manager.
Documentation: https://docs.mesibo.com/

## Installation

In Xcode, choose **File → Add Package Dependencies…** and enter:

```
https://github.com/mesibo/mesibo-ios-sdk
```

Pick a version rule (for example "Up to Next Major Version"), then add the products you need
to your app target:

| Product | What it is | Also brings in |
|---|---|---|
| `mesibo` | Core real-time messaging and calls API | |
| `MesiboUI` | Ready-to-use messaging UI | `mesibo` |
| `MesiboCall` | Voice and video call UI and API | `mesibo` |
| `MesiboUIHelper` | Welcome and login screens | |

Or, in a `Package.swift`:

```swift
dependencies: [
    .package(url: "https://github.com/mesibo/mesibo-ios-sdk", from: "2.10.0"),
],
targets: [
    .target(name: "YourApp", dependencies: [
        .product(name: "mesibo", package: "mesibo-ios-sdk"),
        .product(name: "MesiboUI", package: "mesibo-ios-sdk"),
        .product(name: "MesiboCall", package: "mesibo-ios-sdk"),
    ]),
]
```

Xcode downloads the frameworks and embeds and signs them in your app. You don't need to set
"Embed & Sign" yourself.

## Usage

Swift:

```swift
import mesibo
import MesiboUI
import MesiboCall
```

Objective-C:

```objc
#import <mesibo/Mesibo.h>
#import <MesiboUI/MesiboUI.h>
#import <MesiboCall/MesiboCall.h>
```

## Requirements

- iOS 15.0 or later.
- Devices: arm64.
- Simulator: arm64 only, which means a Mac with Apple silicon. Building for "Any iOS Simulator
  Device" also asks for x86_64; set `ARCHS=arm64` (or build for a specific simulator) if your
  build fails with "found architecture 'arm64', required architecture 'x86_64'".
- Calls and microphone/camera use: add `NSMicrophoneUsageDescription` and
  `NSCameraUsageDescription` to your app's Info.plist.

## License

See [LICENSE](LICENSE).

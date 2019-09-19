Bug-FBSnapshotTestCase-Xcode11
------------------------------

This repo demonstrates a bug that is affecting [ios-snapshot-test-case](https://github.com/uber/ios-snapshot-test-case) on Xcode 11 when building to older simulators ([#98](https://github.com/uber/ios-snapshot-test-case/issues/98)).

The error looks like this:
```
Bug-FBSnapshotTestCase-Xcode11.app (19107) encountered an error (Failed to load the test bundle. (Underlying error: The bundle “Bug-FBSnapshotTestCase-Xcode11Tests” couldn’t be loaded because it is damaged or missing necessary resources. The bundle is damaged or missing necessary resources. dlopen_preflight(/Users/amrox/Library/Developer/Xcode/DerivedData/Bug-FBSnapshotTestCase-Xcode11-eajvffidlmqqdibippfqkdungkis/Build/Products/Debug-iphonesimulator/Bug-FBSnapshotTestCase-Xcode11.app/PlugIns/Bug-FBSnapshotTestCase-Xcode11Tests.xctest/Bug-FBSnapshotTestCase-Xcode11Tests): Library not loaded: /usr/lib/swift/libswiftXCTest.dylib
  Referenced from: /Users/amrox/Library/Developer/Xcode/DerivedData/Bug-FBSnapshotTestCase-Xcode11-eajvffidlmqqdibippfqkdungkis/Build/Products/Debug-iphonesimulator/Bug-FBSnapshotTestCase-Xcode11.app/PlugIns/Bug-FBSnapshotTestCase-Xcode11Tests.xctest/Frameworks/FBSnapshotTestCase.framework/FBSnapshotTestCase
  Reason: no suitable image found.  Did find:
     /usr/lib/swift/libswiftXCTest.dylib: mach-o, but not built for iOS simulator))

```

## Steps to Reproduce

  1. Install Xcode 11 (I used GM1 11A419c, will re-test in GM2 when I can)
  1. Install `ios-snapshot-test-case` via `carthage bootstrap`
  1. Set up an simulator using iOS **11.4**. FWIW, I used an 'iPhone X' device
  1. Run the tests via Product -> Test or Cmd-U

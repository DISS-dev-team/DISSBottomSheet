# DISSBottomSheet


BottomSheet makes it easy to take advantage of the new UISheetPresentationController in SwiftUI with a simple .bottomSheet modifier on existing views.

1. [Requirements](#requirements)
2. [Integration](#integration)
3. [Usage](#usage)
    - [Presenting the Sheet](#presenting-the-sheet)
    - [Customizing the Sheet](#customizing-the-sheet)

## Requirements

- iOS 15+
- Xcode 13+

## Integration

### Swift Package Manager

BottomSheet can be added to your app via Swift Package Manager in Xcode using the following configuration:

```swift
dependencies: [
    .package(url: "https://github.com/DISS-dev-team/DISSBottomSheet.git", from: "1.0.0")
]
```

## Usage

To get started with BottomSheet, you'll need to import the framework first:

```swift
import DISSBottomSheet
```

### Presenting the Sheet

You can then apply the .bottomSheet modifier to any SwiftUI view, ensuring you attach a binding to the isPresented property - just like the standard .sheet modifier:

```swift
.mBottomSheet(isPresented: $isPresented) {
    Text("Hello, world!")
}
```

BottomSheet also supports passing an Optional item to it, displaying the sheet if the item is not nil:

```swift
.mBottomSheet(item: $item) {
    Text("Hello, world!")
}
```

### Customizing the Sheet

BottomSheet can be customized in the same way a UISheetPresentationController can be customized in UIKit. This is done by specifying additional properties in the modifier:

```swift
.mBottomSheet(
    isPresented: $isPresented,
    detents: [.medium(), .large()],
    largestUndimmedDetentIdentifier: .large,
    prefersGrabberVisible: true,
    prefersScrollingExpandsWhenScrolledToEdge: true,
    prefersEdgeAttachedInCompactHeight: false,
    widthFollowsPreferredContentSizeWhenEdgeAttached: false,
    onDismiss: { print("Dismissed") }
) {
    Text("Hello, world!")
}
```

For more information on UISheetPresentationController, read Apple's documentation: https://developer.apple.com/documentation/uikit/uisheetpresentationcontroller
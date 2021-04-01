*This is a forked package from [flutter_qr_code_scaner](https://github.com/SeasonLeee/flutter_qr_code_scaner)*


# flutter_qr_code_scaner

[![Pub](https://img.shields.io/pub/v/flutter_qr_code_scaner.svg)](https://pub.dartlang.org/packages/flutter_qr_code_scaner)
[![Awesome Flutter](https://img.shields.io/badge/Awesome-Flutter-blue.svg?longCache=true&style=flat-square)]()
[![Awesome Flutter](https://img.shields.io/badge/Platform-Android_iOS-blue.svg?longCache=true&style=flat-square)]()
[![License](https://img.shields.io/badge/License-MIT-blue.svg)](/LICENSE)

QR code (scan code &#x2F; picture) recognition （AndroidView&#x2F;UiKitView）

# features:
- place the code inside the square frame to get the information from QR code
- select QR code from your local library from the image picker inside the ScanView


## Getting Started

```dart
import 'package:flutter_qr_code_scaner/scan_view.dart';

class HomePage extends StatefulWidget {
  HomePage({Key key}) : super(key: key);

  @override
  _HomePageState createState() => new _HomePageState();
}

class _HomePageState extends State<HomePage> {
  String result = '';

  var scanResult;
  @override
  void initState() {
    super.initState();
  }

  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(
        title: const Text('Package example app'),
      ),
      body: Padding(
        padding: const EdgeInsets.symmetric(horizontal: 16),
        child: Column(
          mainAxisAlignment: MainAxisAlignment.center,
          crossAxisAlignment: CrossAxisAlignment.stretch,
          children: <Widget>[
            RaisedButton(
              onPressed: () async {
                String results = await Navigator.push( // waiting for the scan results
                  context,
                  MaterialPageRoute(
                    builder: (context) => ScanView(), // open the scan view
                  ),
                );

                if (results != null) {
                  setState(() {
                    result = results;
                  });
                }
              },
              child: Text("扫码/tap to scan"),
            ),
            Text(result), // display the scan results
          ],
        ),
      ),
    );
  }
} 
```

### For IOS
Opt-in to the embedded views preview by adding a boolean property to the app's Info.plist file with the key io.flutter.embedded_views_preview and the value YES.

	<key>io.flutter.embedded_views_preview</key>
	<string>YES</string>

And you will need provide the description of camera's permission to work properly, otherwise will crash your app.
``` 
  <key>NSCameraUsageDescription</key>
	<string>The porpuse explaining why you will use the camera</string>
```


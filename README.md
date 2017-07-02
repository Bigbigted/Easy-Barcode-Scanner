Easy Barcode Scanner
=================================

# Introduction

This is a very simple barcode scanner. There are no settings you need to handle.

"Easy Barcode Scanner" is a simple barcode scanner based on zBar Reader. The zBar Reader is implemented by C code so that it has high performance. With zBar, Easy Barcode Scanner can support QR Code, EAN-8, EAN-13, UPC-E, UPC-A, ISBN-10, ISBN-13, Interleaved 2 of 5, DataBar, DataBar Expanded, Codabar, Code 39, Code 93、Code 128 and PDF417. Data Matrix is supporting now, too.

"Easy Barcode Scanner" allows you to use any angle of camera and device to scan barcode, and you don't have to put barcode at the center of your camera. Becides, you can touch the camera preview to focus to a object, zoom in or zoom out. If you want to change your camera, only ONE click you need to do.

For Android Developer, you can use this Android SDK code below to scan barcode for your app:

    final Intent intent = new Intent("org.magiclen.barcodescanner.SCAN");
    final List<ResolveInfo> list = getPackageManager().queryIntentActivities(intent, PackageManager.MATCH_DEFAULT_ONLY);
    if (list.size() > 0) {
      intent.putExtra("SCAN_MODE", "QR_CODE_MODE"); // Can also use PRODUCT_MODE, SCAN_MODE, QR_CODE_MODE
      startActivityForResult(intent, 0);
    } else {
      // You may ask your user to install Easy Barcode Scanner
    }

To get the scanning result, you must override onActivityResult method:

    public void onActivityResult(final int requestCode, final int resultCode, final Intent data) {
      if (requestCode == 0) {
        if (resultCode == Activity.RESULT_OK) {
          final String result = data.getStringExtra("SCAN_RESULT"); // Get scanning result
          final String type = data.getStringExtra("code_type"); // Get code type
        } else {
          // Not scan any code yet
        }
      }
    }

Moreover, if you want to generate a QR code you can use this Android SDK code below:

    final Intent intent = new Intent("org.magiclen.barcodescanner.ENCODE");
    final List<ResolveInfo> list = getPackageManager().queryIntentActivities(intent, PackageManager.MATCH_DEFAULT_ONLY);
    if (list.size() > 0) {
      intent.putExtra("ENCODE_DATA", "Put some string you want to encode");
      startActivity(intent);
    } else {
      // You may ask your user to install Easy Barcode Scanner
    }

# License

    Copyright 2015-2016 magiclen.org

    Everyone can not use this program to do any business activity.

# Google Play

https://play.google.com/store/apps/details?id=org.magiclen.barcodescanner

# What's More?

Please check out our web page at

https://magiclen.org/easy-barcode-scanner/

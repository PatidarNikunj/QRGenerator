# QRGenerator
Using ZXing generate QR

GRADLE
-------------
    implementation 'com.google.zxing:core:3.3.0'
    implementation 'com.journeyapps:zxing-android-embedded:3.4.0'

JAVA
-------------
    Bitmap createBarcode(String data) throws WriterException {
        MultiFormatWriter barcodeWriter = new MultiFormatWriter();
        BitMatrix barcodeBitMatrix = barcodeWriter.encode(data, BarcodeFormat.QR_CODE, 500, 500);
        int width = barcodeBitMatrix.getWidth();
        int height = barcodeBitMatrix.getHeight();
        int[] pixels = new int[width * height];
        for (int y = 0; y < height; y++) {
            int offset = y * width;
            for (int x = 0; x < width; x++) {
                pixels[offset + x] = barcodeBitMatrix.get(x, y) ? BLACK : WHITE;
            }
        }
        Bitmap bitmap = Bitmap.createBitmap(width, height, Bitmap.Config.ARGB_8888);
        bitmap.setPixels(pixels, 0, width, 0, 0, width, height);
        return bitmap;
    }

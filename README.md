
============

## 效果图与示例 apk


>ZXing

```groovy
dependencies {
   
    compile 'org.chzz.qrcode:qrcode.1.0.0'
}
```
## 布局文件
>ZXing

```xml
<org.chzz.qrcode.zxing.ZXingView
    android:id="@+id/zxingview"
    style="@style/MatchMatch"
    app:qrcv_animTime="1000"
    app:qrcv_borderColor="@android:color/white"
    app:qrcv_borderSize="1dp"
    app:qrcv_cornerColor="@color/colorPrimaryDark"
    app:qrcv_cornerLength="20dp"
    app:qrcv_cornerSize="3dp"
    app:qrcv_maskColor="#33FFFFFF"
    app:qrcv_rectWidth="200dp"
    app:qrcv_scanLineColor="@color/colorPrimaryDark"
    app:qrcv_scanLineSize="1dp"
    app:qrcv_topOffset="90dp" />
```

## 自定义属性说明

属性名 | 说明 | 默认值
:----------- | :----------- | :-----------
qrcv_topOffset         | 扫描框距离 toolbar 底部的距离        | 90dp
qrcv_cornerSize         | 扫描框边角线的宽度        | 3dp
qrcv_cornerLength         | 扫描框边角线的长度        | 20dp
qrcv_cornerColor         | 扫描框边角线的颜色        | @android:color/white
qrcv_rectWidth         | 扫描框的宽度        | 200dp
qrcv_barcodeRectHeight         | 条码扫样式描框的高度        | 140dp
qrcv_maskColor         | 除去扫描框，其余部分阴影颜色        | #33FFFFFF
qrcv_scanLineSize         | 扫描线的宽度        | 1dp
qrcv_scanLineColor         | 扫描线的颜色「扫描线和默认的扫描线图片的颜色」        | @android:color/white
qrcv_scanLineMargin         | 扫描线距离上下或者左右边框的间距        | 0dp
qrcv_isShowDefaultScanLineDrawable         | 是否显示默认的图片扫描线「设置该属性后 qrcv_scanLineSize 将失效，可以通过 qrcv_scanLineColor 设置扫描线的颜色，避免让你公司的UI单独给你出特定颜色的扫描线图片」        | false
qrcv_customScanLineDrawable         | 扫描线的图片资源「默认的扫描线图片样式不能满足你的需求时使用，设置该属性后 qrcv_isShowDefaultScanLineDrawable、qrcv_scanLineSize、qrcv_scanLineColor 将失效」        | null
qrcv_borderSize         | 扫描边框的宽度        | 1dp
qrcv_borderColor         | 扫描边框的颜色        | @android:color/white
qrcv_animTime         | 扫描线从顶部移动到底部的动画时间「单位为毫秒」        | 1000
qrcv_isCenterVertical         | 扫描框是否垂直居中，该属性为true时会忽略 qrcv_topOffset 属性        | false
qrcv_toolbarHeight         | Toolbar 的高度，通过该属性来修正由 Toolbar 导致扫描框在垂直方向上的偏差        | 0dp
qrcv_isBarcode         | 是否是扫条形码        | false
qrcv_tipText         | 提示文案        | null
qrcv_tipTextSize         | 提示文案字体大小        | 14sp
qrcv_tipTextColor         | 提示文案颜色        | @android:color/white
qrcv_isTipTextBelowRect         | 提示文案是否在扫描框的底部        | false
qrcv_tipTextMargin         | 提示文案与扫描框之间的间距        | 20dp
qrcv_isShowTipTextAsSingleLine         | 是否把提示文案作为单行显示        | false
qrcv_isShowTipBackground         | 是否显示提示文案的背景        | false
qrcv_tipBackgroundColor         | 提示文案的背景色        | #22000000
qrcv_isScanLineReverse         | 扫描线是否来回移动        | true
qrcv_isShowDefaultGridScanLineDrawable         | 是否显示默认的网格图片扫描线        | false
qrcv_customGridScanLineDrawable         | 扫描线的网格图片资源        | nulll

## 接口说明

>QRCodeView

```java
/**
 * 设置扫描二维码的代理
 *
 * @param delegate 扫描二维码的代理
 */
public void setDelegate(Delegate delegate)

/**
 * 显示扫描框
 */
public void showScanRect()

/**
 * 隐藏扫描框
 */
public void hiddenScanRect()

/**
 * 打开摄像头开始预览，但是并未开始识别
 */
public void startCamera()

/**
 * 关闭摄像头预览，并且隐藏扫描框
 */
public void stopCamera()

/**
 * 延迟1.5秒后开始识别
 */
public void startSpot()

/**
 * 延迟delay毫秒后开始识别
 *
 * @param delay
 */
public void startSpotDelay(int delay)

/**
 * 停止识别
 */
public void stopSpot()

/**
 * 停止识别，并且隐藏扫描框
 */
public void stopSpotAndHiddenRect()

/**
 * 显示扫描框，并且延迟1.5秒后开始识别
 */
public void startSpotAndShowRect()

/**
 * 打开闪光灯
 */
public void openFlashlight()

/**
 * 关闭散光灯
 */
public void closeFlashlight()
```

>QRCodeView.Delegate   扫描二维码的代理

```java
/**
 * 处理扫描结果
 *
 * @param result
 */
void onScanQRCodeSuccess(String result)

/**
 * 处理打开相机出错
 */
void onScanQRCodeOpenCameraError()
```

>QRCodeDecoder  解析二维码图片

```java
/**
 * 解析二维码图片
 *
 * @param bitmap   要解析的二维码图片
 * @param delegate 解析二位码图片的代理
 */
public static void decodeQRCode(Bitmap bitmap, Delegate delegate)
```

>QRCodeDecoder.Delegate  解析二位码图片的代理

```java
/**
 * 解析二维码成功
 *
 * @param result 从二维码中解析的文本，如果该方法有被调用，result不会为空
 */
void onDecodeQRCodeSuccess(String result)

/**
 * 解析二维码失败
 */
void onDecodeQRCodeFailure()
```

>QRCodeEncoder  创建二维码图片

```java
/**
 * 创建黑色的二维码图片
 *
 * @param content
 * @param size     图片宽高，单位为px
 * @param delegate 创建二维码图片的代理
 */
public static void encodeQRCode(String content, int size, Delegate delegate)

/**
 * 创建指定颜色的二维码图片
 *
 * @param content
 * @param size     图片宽高，单位为px
 * @param color    二维码图片的颜色
 * @param delegate 创建二维码图片的代理
 */
public static void encodeQRCode(String content, int size, int color, Delegate delegate)

/**
 * 创建指定颜色的、带logo的二维码图片
 *
 * @param content
 * @param size     图片宽高，单位为px
 * @param color    二维码图片的颜色
 * @param logo     二维码图片的logo
 * @param delegate 创建二维码图片的代理
 */
public static void encodeQRCode(final String content, final int size, final int color, final Bitmap logo, final Delegate delegate)
```

>QRCodeEncoder.Delegate   创建二维码图片的代理

```java
/**
 * 创建二维码图片成功
 *
 * @param bitmap
 */
void onEncodeQRCodeSuccess(Bitmap bitmap)

/**
 * 创建二维码图片失败
 */
void onEncodeQRCodeFailure()
```

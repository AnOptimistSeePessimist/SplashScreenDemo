# SplashScreenDemo(包括 APP 图标生成)


##### 1.  下载
`npm i react-native-splash-screen --save` 或者 `yarn add react-native-splash-screen`

##### 2. 安装(link 不成功的话，建议查看官网手动安装,到达该步骤后 ios 配置已经完成，从第三步开始为 android 的额外配置)
`react-native link`

##### 3.  在 MainActivity.java 中添加以下代码：
```
package com.splashscreendemo;
// 添加以下代码
import android.os.Bundle;
import com.facebook.react.ReactActivity;
// 添加以下代码
import org.devio.rn.splashscreen.SplashScreen;

public class MainActivity extends ReactActivity {
    ...
    //添加以下代码
    @Override
    protected void onCreate(Bundle savedInstanceState) {
        SplashScreen.show(this);
        super.onCreate(savedInstanceState);
    }
    ...
}
```
##### 4. 在`android/app/src/main/res` 下创建 `layout` 文件夹，在 `layout` 文件夹下创建 `launch_screen.xml`

```
<?xml version="1.0" encoding="utf-8"?>
<LinearLayout xmlns:android="http://schemas.android.com/apk/res/android"
    android:orientation="vertical" android:layout_width="match_parent"
    android:layout_height="match_parent"
    android:background="@drawable/launch_screen">
</LinearLayout>
<!-- android:background="@drawable/launch_screen"  @drawable 代表的是 res 目录下的 drawable 文件夹
    launch_screen 表示启动屏的图片名字。
-->
```

##### 5. 在 `android/app/src/main/res/values` 文件夹下创建 `colors.xml`
```
<?xml version="1.0" encoding="utf-8"?>
<resources>
    <color name="status_bar_color">#000</color>
    <!-- 这句绝不能删除，这个配置可以用来设置主题 -->
    <color name="primary_dark">#000000</color>
</resources>
```
##### 6.  在 `android/app/src/main/res/values/styles.xml` 文件下加入以下代码：

```
<resources>
    <!-- Base application theme. -->
    <style name="AppTheme" parent="Theme.AppCompat.Light.NoActionBar">
        <!-- Customize your theme here. -->
        <!--加入以下代码，设置透明背景-->
        <item name="android:windowIsTranslucent">true</item>
    </style>
</resources>
```

##### 7. 在 AndroidManifest.xml 中加入如下代码(到此 android 额外配置完毕)：

```
<manifest xmlns:android="http://schemas.android.com/apk/res/android"
          // 添加以下这一行代码：
          xmlns:tools="http://schemas.android.com/tools"
    package="com.splashscreendemo">

    <uses-permission android:name="android.permission.INTERNET" />
    <uses-permission android:name="android.permission.SYSTEM_ALERT_WINDOW"/>

    <application
      // 添加以下这一行代码：
      tools:replace="android:allowBackup"
      android:name=".MainApplication"
      android:label="@string/app_name"
      android:icon="@mipmap/ic_launcher"
      android:allowBackup="false"
      android:theme="@style/AppTheme">
      <activity
        android:name=".MainActivity"
        android:label="@string/app_name"
        android:configChanges="keyboard|keyboardHidden|orientation|screenSize"
        android:windowSoftInputMode="adjustResize">
        <intent-filter>
            <action android:name="android.intent.action.MAIN" />
            <category android:name="android.intent.category.LAUNCHER" />
        </intent-filter>
      </activity>
      <activity android:name="com.facebook.react.devsupport.DevSettingsActivity" />
    </application>
</manifest>
```
##### 8.  生成 android 和 ios 的 app 图标和启动图相关网站，这里就差亲给张图来生成相关图标了：

> (推荐)1. 自动生成各种分辨率 app 图标和启动屏的网站(最好上传 1024 * 1024 像素的图片可以获得最佳效果)，图标一键生成网站：https://icon.wuruihong.com/

> 2.  Mac 中下面这款软件也不错：
![QQ20180520-204334.png](https://upload-images.jianshu.io/upload_images/11627544-94c528f23deaa780.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)




##### 9.1 android app 图标配置  和 android 启动屏配置，如下图所示：

![QQ20180520-161600.png](https://upload-images.jianshu.io/upload_images/11627544-2fb7f67961c28a09.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)


##### 9.2 iOS app 图标配置 和 启动屏配置：

###### 9.2.1 启动屏配置

（1）如下图所示，新建一个LaunchImage：
![QQ20180520-195017.png](https://upload-images.jianshu.io/upload_images/11627544-cf79358b6e34cc3f.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)


（2）设置新建的 LaunchImage 生效：

 ![QQ20180520-193832.png](https://upload-images.jianshu.io/upload_images/11627544-793e3d23a7dbb2e3.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

（3） LaunchImage所需的图片尺寸

![QQ20180520-205743.png](https://upload-images.jianshu.io/upload_images/11627544-b28933bc2bea9690.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)














# 第一步
在根目录的 build.gradle中 allprojects的repositories里添加jitpack依赖
maven { url 'https://jitpack.io' }
# 第二步
在app项目的build.gradle下的dependencies中添加IMO库依赖
implementation 'com.github.Seasonallan:LibFace:2.0'
# 第三步
在app项目的build.gradle下添加配置
1、在defaultConfig中添加
        ndk {
            abiFilters "x86", 'armeabi-v7a', 'armeabi'
        }
2、在android中添加
 repositories {
        flatDir {
            dirs 'libs'
        }
    }
    compileOptions {
        sourceCompatibility JavaVersion.VERSION_1_8
        targetCompatibility JavaVersion.VERSION_1_8
    }
        
# 第四步
在AndroidManifest.xml中添加摄像头权限和网络权限（IMO校验key是否正确需要）
<uses-permission android:name="android.permission.CAMERA" />
<uses-permission android:name="android.permission.INTERNET" />
# 第五步
使用IMoBridge调用IMO库API （见demo）
示例1 交互式活体检测：
 demo中的DemoFaceActionActivity
示例2 人脸登录：
 demo中的DemoFaceLoginActivity
示例3 静态活体检测：
 demo中的DemoFaceStaticActivity
 
# 注意事项
1、使用的时候要注意包名和key需要匹配
2、使用demo时，gradle版本不一致方案：
中断更新gradle
修改根目录下的build.gradle中的classpath "com.android.tools.build:gradle:4.0.1" 为你的版本
修改根目录下的gradle/wrapper/gradle-wrapper.properties中的distributionUrl为你的版本
关闭重启项目
3、混淆配置
-dontwarn com.aimall.**
-keep class com.aimall.**{*;}
-keep class org.opencv.**{*;}
 
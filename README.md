
## 安装

安装时msvc一定要勾选，因为若是build时选择mingw,在使用windeployqt.exe打包时会一直报: Unable to Find platform plugin (到QT5.14版本时仍存在这个问题),如下图

<img src="./img/qt-安装.png"/>

## 新建项目

### kit选择

必须选择msvc来编译；若是选择mingw，在使用windeployqt.exe打包时会一直报: Unable to Find platform plugin (到QT5.14版本时仍存在这个问题),如下图

<img src="./img/qt-新建项目-kit选择.png">

## 生成可执行文件

### 生成exe文件，并打包


1、 QtCreator 左下角改相应版本debug为release

2、 设置构建目录，F5运行

3、 $ cd F:\Qt\Qt5.14.0\5.14.0\msvc2015_64\bin   // 这是windeployqt.exe 所在目录

4、 $ windeployqt.exe E:\QT\chartthemes\chart.exe // 打包指定路径的exe文件

### 生成android可执行文件

#### 首先安装安卓相关的jdk，sdk和ndk

1、下载地址：http://www.qter.org/portal.php?mod=list&catid=18

   SDK下载地址： http://www.android-studio.org/

   sdk下载之后，执行SDK Manager.exe文件，下载Platform tools和tools

2、 打开 选项 | 设备 | Android | 设置安装路径

3、 点击设置ADV manager

##### 报错

1、 emulation currently requires hardware acceleration

解决：
  * 打开SDK manager 找到 intel x86 Emulator Accelerator (HAXM) 并安装
  * 进入目录F:\android-sdk-windows\extras\intel\Hardware_Accelerated_Execution_Manager，运行 intelhaxm-android.exe

2、创建AVD时一直报cannot create a AVD for ABI armeabi-v7a

解决：
  * 确认一下有没有相应的镜像，如armeabi-v7a需要的镜像是否存在
  * 若是仍旧失败，则直接打开sdk中的ADV manager进行创建

3、 Failed to install the following Android SDK packages as some licences have not been accepted.

解决：
  * 往下看看一下缺少哪个版本的Android SDK Build-Tools 然后打开SDK manager.exe去下载

4、 编译运行成功，但是没有生成apk

解决：
  * 需要设置 Build Android APK ，添加sign，若是没有就生成
  * 运行时修改debug为release
## 使用VSCODE 开发编译QT

点击 ctrl+shift+p 打开，c++UI配置


### 添加includePath

将QT相关头文件路径添加至includePath,如：

<img src="./img/c++ includePath.png">

${env:QTMINGW} 为环境变量QTMINGW的值,如 F:\Qt\Qt5.14.0\5.14.0\mingw73_64\include

当然也可以用MSVC的inclue包

目录下放置的是QT相关头文件

### 添加浏览路径

<img src="./img/c++ browsePath.png"/>
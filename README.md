# LearnQt
qt 学习笔记，跨平台开发
## 配置Gradle
1、修改Qt安装目录下各平台配置模板build.gradle和gradle-wrapper.properties文件，例如android_arm64_v8a，分别位于"I:\Qt\6.7.3\android_arm64_v8a\src\android\templates\"和"I:\Qt\6.7.3\android_arm64_v8a\src\3rdparty\gradle\gradle\wrapper\"下

build.gradle中repositories新增加mavenLocal()及maven { url 'https://maven.aliyun.com/repository/central' }等国内镜像源；


不删除google()及mavenCentral()，原因：国内源版本低


修改dependencies->classpath 'com.android.tools.build:gradle:8.6.0'版本        


修改dependencies->implementation 'androidx.core:core:1.13.1'版本        

gradle-wrapper.properties中修改distributionUrl=https\://mirrors.cloud.tencent.com/gradle/gradle-8.10.1-all.zip


## 配置QtCreator
1、构建含有多个子项目依赖的主项目时，手动确认下"运行目标"为主项目，否则无法生成apk文件


2、为apk签名

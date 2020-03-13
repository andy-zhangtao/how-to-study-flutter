<!-- vscode-markdown-toc -->
* 1. [下载android-studio](#android-studio)
	* 1.1. [配置代理](#)
	* 1.2. [安装SDK和AVD](#SDKAVD)
* 2. [安装Flutter](#Flutter)
* 3. [配置Emulators](#Emulators)
	* 3.1. [修复Mac错误](#Mac)
	* 3.2. [执行模拟器](#-1)

<!-- vscode-markdown-toc-config
	numbering=true
	autoSave=true
	/vscode-markdown-toc-config -->
<!-- /vscode-markdown-toc -->
# 如何配置开发环境(以mac为例)

##  1. <a name='android-studio'></a>下载android-studio

###  1.1. <a name=''></a>配置代理

在
    `Preferences`
        ->
            `Appearance & Behavior`
                ->
                `System Settings`
                    ->
                    `HTTP Proxy` 中选中 `Auto-detect proxy settings`，然后输入电子科大的代理地址:


```
mirrors.dormforce.net:80
```

点击`Clear Passwords`

![配置截图](https://tva1.sinaimg.cn/large/00831rSTly1gcs9oftsszj30ll03y0sz.jpg)

###  1.2. <a name='SDKAVD'></a>安装SDK和AVD

安装较高的SDK就可以了，如果代理设置正确的话，下载速度会很快。

##  2. <a name='Flutter'></a>安装Flutter

使用国内源:

``` shell
export PUB_HOSTED_URL=https://pub.flutter-io.cn
export FLUTTER_STORAGE_BASE_URL=https://storage.flutter-io.cn
```

下载Flutter SDK，然后在`PATH`中添加`flutter bin`路径，如下:

```
export PATH=~/Documents/flutter/bin:$PATH
```

##  3. <a name='Emulators'></a>配置Emulators

执行`flutter emulators`，可以查看当前环境设置成功的模拟器(第一次执行会有些慢)。

如下：

![展示模拟器](https://tva1.sinaimg.cn/large/00831rSTly1gcs9zdwi2tj30gy05qgmb.jpg)

###  3.1. <a name='Mac'></a>修复Mac错误

mac中运行模拟机时，可能会出现如下的错误:
```
无法打开“idevice_id”，因为无法验证开发者。
```

执行
```
sudo spctl --master-disable
sudo xattr -r -d com.apple.quarantine 【flutter解压后的目录】/flutter/bin/cache/artifacts/libimobiledevice/idevice_id
sudo xattr -r -d com.apple.quarantine 【flutter解压后的目录】/flutter/bin/cache/artifacts/libimobiledevice/idevicename
sudo xattr -r -d com.apple.quarantine 【flutter解压后的目录】/flutter/bin/cache/artifacts/libimobiledevice/idevicescreenshot
sudo xattr -r -d com.apple.quarantine 【flutter解压后的目录】/flutter/bin/cache/artifacts/libimobiledevice/idevicesyslog
sudo xattr -r -d com.apple.quarantine 【flutter解压后的目录】/flutter/bin/cache/artifacts/libimobiledevice/ideviceinfo
```
###  3.2. <a name='-1'></a>执行模拟器

执行
```
flutter emulators --launch apple_ios_simulator
```

会启动本地Iphone模拟器(第一次会有些慢)， 启动成功后，会看到一个iphone的主界面。

然后在`flutter/examples/hello_world`执行`flutter run`，就会看到`Hello world`的运行结果。

![](https://tva1.sinaimg.cn/large/00831rSTly1gcsa4ovms2j30u01hw0tt.jpg)

## 检查工具链

运行`flutter doctor`，会显示当前环境中是否存在问题。 `doctor`检测到问题之后，会回显出解决方案。

按照提示修复错误即可
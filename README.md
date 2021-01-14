# android_demo
学习android基本知识

### 一、Android体系

#### 1.Dalvik与ART

#### 2.Framework

#### 3.Standard libraries

#### 4.Application

### 二、Android App组件架构

**Activity、BroadCastReciever、ContentProvider和Service**

#### 1.四大组件如何协同工作

&emsp;Activity作为人机交互的第一界面，负责向用户展示信息和处理结果，而这些信息的来源，可以通过资源获取，也可以通过ContentProvider来获取用户应用信息，或是Service从后台计算、下载、处理的结果，当然也可以是通过BroadCastReciever获取到的广播信息。同时，Android系统还提供一个信使---Intent，作为信息传递的载体。组件与组件之间通过Intent来通信、传递信息、交换数据，正是通过这样一种方式，四大组件形成了各自独立而又紧密联系的关系，让整个Android系统"活"了起来。

#### 2.应用运行上下文对象

&emsp;Android系统的上下文对象，即在Context中，为我们封装了这样一个语境。Activity、Service、Application都是继承自Context。

### 三、Android系统源代码目录与系统目录

#### 1.Android系统源代码目录

&emsp;查看Android源代码的网站 `http://androidxref.com/`

```
- Makefile
- bionic 					(bionic C库)
- bootable 				(启动引导相关代码)
- build 					(存放系统编译规则等基础开发包配置)
- cts							(Google兼容性测试标准)
- dalvik					(dalvik虚拟机)
- development			(应用程序开发相关)
- external				(android使用的一些开源的模块)
- framworks				(Framwork框架核心)
- hardware 				(厂家硬件适配层HAL代码)
- out							(编译完成后的代码输出目录)
- packages				(应用程序包)
- prebuild				(x86和arm架构下预编译资源)
- sdk							(sdk及其模拟器)
- system					(底层文件系统库、应用及组件)
- vendor					(厂商定制代码)
```



Makefile解释:一个像Android这样的大型工程，它的源文件不计其数，不同的功能、模块，按类型分别放置在不同的目录中，这些模块通常会有一个叫Makefile的文件来进行管理。它定义了一系列规则来制定模块，哪些文件需要编译，以及这些文件按照怎样的顺序去编译。甚至，它还可以配置更复杂的功能操作，比如定义编译规则，打包规则等，因为Makefile就像一个shell脚本，不仅可以使用自己的语法，也能调用操作系统的命令。

#### 2.Android系统目录

+ root根目录**

```
|root@nikel:/ # ls -l
ls -l
dr-xr-xr-x root     root              2020-12-29 16:20 acct
drwxr-xr-x root     root              1970-01-01 08:00 bin
drwxrwx--- system   cache             2020-12-29 16:20 cache
lrwxrwxrwx root     root              1970-01-01 08:00 charger -> /sbin/healthd
dr-x------ root     root              2020-12-29 16:20 config
drwxr-xr-x root     root              1970-01-01 08:00 cust
drwxr-xr-x root     root              2020-12-29 16:20 custom
lrwxrwxrwx root     root              2020-12-29 16:20 d -> /sys/kernel/debug
drwxrwx--x system   system            2020-12-29 16:20 data
-rw-r--r-- root     root          733 1970-01-01 08:00 default.prop
drwxr-xr-x root     root              2020-12-29 16:20 dev
-rw-r--r-- root     root          127 1970-01-01 08:00 enableswap.sh
lrwxrwxrwx root     root              2020-12-29 16:20 etc -> /system/etc
-rw-r--r-- root     root         2550 1970-01-01 08:00 factory_init.project.rc
-rw-r--r-- root     root        20359 1970-01-01 08:00 factory_init.rc
-rw-r--r-- root     root        48541 1970-01-01 08:00 file_contexts
-rw-r----- root     root         3457 1970-01-01 08:00 fstab.mt6797
-rwxr-x--- root     root      1154896 1970-01-01 08:00 init
-rwxr-x--- root     root          674 1970-01-01 08:00 init.aee.rc
-rwxr-x--- root     root          430 1970-01-01 08:00 init.common_svc.rc
-rwxr-x--- root     root          764 1970-01-01 08:00 init.custom.rc
-rwxr-x--- root     root         1043 1970-01-01 08:00 init.environ.rc
-rwxr-x--- root     root         1002 1970-01-01 08:00 init.mal.rc
-rwxr-x--- root     root           37 1970-01-01 08:00 init.miui.cust.rc
-rwxr-x--- root     root         3740 1970-01-01 08:00 init.miui.early_boot.sh
-rwxr-x--- root     root           57 1970-01-01 08:00 init.miui.google_revenue_share.rc
-rwxr-x--- root     root           57 1970-01-01 08:00 init.miui.google_revenue_share_v2.rc
-rwxr-x--- root     root          359 1970-01-01 08:00 init.miui.nativedebug.rc
-rwxr-x--- root     root          545 1970-01-01 08:00 init.miui.post_boot.sh
-rwxr-x--- root     root         8818 1970-01-01 08:00 init.miui.rc
-rwxr-x--- root     root         5566 1970-01-01 08:00 init.modem.rc
-rwxr-x--- root     root        59241 1970-01-01 08:00 init.mt6797.rc
-rwxr-x--- root     root        48183 1970-01-01 08:00 init.mt6797.usb.rc
-rwxr-x--- root     root        19924 1970-01-01 08:00 init.project.rc
-rwxr-x--- root     root        27449 1970-01-01 08:00 init.rc
-rwxr-x--- root     root            1 1970-01-01 08:00 init.recovery.hardware.rc
-rwxr-x--- root     root          972 1970-01-01 08:00 init.recovery.mt6797.rc
-rwxr-x--- root     root         2249 1970-01-01 08:00 init.trace.rc
-rwxr-x--- root     root         1364 1970-01-01 08:00 init.trustonic.rc
-rwxr-x--- root     root         3885 1970-01-01 08:00 init.usb.rc
-rwxr-x--- root     root         1172 1970-01-01 08:00 init.volte.rc
-rwxr-x--- root     root          583 1970-01-01 08:00 init.xlog.rc
-rwxr-x--- root     root          301 1970-01-01 08:00 init.zygote32.rc
-rwxr-x--- root     root          615 1970-01-01 08:00 init.zygote64_32.rc
-rw-r--r-- root     root         1393 1970-01-01 08:00 meta_init.modem.rc
-rw-r--r-- root     root         1259 1970-01-01 08:00 meta_init.project.rc
-rw-r--r-- root     root        14391 1970-01-01 08:00 meta_init.rc
drwxr-xr-x root     system            2020-12-29 16:20 mnt
drwxrwx--x system   system            2010-01-01 09:15 nvcfg
drwxrwx--x root     system            2010-01-01 08:00 nvdata
drwxr-xr-x root     root              1970-01-01 08:00 oem
dr-xr-xr-x root     root              1970-01-01 08:00 proc
-rw-r--r-- root     root        13016 1970-01-01 08:00 property_contexts
drwxrwx--- system   system            2010-01-01 08:00 protect_f
drwxrwx--- system   system            2017-10-11 13:40 protect_s
drwx------ root     root              2019-03-21 03:03 root
drwxr-x--- root     root              1970-01-01 08:00 sbin
lrwxrwxrwx root     root              2020-12-29 16:20 sdcard -> /storage/self/primary
-rw-r--r-- root     root         1521 1970-01-01 08:00 seapp_contexts
-rw-r--r-- root     root           51 1970-01-01 08:00 selinux_version
-rw-r--r-- root     root       379542 1970-01-01 08:00 sepolicy
-rw-r--r-- root     root        14169 1970-01-01 08:00 service_contexts
drwxr-xr-x root     root              2020-12-29 16:20 storage
dr-xr-xr-x root     root              2020-12-29 16:20 sys
drwxr-xr-x root     root              1970-01-01 08:00 system
-rw-r--r-- root     root         5307 1970-01-01 08:00 ueventd.mt6797.rc
-rw-r--r-- root     root         5595 1970-01-01 08:00 ueventd.rc
-rw-r--r-- root     root          451 1970-01-01 08:00 unlock_key
lrwxrwxrwx root     root              2020-12-29 16:20 vendor -> /system/vendor
-rw-r--r-- root     root          524 1970-01-01 08:00 verity_key
```

+ /system/app/ 这里面放着系统的一些App

```
root@nikel:/system/app # ls -l
ls -l
drwxr-xr-x root     root              2019-03-21 03:05 AnalyticsCore
drwxr-xr-x root     root              2019-03-21 03:05 AntHalService
drwxr-xr-x root     root              2019-03-21 03:05 AntiSpam
drwxr-xr-x root     root              2019-03-21 03:05 AppIndexProvider
drwxr-xr-x root     root              2019-03-21 03:05 AtciService
drwxr-xr-x root     root              2019-03-21 03:05 AutoDialer
drwxr-xr-x root     root              2019-03-21 03:05 AutoTest
drwxr-xr-x root     root              2019-03-21 03:05 BSPTelephonyDevTool
drwxr-xr-x root     root              2019-03-21 03:05 BasicDreams
drwxr-xr-x root     root              2019-03-21 03:05 BatteryWarning
drwxr-xr-x root     root              2019-03-21 03:05 Bluetooth
drwxr-xr-x root     root              2019-03-21 03:05 BluetoothMidiService
drwxr-xr-x root     root              2019-03-21 03:05 BtTool
drwxr-xr-x root     root              2019-03-21 03:05 BugReport
drwxr-xr-x root     root              2019-03-21 03:05 CMASReceiver
drwxr-xr-x root     root              2019-03-21 03:05 Calculator
drwxr-xr-x root     root              2019-03-21 03:05 CalendarImporter
drwxr-xr-x root     root              2019-03-21 03:05 CameraAutoTest
drwxr-xr-x root     root              2019-03-21 03:05 CaptivePortalLogin
drwxr-xr-x root     root              2019-03-21 03:05 CatcherPatch
drwxr-xr-x root     root              2019-03-21 03:05 CertInstaller
drwxr-xr-x root     root              2019-03-21 03:05 CloudService
drwxr-xr-x root     root              2019-03-21 03:05 CmasEM
drwxr-xr-x root     root              2019-03-21 03:05 DeskClock
drwxr-xr-x root     root              2019-03-21 03:05 DeviceRegister
drwxr-xr-x root     root              2019-03-21 03:05 DocumentsUI
drwxr-xr-x root     root              2019-03-21 03:05 DrmProvider
drwxr-xr-x root     root              2019-03-21 03:05 Email
drwxr-xr-x root     root              2019-03-21 03:05 EngineerMode
drwxr-xr-x root     root              2019-03-21 03:05 EsnTrack
drwxr-xr-x root     root              2019-03-21 03:05 FM
drwxr-xr-x root     root              2019-03-21 03:05 FileExplorer
drwxr-xr-x root     root              2019-03-21 03:05 FingerprintEnroll
drwxr-xr-x root     root              2019-03-21 03:05 FingerprintServiceExtension
drwxr-xr-x root     root              2019-03-21 03:05 FusedLocationProvider
drwxr-xr-x root     root              2019-03-21 03:05 GFManager
drwxr-xr-x root     root              2019-03-21 03:05 GFTest
drwxr-xr-x root     root              2019-03-21 03:05 Galaxy4
drwxr-xr-x root     root              2019-03-21 03:05 GameCenter
drwxr-xr-x root     root              2019-03-21 03:05 Gba
drwxr-xr-x root     root              2019-03-21 03:05 GuardProvider
drwxr-xr-x root     root              2019-03-21 03:05 HTMLViewer
drwxr-xr-x root     root              2019-03-21 03:05 HetComm
drwxr-xr-x root     root              2019-03-21 03:05 HoloSpiralWallpaper
drwxr-xr-x root     root              2019-03-21 03:05 HybridAccessory
drwxr-xr-x root     root              2019-03-21 03:05 HybridPlatform
drwxr-xr-x root     root              2019-03-21 03:05 Joyose
drwxr-xr-x root     root              2019-03-21 03:05 KSICibaEngine
drwxr-xr-x root     root              2019-03-21 03:05 KeyChain
drwxr-xr-x root     root              2019-03-21 03:05 LiveWallpapers
drwxr-xr-x root     root              2019-03-21 03:05 LiveWallpapersPicker
drwxr-xr-x root     root              2019-03-21 03:05 LocationEM2
drwxr-xr-x root     root              2019-03-21 03:05 MDMLSample
drwxr-xr-x root     root              2019-03-21 03:05 MSA
drwxr-xr-x root     root              2019-03-21 03:05 MTKLogger
drwxr-xr-x root     root              2019-03-21 03:05 MTKThermalManager
drwxr-xr-x root     root              2019-03-21 03:05 MetokNLP
drwxr-xr-x root     root              2019-03-21 03:05 MiCloudSync
drwxr-xr-x root     root              2019-03-21 03:05 MiDrive
drwxr-xr-x root     root              2019-03-21 03:05 MiLinkService
drwxr-xr-x root     root              2019-03-21 03:05 MiRadio
drwxr-xr-x root     root              2019-03-21 03:05 MiWallpaper
drwxr-xr-x root     root              2019-03-21 03:05 Mipay
drwxr-xr-x root     root              2019-03-21 03:05 MiuiBluetooth
drwxr-xr-x root     root              2019-03-21 03:05 MiuiCompass
drwxr-xr-x root     root              2019-03-21 03:05 MiuiContentCatcher
drwxr-xr-x root     root              2019-03-21 03:05 MiuiDaemon
drwxr-xr-x root     root              2019-03-21 03:05 MiuiDriveMode
drwxr-xr-x root     root              2019-03-21 03:05 MiuiScanner
drwxr-xr-x root     root              2019-03-21 03:05 MiuiScreenRecorder
drwxr-xr-x root     root              2019-03-21 03:05 MiuiSuperMarket
drwxr-xr-x root     root              2019-03-21 03:05 MiuiVpnSdkManager
drwxr-xr-x root     root              2019-03-21 03:05 MtkFloatMenu
drwxr-xr-x root     root              2019-03-21 03:05 MusicFX
drwxr-xr-x root     root              2019-03-21 03:05 NoiseField
drwxr-xr-x root     root              2019-03-21 03:05 Notes
drwxr-xr-x root     root              2019-03-21 03:05 Omacp
drwxr-xr-x root     root              2019-03-21 03:05 PacProcessor
drwxr-xr-x root     root              2019-03-21 03:05 PaymentService
drwxr-xr-x root     root              2019-03-21 03:05 PhaseBeam
drwxr-xr-x root     root              2019-03-21 03:05 PhotoTable
drwxr-xr-x root     root              2019-03-21 03:05 PowerChecker
drwxr-xr-x root     root              2019-03-21 03:05 PowerKeeper
drwxr-xr-x root     root              2019-03-21 03:05 PrintSpooler
drwxr-xr-x root     root              2019-03-21 03:05 Provision
drwxr-xr-x root     root              2019-03-21 03:05 RawDataTest
drwxr-xr-x root     root              2019-03-21 03:05 RootPA
drwxr-xr-x root     root              2019-03-21 03:05 SYSOPT
drwxr-xr-x root     root              2019-03-21 03:05 SecurityAdd
drwxr-xr-x root     root              2019-03-21 03:05 SecurityCoreAdd
drwxr-xr-x root     root              2019-03-21 03:05 SelfRegister
drwxr-xr-x root     root              2019-03-21 03:05 SensorHub
drwxr-xr-x root     root              2019-03-21 03:05 SmsExtra
drwxr-xr-x root     root              2019-03-21 03:05 SogouInput
drwxr-xr-x root     root              2019-03-21 03:05 SoundRecorder
drwxr-xr-x root     root              2019-03-21 03:05 SystemHelper
drwxr-xr-x root     root              2019-03-21 03:05 ThemeManager
drwxr-xr-x root     root              2019-03-21 03:05 ThemeModule
drwxr-xr-x root     root              2019-03-21 03:05 TouchAssistant
drwxr-xr-x root     root              2019-03-21 03:05 TranslationService
drwxr-xr-x root     root              2019-03-21 03:05 Updater
drwxr-xr-x root     root              2019-03-21 03:05 UpnpService
drwxr-xr-x root     root              2019-03-21 03:05 UserDictionaryProvider
drwxr-xr-x root     root              2019-03-21 03:05 Userguide
drwxr-xr-x root     root              2019-03-21 03:05 VipAccount
drwxr-xr-x root     root              2019-03-21 03:05 VirtualSim
drwxr-xr-x root     root              2019-03-21 03:05 VoiceAssist
drwxr-xr-x root     root              2019-03-21 03:05 VsimCore
drwxr-xr-x root     root              2019-03-21 03:05 WMService
drwxr-xr-x root     root              2019-03-21 03:05 WebViewGoogle
drwxr-xr-x root     root              2019-03-21 03:05 XMCloudEngine
drwxr-xr-x root     root              2019-03-21 03:05 XMPass
drwxr-xr-x root     root              2019-03-21 03:05 XiaomiAccount
drwxr-xr-x root     root              2019-03-21 03:05 XiaomiServiceFramework
drwxr-xr-x root     root              2019-03-21 03:05 XiaomiSimActivateService
drwxr-xr-x root     root              2019-03-21 03:05 YGPS
drwxr-xr-x root     root              2019-03-21 03:05 YouDaoEngine
drwxr-xr-x root     root              2019-03-21 03:05 cit_nikel
drwxr-xr-x root     root              2019-03-21 03:05 greenguard
drwxr-xr-x root     root              2019-03-21 03:05 jjhome
drwxr-xr-x root     root              2019-03-21 03:05 limitedbatterycharge
drwxr-xr-x root     root              2019-03-21 03:05 mab
drwxr-xr-x root     root              2019-03-21 03:05 mcRegistry
drwxr-xr-x root     root              2019-03-21 03:05 miui
drwxr-xr-x root     root              2019-03-21 03:05 miuisystem
```



+ /system/bin/ 这里面主要放的是Linux自带的组件。

```
root@nikel:/system/bin # ls -l
ls -l
-rwxr-xr-x root     shell       35800 2019-03-21 03:05 6620_launcher
-rwxr-xr-x root     shell       10168 2019-03-21 03:05 6620_wmt_concurrency
-rwxr-xr-x root     shell       10168 2019-03-21 03:05 6620_wmt_lpbk
-rwxr-xr-x root     shell       79512 2019-03-21 03:05 AcdApiDaemon
-rwxr-xr-x root     shell       17980 2019-03-21 03:05 AudioSetParam
-rwxr-xr-x root     shell       10184 2019-03-21 03:05 MATest
-rwxr-xr-x root     shell       10280 2019-03-21 03:05 MTKNetworkDump
-rwxr-xr-x root     shell       13824 2019-03-21 03:05 MtkCodecService
-rwxr-xr-x root     shell      258048 2019-03-21 03:05 Test_Binary_P18.bin
-rwxr-xr-x root     shell       18360 2019-03-21 03:05 XMTEST
-rwxr-xr-x root     shell       10168 2019-03-21 03:05 aal
lrwxr-xr-x root     shell             2019-03-21 03:05 acpi -> toybox
-rwxr-xr-x root     shell       25868 2019-03-21 03:05 aee
-rwxr-xr-x root     shell       17676 2019-03-21 03:05 aee_archive
-rwxr-xr-x root     shell       21968 2019-03-21 03:05 aee_core_forwarder
-rwxr-xr-x root     shell       38232 2019-03-21 03:05 aee_dumpstate
-rwxr-xr-x root     shell       75768 2019-03-21 03:05 akmd09911
-rwxr-xr-x root     shell       79872 2019-03-21 03:05 akmd09912
-rwxr-xr-x root     shell       46876 2019-03-21 03:05 akmd8963
-rwxr-xr-x root     shell       38692 2019-03-21 03:05 akmd8975
-rwxr-xr-x root     shell         210 2019-03-21 03:05 am
-rwxr-xr-x root     shell       38552 2019-03-21 03:05 ami304d
lrwxr-xr-x root     shell             2019-03-21 03:05 app_process -> app_process64
-rwxr-xr-x root     shell       22072 2019-03-21 03:05 app_process32
-rwxr-xr-x root     shell       22456 2019-03-21 03:05 app_process64
-rwxr-xr-x root     shell       66512 2019-03-21 03:05 applypatch
-rwxr-xr-x root     shell         213 2019-03-21 03:05 appops
-rwxr-xr-x root     shell         215 2019-03-21 03:05 appwidget
-rwxr-xr-x root     shell      217644 2019-03-21 03:05 atci_service
-rwxr-xr-x root     shell       67672 2019-03-21 03:05 atcid
-rwxr-xr-x root     shell       39064 2019-03-21 03:05 atrace
-rwxr-xr-x root     shell       71352 2019-03-21 03:05 audiocmdservice_atci
-rwxr-xr-x root     shell       19128 2019-03-21 03:05 autobt
-rwxr-xr-x root     shell       42864 2019-03-21 03:05 autokd
-rwxr-xr-x root     shell       26496 2019-03-21 03:05 badblocks
lrwxr-xr-x root     shell             2019-03-21 03:05 basename -> toybox
-rwxr-xr-x root     shell       10096 2019-03-21 03:05 batterywarning
-rwxr-xr-x root     shell       55248 2019-03-21 03:05 bcc
-rwxr-xr-x root     shell       14224 2019-03-21 03:05 blkid
lrwxr-xr-x root     shell             2019-03-21 03:05 blockdev -> toybox
-rwxr-xr-x root     shell         199 2019-03-21 03:05 bmgr
-rwxr-xr-x root     shell       72296 2019-03-21 03:05 bmm050d
-rwxr-xr-x root     shell       17920 2019-03-21 03:05 boot_logo_updater
-rwxr-xr-x root     shell       71608 2019-03-21 03:05 bootanimation
-rwxr-xr-x root     shell         156 2019-03-21 03:05 bu
-rwxr-xr-x root     shell       10096 2019-03-21 03:05 bugreport
lrwxr-xr-x root     shell             2019-03-21 03:05 bzcat -> toybox
lrwxr-xr-x root     shell             2019-03-21 03:05 cal -> toybox
-rwxr-xr-x root     shell         606 2019-03-21 03:05 capture_audio.sh
lrwxr-xr-x root     shell             2019-03-21 03:05 cat -> toybox
-rwxr-xr-x root     shell       98120 2019-03-21 03:05 ccci_fsd
-rwxr-xr-x root     shell       77996 2019-03-21 03:05 ccci_mdinit
lrwxr-xr-x root     shell             2019-03-21 03:05 chcon -> toybox
lrwxr-xr-x root     shell             2019-03-21 03:05 chgrp -> toybox
lrwxr-xr-x root     shell             2019-03-21 03:05 chmod -> toybox
lrwxr-xr-x root     shell             2019-03-21 03:05 chown -> toybox
lrwxr-xr-x root     shell             2019-03-21 03:05 chroot -> toybox
lrwxr-xr-x root     shell             2019-03-21 03:05 cksum -> toybox
-rwxr-xr-x root     shell       59584 2019-03-21 03:05 clatd
lrwxr-xr-x root     shell             2019-03-21 03:05 clear -> toybox
lrwxr-xr-x root     shell             2019-03-21 03:05 cmp -> toybox
lrwxr-xr-x root     shell             2019-03-21 03:05 comm -> toybox
-rwxr-xr-x root     shell       10096 2019-03-21 03:05 consumerird
-rwxr-xr-x root     shell         207 2019-03-21 03:05 content
lrwxr-xr-x root     shell             2019-03-21 03:05 cp -> toybox
lrwxr-xr-x root     shell             2019-03-21 03:05 cpio -> toybox
-rwxr-xr-x root     shell       17976 2019-03-21 03:05 ctclient
lrwxr-xr-x root     shell             2019-03-21 03:05 cut -> toybox
lrwxr-xr-x root     shell             2019-03-21 03:05 dalvikvm -> dalvikvm64
-rwxr-xr-x root     shell       17920 2019-03-21 03:05 dalvikvm32
-rwxr-xr-x root     shell       14192 2019-03-21 03:05 dalvikvm64
lrwxr-xr-x root     shell             2019-03-21 03:05 date -> toybox
lrwxr-xr-x root     shell             2019-03-21 03:05 dd -> toolbox
-rwxr-xr-x root     shell       42496 2019-03-21 03:05 debuggerd
-rwxr-xr-x root     shell       47056 2019-03-21 03:05 debuggerd64
-rwxr-xr-x root     shell      112180 2019-03-21 03:05 dex2oat
lrwxr-xr-x root     shell             2019-03-21 03:05 df -> toolbox
-rwxr-xr-x root     shell      124764 2019-03-21 03:05 dhcp6c
-rwxr-xr-x root     shell       22016 2019-03-21 03:05 dhcp6ctl
-rwxr-xr-x root     shell      116380 2019-03-21 03:05 dhcp6s
-rwxr-xr-x root     shell      112736 2019-03-21 03:05 dhcpcd
lrwxr-xr-x root     shell             2019-03-21 03:05 dirname -> toybox
-rwxr-xr-x root     shell       71632 2019-03-21 03:05 dm_agent_binder
lrwxr-xr-x root     shell             2019-03-21 03:05 dmesg -> toybox
-rwxr-xr-x root     shell       10096 2019-03-21 03:05 dmlog
-rwxr-xr-x root     shell      173120 2019-03-21 03:05 dnsmasq
lrwxr-xr-x root     shell             2019-03-21 03:05 dos2unix -> toybox
-rwxr-xr-x root     shell      408016 2019-03-21 03:05 downloader
-rwxr-xr-x root     shell         156 2019-03-21 03:05 dpm
-rwxr-xr-x root     shell       99896 2019-03-21 03:05 drmserver
lrwxr-xr-x root     shell             2019-03-21 03:05 du -> toolbox
-rwxr-xr-x root     shell       59304 2019-03-21 03:05 dumpstate
-rwxr-xr-x root     shell       14264 2019-03-21 03:05 dumpsys
-rwxr-xr-x root     shell      212912 2019-03-21 03:05 e2fsck
lrwxr-xr-x root     shell             2019-03-21 03:05 echo -> toybox
lrwxr-xr-x root     shell             2019-03-21 03:05 egrep -> grep
-rwxr-xr-x root     shell       84680 2019-03-21 03:05 em_svr
-rwxr-xr-x root     shell      229176 2019-03-21 03:05 emdlogger1
-rwxr-xr-x root     shell      208680 2019-03-21 03:05 emdlogger3
-rwxr-xr-x root     shell          87 2019-03-21 03:05 emmc_ffu.sh
lrwxr-xr-x root     shell             2019-03-21 03:05 env -> toybox
-rwxr-xr-x root     shell      137600 2019-03-21 03:05 epdg_wod
-rwxr-xr-x root     shell       34672 2019-03-21 03:05 exfatfsck
lrwxr-xr-x root     shell             2019-03-21 03:05 expand -> toybox
lrwxr-xr-x root     shell             2019-03-21 03:05 expr -> toybox
-rwxr-xr-x root     shell      651936 2019-03-21 03:05 factory
lrwxr-xr-x root     shell             2019-03-21 03:05 fallocate -> toybox
lrwxr-xr-x root     shell             2019-03-21 03:05 false -> toybox
-rwxr-xr-x root     shell       34744 2019-03-21 03:05 fdpp
lrwxr-xr-x root     shell             2019-03-21 03:05 fgrep -> grep
lrwxr-xr-x root     shell             2019-03-21 03:05 find -> toybox
-rwxr-xr-x root     shell       38840 2019-03-21 03:05 fingerprintd
-rwxr-xr-x root     shell      100528 2019-03-21 03:05 flashlessd
lrwxr-xr-x root     shell             2019-03-21 03:05 free -> toybox
-rwxr-xr-x root     shell       67512 2019-03-21 03:05 fsck.f2fs
-rwxr-xr-x root     shell       46960 2019-03-21 03:05 fsck_msdos
-rwxr-xr-x root     shell       71728 2019-03-21 03:05 fsck_msdos_mtk
-rwxr-xr-x root     shell       13880 2019-03-21 03:05 fuelgauged
-rwxr-xr-x root     shell       15448 2019-03-21 03:05 fusiond
-rwxr-xr-x root     shell       10184 2019-03-21 03:05 gas_srv
-rwxr-xr-x root     shell       51152 2019-03-21 03:05 gatekeeperd
-rwxr-xr-x root     shell       34864 2019-03-21 03:05 ged_srv
-rwxr-xr-x root     shell       35232 2019-03-21 03:05 geomagneticd
lrwxr-xr-x root     shell             2019-03-21 03:05 getenforce -> toybox
lrwxr-xr-x root     shell             2019-03-21 03:05 getevent -> toolbox
lrwxr-xr-x root     shell             2019-03-21 03:05 getprop -> toybox
-rwxr-xr-x root     shell      169944 2019-03-21 03:05 goodixfingerprintd
-rwxr-xr-x root     shell       36288 2019-03-21 03:05 grep
lrwxr-xr-x root     shell             2019-03-21 03:05 groups -> toybox
-rwxr-xr-x root     shell       81076 2019-03-21 03:05 gsm0710muxd
-rwxr-xr-x root     shell       81068 2019-03-21 03:05 gsm0710muxdmd2
-rwxr-xr-x root     shell       10168 2019-03-21 03:05 guiext-server
-rwxr-xr-x root     shell       10096 2019-03-21 03:05 gzip
-rwxr-xr-x root     shell       13824 2019-03-21 03:05 hangdebug
lrwxr-xr-x root     shell             2019-03-21 03:05 head -> toybox
-rwxr-xr-x root     shell         213 2019-03-21 03:05 hid
-rwxr-xr-x root     shell      618552 2019-03-21 03:05 hostapd
-rwxr-xr-x root     shell       47056 2019-03-21 03:05 hostapd_cli
lrwxr-xr-x root     shell             2019-03-21 03:05 hostname -> toybox
lrwxr-xr-x root     shell             2019-03-21 03:05 hwclock -> toybox
lrwxr-xr-x root     shell             2019-03-21 03:05 id -> toybox
-rwxr-xr-x root     shell       30648 2019-03-21 03:05 idmap
lrwxr-xr-x root     shell             2019-03-21 03:05 ifconfig -> toybox
lrwxr-xr-x root     shell             2019-03-21 03:05 iftop -> toolbox
-rwxr-xr-x root     shell         194 2019-03-21 03:05 ime
-rwxr-xr-x root     shell         300 2019-03-21 03:05 init_atmel
lrwxr-xr-x root     shell             2019-03-21 03:05 inotifyd -> toybox
-rwxr-xr-x root     shell         203 2019-03-21 03:05 input
lrwxr-xr-x root     shell             2019-03-21 03:05 insmod -> toybox
-rwxr-x--- root     root          694 2019-03-21 03:05 install-recovery.sh
-rwxr-xr-x root     shell       76272 2019-03-21 03:05 installd
lrwxr-xr-x root     shell             2019-03-21 03:05 ioctl -> toolbox
lrwxr-xr-x root     shell             2019-03-21 03:05 ionice -> toolbox
-rwxr-xr-x root     shell      223552 2019-03-21 03:05 ip
-rwxr-xr-x root     shell      402648 2019-03-21 03:05 ip6tables
lrwxr-xr-x root     shell             2019-03-21 03:05 ip6tables-restore -> ip6tables
lrwxr-xr-x root     shell             2019-03-21 03:05 ip6tables-save -> ip6tables
-rwxr-xr-x root     shell      394144 2019-03-21 03:05 iptables
lrwxr-xr-x root     shell             2019-03-21 03:05 iptables-restore -> iptables
lrwxr-xr-x root     shell             2019-03-21 03:05 iptables-save -> iptables
-rwxr-xr-x root     shell      125088 2019-03-21 03:05 keystore
lrwxr-xr-x root     shell             2019-03-21 03:05 kill -> toybox
-rwxr-xr-x root     shell       26192 2019-03-21 03:05 kpoc_charger
-rwxr-xr-x root     shell       17920 2019-03-21 03:05 lcdc_screen_cap
-rwxr-xr-x root     shell         220 2019-03-21 03:05 lctautotest
-rwxr-xr-x root     shell      874960 2019-03-21 03:05 ld.mc
-rwxr-xr-x root     shell      195368 2019-03-21 03:05 linker
-rwxr-xr-x root     shell      274168 2019-03-21 03:05 linker64
-rwxr-xr-x root     shell       18296 2019-03-21 03:05 lmkd
lrwxr-xr-x root     shell             2019-03-21 03:05 ln -> toybox
lrwxr-xr-x root     shell             2019-03-21 03:05 load_policy -> toybox
lrwxr-xr-x root     shell             2019-03-21 03:05 log -> toolbox
-rwxr-xr-x root     shell       26488 2019-03-21 03:05 logcat
-rwxr-xr-x root     shell       79808 2019-03-21 03:05 logd
lrwxr-xr-x root     shell             2019-03-21 03:05 logname -> toybox
-rwxr-xr-x root     shell       22424 2019-03-21 03:05 logwrapper
lrwxr-xr-x root     shell             2019-03-21 03:05 losetup -> toybox
lrwxr-xr-x root     shell             2019-03-21 03:05 ls -> toolbox
-rwxr-xr-x root     shell       38568 2019-03-21 03:05 lsm303md
lrwxr-xr-x root     shell             2019-03-21 03:05 lsmod -> toybox
lrwxr-xr-x root     shell             2019-03-21 03:05 lsof -> toolbox
lrwxr-xr-x root     shell             2019-03-21 03:05 lsusb -> toybox
-rwxr-xr-x root     shell       38568 2019-03-21 03:05 magd
-rwxr-xr-x root     shell       14192 2019-03-21 03:05 make_ext4fs
-rwxr-xr-x root     shell       26712 2019-03-21 03:05 make_f2fs
-rwxr-xr-x root     shell        6072 2019-03-21 03:05 matv
-rwxr-xr-x root     shell      150136 2019-03-21 03:05 mbimd
-rwxr-xr-x root     shell       39016 2019-03-21 03:05 mc6420d
-rwxr-xr-x root     shell      731880 2019-03-21 03:05 mcDriverDaemon
-rwxr-xr-x root     shell       45560 2019-03-21 03:05 mcd
lrwxr-xr-x root     shell             2019-03-21 03:05 md5sum -> toybox
-rwxr-xr-x root     shell       10096 2019-03-21 03:05 md_ctrl
-rwxr-xr-x root     shell      291336 2019-03-21 03:05 md_monitor
-rwxr-xr-x root     shell      175240 2019-03-21 03:05 md_monitor_ctrl
-rwxr-xr-x root     shell      138628 2019-03-21 03:05 mdlogger
-rwxr-xr-x root     shell      850480 2019-03-21 03:05 mdnsd
-rwxr-xr-x root     shell         210 2019-03-21 03:05 media
-rwxr-xr-x root     shell       26168 2019-03-21 03:05 mediaserver
-rwxr-xr-x root     shell       10096 2019-03-21 03:05 memorydumper
-rwxr-xr-x root     shell       34632 2019-03-21 03:05 memsicd
-rwxr-xr-x root     shell       34640 2019-03-21 03:05 memsicd3416x
-rwxr-xr-x root     shell      616344 2019-03-21 03:05 meta_tst
-rwxr-xr-x root     shell      153404 2019-03-21 03:05 mfv_ut
-rwxr-xr-x root     shell       18288 2019-03-21 03:05 mitop
-rwxr-xr-x root     shell       26480 2019-03-21 03:05 miuindbg_post
-rwxr-xr-x root     shell       75800 2019-03-21 03:05 miuizip
lrwxr-xr-x root     shell             2019-03-21 03:05 mkdir -> toybox
-rwxr-xr-x root     shell       55248 2019-03-21 03:05 mke2fs
-rwxr-xr-x root     shell       28368 2019-03-21 03:05 mkexfatfs
lrwxr-xr-x root     shell             2019-03-21 03:05 mknod -> toybox
lrwxr-xr-x root     shell             2019-03-21 03:05 mkswap -> toybox
lrwxr-xr-x root     shell             2019-03-21 03:05 mktemp -> toybox
-rwxr-xr-x root     shell       14192 2019-03-21 03:05 mmc_ffu
-rwxr-xr-x root     shell       26224 2019-03-21 03:05 mmp
-rwxr-xr-x root     shell       64056 2019-03-21 03:05 mobile_log_d
lrwxr-xr-x root     shell             2019-03-21 03:05 modinfo -> toybox
-rwxr-xr-x root     shell         217 2019-03-21 03:05 monkey
lrwxr-xr-x root     shell             2019-03-21 03:05 more -> toybox
lrwxr-xr-x root     shell             2019-03-21 03:05 mount -> toolbox
lrwxr-xr-x root     shell             2019-03-21 03:05 mountpoint -> toybox
-rwxr-xr-x root     shell       10184 2019-03-21 03:05 msensord
-rwxr-xr-x root     shell       10096 2019-03-21 03:05 mtd
-rwxr-xr-x root     shell     1459592 2019-03-21 03:05 mtk_agpsd
-rwxr-xr-x root     shell       26176 2019-03-21 03:05 mtkmal
-rwxr-xr-x root     shell        1882 2019-03-21 03:05 mtkpwdump.sh
-rwxr-xr-x root     shell       14288 2019-03-21 03:05 mtkrild
-rwxr-xr-x root     shell       18384 2019-03-21 03:05 mtkrildmd2
-rwxr-xr-x root     shell       26672 2019-03-21 03:05 mtpd
-rwxr-xr-x root     shell       19992 2019-03-21 03:05 muxreport
lrwxr-xr-x root     shell             2019-03-21 03:05 mv -> toybox
lrwxr-xr-x root     shell             2019-03-21 03:05 nandread -> toolbox
-rwxr-xr-x root     shell       10112 2019-03-21 03:05 ndc
-rwxr-xr-x root     shell      350760 2019-03-21 03:05 netd
-rwxr-xr-x root     shell       59504 2019-03-21 03:05 netdiag
lrwxr-xr-x root     shell             2019-03-21 03:05 netstat -> toybox
lrwxr-xr-x root     shell             2019-03-21 03:05 newfs_msdos -> toolbox
lrwxr-xr-x root     shell             2019-03-21 03:05 nice -> toybox
lrwxr-xr-x root     shell             2019-03-21 03:05 nl -> toybox
lrwxr-xr-x root     shell             2019-03-21 03:05 nohup -> toybox
-rwxr-xr-x root     shell       26656 2019-03-21 03:05 nvram_agent_binder
-rwxr-xr-x root     shell       22296 2019-03-21 03:05 nvram_daemon
-rwxr-xr-x root     shell      215040 2019-03-21 03:05 oatdump
lrwxr-xr-x root     shell             2019-03-21 03:05 od -> toybox
-rwxr-xr-x root     shell       23632 2019-03-21 03:05 orientationd
-rwxr-xr-x root     shell       10096 2019-03-21 03:05 otp
lrwxr-xr-x root     shell             2019-03-21 03:05 paste -> toybox
lrwxr-xr-x root     shell             2019-03-21 03:05 patch -> toybox
-rwxr-xr-x root     shell       67072 2019-03-21 03:05 patchoat
-rwxr-xr-x root     shell       14192 2019-03-21 03:05 perf_native_test
lrwxr-xr-x root     shell             2019-03-21 03:05 pgrep -> toybox
lrwxr-xr-x root     shell             2019-03-21 03:05 pidof -> toybox
-rwxr-xr-x root     shell       43136 2019-03-21 03:05 ping
-rwxr-xr-x root     shell       47664 2019-03-21 03:05 ping6
lrwxr-xr-x root     shell             2019-03-21 03:05 pkill -> toybox
-rwxr-xr-x root     shell         489 2019-03-21 03:05 playback_audio.sh
-rwxr-xr-x root     shell         191 2019-03-21 03:05 pm
lrwxr-xr-x root     shell             2019-03-21 03:05 pmap -> toybox
-rwxr-xr-x root     shell       35312 2019-03-21 03:05 ppl_agent
-rwxr-xr-x root     shell      279888 2019-03-21 03:05 pppd
-rwxr-xr-x root     shell      288080 2019-03-21 03:05 pppd_dt
-rwxr-xr-x root     shell       10168 2019-03-21 03:05 pq
lrwxr-xr-x root     shell             2019-03-21 03:05 printenv -> toybox
lrwxr-xr-x root     shell             2019-03-21 03:05 printf -> toybox
lrwxr-xr-x root     shell             2019-03-21 03:05 prlimit -> toolbox
-rwxr-xr-x root     shell       39008 2019-03-21 03:05 program_binary_service
lrwxr-xr-x root     shell             2019-03-21 03:05 ps -> toolbox
lrwxr-xr-x root     shell             2019-03-21 03:05 pwd -> toybox
-rwxr-xr-x root     shell      283280 2019-03-21 03:05 racoon
-rwxr-xr-x root     shell       76816 2019-03-21 03:05 radvd
-rwxr-xr-x root     shell       18288 2019-03-21 03:05 rda
lrwxr-xr-x root     shell             2019-03-21 03:05 readlink -> toybox
lrwxr-xr-x root     shell             2019-03-21 03:05 realpath -> toybox
-rwxr-xr-x root     shell        6000 2019-03-21 03:05 reboot
lrwxr-xr-x root     shell             2019-03-21 03:05 renice -> toolbox
-rwxr-xr-x root     shell         188 2019-03-21 03:05 requestsync
-rwxr-xr-x root     shell       42864 2019-03-21 03:05 resize2fs
-rwxr-xr-x root     shell       10096 2019-03-21 03:05 resize_ext4
lrwxr-xr-x root     shell             2019-03-21 03:05 restorecon -> toybox
-rwxr-xr-x root     shell       14216 2019-03-21 03:05 rilproxy
lrwxr-xr-x root     shell             2019-03-21 03:05 rm -> toybox
lrwxr-xr-x root     shell             2019-03-21 03:05 rmdir -> toybox
lrwxr-xr-x root     shell             2019-03-21 03:05 rmmod -> toybox
lrwxr-xr-x root     shell             2019-03-21 03:05 route -> toybox
-rwxr-xr-x root     shell     5183680 2019-03-21 03:05 rs2spir
-rwxr-xr-x root     shell       13580 2019-03-21 03:05 rtt
-rwxr-x--- root     shell       14192 2019-03-21 03:05 run-as
lrwxr-xr-x root     shell             2019-03-21 03:05 runcon -> toybox
-rwxr-xr-x root     shell       34440 2019-03-21 03:05 s62xd
-rwxr-xr-x root     shell        6000 2019-03-21 03:05 schedtest
-rwxr-xr-x root     shell       14264 2019-03-21 03:05 screencap
-rwxr-xr-x root     shell       14200 2019-03-21 03:05 screencolor
-rwxr-xr-x root     shell      112640 2019-03-21 03:05 screenrecord
-rwxr-xr-x root     shell       30576 2019-03-21 03:05 sdcard
lrwxr-xr-x root     shell             2019-03-21 03:05 sed -> toybox
lrwxr-xr-x root     shell             2019-03-21 03:05 sendevent -> toolbox
-rwxr-xr-x root     shell       10096 2019-03-21 03:05 sensorservice
lrwxr-xr-x root     shell             2019-03-21 03:05 seq -> toybox
-rwxr-xr-x root     shell       18360 2019-03-21 03:05 service
-rwxr-xr-x root     shell       18360 2019-03-21 03:05 servicemanager
lrwxr-xr-x root     shell             2019-03-21 03:05 setenforce -> toybox
lrwxr-xr-x root     shell             2019-03-21 03:05 setprop -> toybox
lrwxr-xr-x root     shell             2019-03-21 03:05 setsid -> toybox
-rwxr-xr-x root     shell         178 2019-03-21 03:05 settings
-rwxr-xr-x root     shell      161736 2019-03-21 03:05 sgdisk
-rwxr-xr-x root     shell      289432 2019-03-21 03:05 sh
lrwxr-xr-x root     shell             2019-03-21 03:05 sha1sum -> toybox
-rwxr-xr-x root     shell       26648 2019-03-21 03:05 sink
lrwxr-xr-x root     shell             2019-03-21 03:05 sleep -> toybox
-rwxr-xr-x root     shell      128708 2019-03-21 03:05 slpd
-rwxr-xr-x root     shell         190 2019-03-21 03:05 sm
-rwxr-xr-x root     shell       10168 2019-03-21 03:05 sn
lrwxr-xr-x root     shell             2019-03-21 03:05 sort -> toybox
-rwxr-xr-x root     shell       22552 2019-03-21 03:05 source
-rwxr-xr-x root     shell     4630784 2019-03-21 03:05 spir2cl
lrwxr-xr-x root     shell             2019-03-21 03:05 split -> toybox
-rwxr-xr-x root     shell        6000 2019-03-21 03:05 spm_loader
-rwxr-xr-x root     shell       26288 2019-03-21 03:05 st480
lrwxr-xr-x root     shell             2019-03-21 03:05 start -> toolbox
lrwxr-xr-x root     shell             2019-03-21 03:05 stat -> toybox
-rwxr-xr-x root     shell      116380 2019-03-21 03:05 statusd
lrwxr-xr-x root     shell             2019-03-21 03:05 stop -> toolbox
-rwxr-xr-x root     shell       34672 2019-03-21 03:05 stp_dump3
lrwxr-xr-x root     shell             2019-03-21 03:05 strings -> toybox
-rwxr-xr-x root     shell       46976 2019-03-21 03:05 superumount
-rwxr-xr-x root     shell       14208 2019-03-21 03:05 surfaceflinger
-rwxr-xr-x root     shell         192 2019-03-21 03:05 svc
lrwxr-xr-x root     shell             2019-03-21 03:05 swapoff -> toybox
lrwxr-xr-x root     shell             2019-03-21 03:05 swapon -> toybox
lrwxr-xr-x root     shell             2019-03-21 03:05 sync -> toybox
lrwxr-xr-x root     shell             2019-03-21 03:05 sysctl -> toybox
lrwxr-xr-x root     shell             2019-03-21 03:05 tac -> toybox
lrwxr-xr-x root     shell             2019-03-21 03:05 tail -> toybox
lrwxr-xr-x root     shell             2019-03-21 03:05 tar -> toybox
lrwxr-xr-x root     shell             2019-03-21 03:05 taskset -> toybox
-rwxr-xr-x root     shell       92464 2019-03-21 03:05 tc
lrwxr-xr-x root     shell             2019-03-21 03:05 tee -> toybox
-rwxr-xr-x root     shell         172 2019-03-21 03:05 telecom
-rwxr-xr-x root     shell       10096 2019-03-21 03:05 terservice
-rwxr-xr-x root     shell       10096 2019-03-21 03:05 tertestclient
-rwxr-xr-x root     shell       32380 2019-03-21 03:05 thermal
-rwxr-xr-x root     shell       18152 2019-03-21 03:05 thermal_manager
-rwxr-xr-x root     shell       10096 2019-03-21 03:05 thermald
-rwxr-xr-x root     shell       13824 2019-03-21 03:05 thermalloadalgod
lrwxr-xr-x root     shell             2019-03-21 03:05 time -> toybox
lrwxr-xr-x root     shell             2019-03-21 03:05 timeout -> toybox
-rwxr-xr-x root     shell       10096 2019-03-21 03:05 tiny_mkswap
-rwxr-xr-x root     shell        6000 2019-03-21 03:05 tiny_swapoff
-rwxr-xr-x root     shell        6000 2019-03-21 03:05 tiny_swapon
-rwxr-xr-x root     shell      148184 2019-03-21 03:05 toolbox
lrwxr-xr-x root     shell             2019-03-21 03:05 top -> toolbox
lrwxr-xr-x root     shell             2019-03-21 03:05 touch -> toybox
-rwxr-xr-x root     shell      310800 2019-03-21 03:05 toybox
lrwxr-xr-x root     shell             2019-03-21 03:05 tr -> toybox
lrwxr-xr-x root     shell             2019-03-21 03:05 true -> toybox
lrwxr-xr-x root     shell             2019-03-21 03:05 truncate -> toybox
-rwxr-xr-x root     shell       42920 2019-03-21 03:05 tune2fs
-rwxr-xr-x root     shell       18288 2019-03-21 03:05 tzdatacheck
-rwxr-xr-x root     shell        3814 2019-03-21 03:05 uiautomator
lrwxr-xr-x root     shell             2019-03-21 03:05 umount -> toybox
lrwxr-xr-x root     shell             2019-03-21 03:05 uname -> toybox
-rwxr-x--- root     root        43480 2019-03-21 03:05 uncrypt
lrwxr-xr-x root     shell             2019-03-21 03:05 uniq -> toybox
lrwxr-xr-x root     shell             2019-03-21 03:05 unix2dos -> toybox
lrwxr-xr-x root     shell             2019-03-21 03:05 uptime -> toolbox
lrwxr-xr-x root     shell             2019-03-21 03:05 usleep -> toybox
-rwxr-xr-x root     shell       10112 2019-03-21 03:05 vdc
-rwxr-xr-x root     shell       13824 2019-03-21 03:05 viaradiooptions
-rwxr-xr-x root     shell       31888 2019-03-21 03:05 viarild
lrwxr-xr-x root     shell             2019-03-21 03:05 vmstat -> toybox
-rwxr-xr-x root     shell      543472 2019-03-21 03:05 vold
-rwxr-xr-x root     shell      560428 2019-03-21 03:05 volte_imcb
-rwxr-xr-x root     shell      710572 2019-03-21 03:05 volte_stack
-rwxr-xr-x root     shell     1255532 2019-03-21 03:05 volte_ua
-rwxr-xr-x root     shell       10096 2019-03-21 03:05 vsimd
-rwxr-xr-x root     shell       13900 2019-03-21 03:05 vtservice
lrwxr-xr-x root     shell             2019-03-21 03:05 watchprops -> toolbox
lrwxr-xr-x root     shell             2019-03-21 03:05 wc -> toybox
-rwxr-xr-x root     shell       34728 2019-03-21 03:05 wechatproxy
lrwxr-xr-x root     shell             2019-03-21 03:05 which -> toybox
lrwxr-xr-x root     shell             2019-03-21 03:05 whoami -> toybox
-rwxr-xr-x root     shell       22384 2019-03-21 03:05 wifi2agps
-rwxr-xr-x root     shell         190 2019-03-21 03:05 wm
-rwxr-xr-x root     shell       10096 2019-03-21 03:05 wmt_loader
-rwxr-xr-x root     shell      122608 2019-03-21 03:05 wpa_cli
-rwxr-xr-x root     shell     1806416 2019-03-21 03:05 wpa_supplicant
lrwxr-xr-x root     shell             2019-03-21 03:05 xargs -> toybox
-rwxr-xr-x root     shell       22016 2019-03-21 03:05 xlog
lrwxr-xr-x root     shell             2019-03-21 03:05 yes -> toybox
-rwxr-xr-x root     shell       75800 2019-03-21 03:05 zip_utils

```



+ /system/build.prop 这里记录的是系统的属性信息
+ /system/fonts/ 系统字体存放目录
+ /system/framworks/  系统核心文件、框架层
+ /system/lib/ 存放几乎所有的共享(.so)文件

```
root@nikel:/system/lib # ls -l 
ls -l 
-rw-r--r-- root     root         1660 2019-03-21 03:05 crtbegin_so.o
-rw-r--r-- root     root          620 2019-03-21 03:05 crtend_so.o
drwxr-xr-x root     root              2019-03-21 03:05 drm
drwxr-xr-x root     root              2019-03-21 03:05 egl
drwxr-xr-x root     root              2019-03-21 03:05 hw
-rw-r--r-- root     root       720976 2019-03-21 03:05 lib3a.so
-rw-r--r-- root     root        71292 2019-03-21 03:05 lib3a_sample.so
-rw-r--r-- root     root        75312 2019-03-21 03:05 libBnMtkCodec.so
-rw-r--r-- root     root       218628 2019-03-21 03:05 libCameraEffectJNI.so
-rw-r--r-- root     root        67208 2019-03-21 03:05 libClearMotionFW.so
-rw-r--r-- root     root        22240 2019-03-21 03:05 libDR.so
-rw-r--r-- root     root      1193672 2019-03-21 03:05 libDiracAPI_SHARED.so
-rw-r--r-- root     root       420296 2019-03-21 03:05 libEGL.so
-rw-r--r-- root     root        17916 2019-03-21 03:05 libETC1.so
-rw-r--r-- root     root       214592 2019-03-21 03:05 libFFTEm.so
-rw-r--r-- root     root        83652 2019-03-21 03:05 libFaceGrade.so
-rw-r--r-- root     root      3632468 2019-03-21 03:05 libFaceProc.so
-rw-r--r-- root     root       456160 2019-03-21 03:05 libGLES_trace.so
-rw-r--r-- root     root        34340 2019-03-21 03:05 libGLESv1_CM.so
-rw-r--r-- root     root        54820 2019-03-21 03:05 libGLESv2.so
lrw-r--r-- root     root              2019-03-21 03:05 libGLESv3.so -> libGLESv2.so
-rw-r--r-- root     root       294332 2019-03-21 03:05 libHEVCdec_sa.ca7.android.so
-rw-r--r-- root     root       308000 2019-03-21 03:05 libJeejenAisound.so
-rw-r--r-- root     root        34796 2019-03-21 03:05 libJniAtvService.so
-rw-r--r-- root     root        54972 2019-03-21 03:05 libJpgDecPipe.so
-rw-r--r-- root     root        38560 2019-03-21 03:05 libJpgEncPipe.so
-rw-r--r-- root     root     10858036 2019-03-21 03:05 libLLVM.so
-rw-r--r-- root     root        17980 2019-03-21 03:05 libMJCjni.so
-rw-r--r-- root     root        38508 2019-03-21 03:05 libMTKAudioTimeStretch.so
-rw-r--r-- root     root        58928 2019-03-21 03:05 libMcClient.so
-rw-r--r-- root     root        22064 2019-03-21 03:05 libMcRegistry.so
-rw-r--r-- root     root        13840 2019-03-21 03:05 libMiraVision_jni.so
-rw-r--r-- root     root        26196 2019-03-21 03:05 libMtkH264SecVdecTLCLib.so
-rw-r--r-- root     root        26196 2019-03-21 03:05 libMtkH264SecVencTLCLib.so
-rw-r--r-- root     root        26196 2019-03-21 03:05 libMtkH265SecVdecTLCLib.so
-rw-r--r-- root     root        67248 2019-03-21 03:05 libMtkOmxAdpcmDec.so
-rw-r--r-- root     root        67248 2019-03-21 03:05 libMtkOmxAdpcmEnc.so
-rw-r--r-- root     root        59024 2019-03-21 03:05 libMtkOmxAlacDec.so
-rw-r--r-- root     root        63112 2019-03-21 03:05 libMtkOmxApeDec.so
-rw-r--r-- root     root        26212 2019-03-21 03:05 libMtkOmxCore.so
-rw-r--r-- root     root       203456 2019-03-21 03:05 libMtkOmxFlacDec.so
-rw-r--r-- root     root        50816 2019-03-21 03:05 libMtkOmxG711Dec.so
-rw-r--r-- root     root        63260 2019-03-21 03:05 libMtkOmxGsmDec.so
-rw-r--r-- root     root       116396 2019-03-21 03:05 libMtkOmxMp3Dec.so
-rw-r--r-- root     root        63764 2019-03-21 03:05 libMtkOmxRawDec.so
-rw-r--r-- root     root       190716 2019-03-21 03:05 libMtkOmxVdecEx.so
-rw-r--r-- root     root       120920 2019-03-21 03:05 libMtkOmxVenc.so
-rw-r--r-- root     root       132792 2019-03-21 03:05 libMtkOmxVorbisEnc.so
-rw-r--r-- root     root        87612 2019-03-21 03:05 libMtkVideoSpeedEffect.so
-rw-r--r-- root     root        42552 2019-03-21 03:05 libMtkVideoTranscoder.so
-rw-r--r-- root     root        26184 2019-03-21 03:05 libOpenCLIcd.so
-rw-r--r-- root     root        17976 2019-03-21 03:05 libOpenMAXAL.so
-rw-r--r-- root     root        17976 2019-03-21 03:05 libOpenSLES.so
-rw-r--r-- root     root        23440 2019-03-21 03:05 libPQDCjni.so
-rw-r--r-- root     root        18408 2019-03-21 03:05 libPQjni.so
-rw-r--r-- root     root       264464 2019-03-21 03:05 libRS.so
-rw-r--r-- root     root       235068 2019-03-21 03:05 libRSCpuRef.so
-rw-r--r-- root     root       153136 2019-03-21 03:05 libRSDriver.so
-rw-r--r-- root     root       468680 2019-03-21 03:05 libRSDriver_mtk.so
-rw-r--r-- root     root       128560 2019-03-21 03:05 libRScpp.so
-rw-r--r-- root     root        13820 2019-03-21 03:05 libSonyIMX230PdafLibrary.so
-rw-r--r-- root     root        22148 2019-03-21 03:05 libSwJpgCodec.so
-rw-r--r-- root     root        34320 2019-03-21 03:05 lib_fpc_tac_shared.so
-rw-r--r-- root     root        13900 2019-03-21 03:05 lib_unique_id.so
-rw-r--r-- root     root       513792 2019-03-21 03:05 liba3m.so
-rw-r--r-- root     root       124624 2019-03-21 03:05 libaal.so
-rw-r--r-- root     root        14008 2019-03-21 03:05 libaal_cust.so
-rw-r--r-- root     root       300652 2019-03-21 03:05 libacdk.so
-rw-r--r-- root     root        22012 2019-03-21 03:05 libadvanced_crypto.so
-rw-r--r-- root     root        22012 2019-03-21 03:05 libadvanced_crypto_jni.so
-rw-r--r-- root     root        74964 2019-03-21 03:05 libaed.so
-rw-r--r-- root     root        13820 2019-03-21 03:05 libaed_ext.so
-rw-r--r-- root     root        22012 2019-03-21 03:05 libalsautils.so
-rw-r--r-- root     root       185972 2019-03-21 03:05 libamr_wrap.so
-rw-r--r-- root     root       144716 2019-03-21 03:05 libamrvt.so
-rw-r--r-- root     root        67180 2019-03-21 03:05 libandroid.so
-rw-r--r-- root     root       945224 2019-03-21 03:05 libandroid_runtime.so
-rw-r--r-- root     root       147468 2019-03-21 03:05 libandroid_servers.so
-rw-r--r-- root     root       169604 2019-03-21 03:05 libandroidfw.so
-rw-r--r-- root     root        26208 2019-03-21 03:05 libantradio.so
-rw-r--r-- root     root      5220584 2019-03-21 03:05 libarcsoft_beauty_shot.so
-rw-r--r-- root     root      3921768 2019-03-21 03:05 libart-compiler.so
-rw-r--r-- root     root      5657996 2019-03-21 03:05 libart.so
-rw-r--r-- root     root        13820 2019-03-21 03:05 libatciserv_jni.so
-rw-r--r-- root     root        46648 2019-03-21 03:05 libatvctrlservice.so
-rw-r--r-- root     root        30204 2019-03-21 03:05 libaudio-resampler.so
-rw-r--r-- root     root       429688 2019-03-21 03:05 libaudio_param_parser.so
-rw-r--r-- root     root        22120 2019-03-21 03:05 libaudiocompensationfilter.so
-rw-r--r-- root     root        34416 2019-03-21 03:05 libaudiocomponentengine.so
-rw-r--r-- root     root        38396 2019-03-21 03:05 libaudiocustparam.so
-rw-r--r-- root     root        26224 2019-03-21 03:05 libaudiodcrflt.so
-rw-r--r-- root     root        30636 2019-03-21 03:05 libaudioeffect_jni.so
-rw-r--r-- root     root       362128 2019-03-21 03:05 libaudioflinger.so
-rw-r--r-- root     root        13824 2019-03-21 03:05 libaudiomtkdcremoval.so
-rw-r--r-- root     root        96100 2019-03-21 03:05 libaudiopolicyenginedefault.so
-rw-r--r-- root     root        13880 2019-03-21 03:05 libaudiopolicymanager.so
-rw-r--r-- root     root       222836 2019-03-21 03:05 libaudiopolicymanagerdefault.so
-rw-r--r-- root     root        83624 2019-03-21 03:05 libaudiopolicyservice.so
-rw-r--r-- root     root       149040 2019-03-21 03:05 libaudioresampler.so
-rw-r--r-- root     root         5448 2019-03-21 03:05 libaudiosetting.so
-rw-r--r-- root     root        22064 2019-03-21 03:05 libaudiospdif.so
-rw-r--r-- root     root        30204 2019-03-21 03:05 libaudioutils.so
-rw-r--r-- root     root       206452 2019-03-21 03:05 libawb_wrap.so
-rw-r--r-- root     root        38448 2019-03-21 03:05 libbacktrace.so
-rw-r--r-- root     root        38504 2019-03-21 03:05 libbase.so
-rw-r--r-- root     root       366180 2019-03-21 03:05 libbcc.so
-rw-r--r-- root     root       222820 2019-03-21 03:05 libbcinfo.so
-rw-r--r-- root     root        63084 2019-03-21 03:05 libbessound_hd_mtk.so
-rw-r--r-- root     root       181884 2019-03-21 03:05 libbinder.so
-rw-r--r-- root     root       808444 2019-03-21 03:05 libblas.so
-rw-r--r-- root     root        95844 2019-03-21 03:05 libblisrc.so
-rw-r--r-- root     root        99916 2019-03-21 03:05 libblisrc32.so
-rw-r--r-- root     root        26112 2019-03-21 03:05 libbluetooth_hw_test.so
-rw-r--r-- root     root       102544 2019-03-21 03:05 libbluetooth_jni.so
-rw-r--r-- root     root        26144 2019-03-21 03:05 libbluetooth_mtk.so
-rw-r--r-- root     root        26416 2019-03-21 03:05 libbluetooth_mtk_pure.so
-rw-r--r-- root     root        17920 2019-03-21 03:05 libbluetooth_relayer.so
-rw-r--r-- root     root        17920 2019-03-21 03:05 libbluetoothem_mtk.so
-rw-r--r-- root     root        57520 2019-03-21 03:05 libbspatch.so
-rw-r--r-- root     root        13872 2019-03-21 03:05 libbt-vendor.so
-rw-r--r-- root     root        50804 2019-03-21 03:05 libbwc.so
-rw-r--r-- root     root       575088 2019-03-21 03:05 libc++.so
-rw-r--r-- root     root       684492 2019-03-21 03:05 libc.so
-rw-r--r-- root     root        94684 2019-03-21 03:05 libc2kril.so
-rw-r--r-- root     root        26356 2019-03-21 03:05 libc2kutils.so
-rw-r--r-- root     root       521836 2019-03-21 03:05 libcam.camadapter.so
-rw-r--r-- root     root       120376 2019-03-21 03:05 libcam.camshot.so
-rw-r--r-- root     root        46708 2019-03-21 03:05 libcam.client.facebeauty.so
-rw-r--r-- root     root       222784 2019-03-21 03:05 libcam.client.so
-rw-r--r-- root     root        18028 2019-03-21 03:05 libcam.cpuperf.so
-rw-r--r-- root     root        63032 2019-03-21 03:05 libcam.device1.so
-rw-r--r-- root     root        54840 2019-03-21 03:05 libcam.device3.so
-rw-r--r-- root     root        54860 2019-03-21 03:05 libcam.exif.so
-rw-r--r-- root     root        50756 2019-03-21 03:05 libcam.exif.v3.so
-rw-r--r-- root     root        22088 2019-03-21 03:05 libcam.feature.ot.so
-rw-r--r-- root     root        26212 2019-03-21 03:05 libcam.feature_utils.so
-rw-r--r-- root     root        22072 2019-03-21 03:05 libcam.featureio.pipe.panorama.so
-rw-r--r-- root     root        17976 2019-03-21 03:05 libcam.featureio.pipe.utility.so
-rw-r--r-- root     root        22068 2019-03-21 03:05 libcam.hal3a.v3.dng.so
-rw-r--r-- root     root        30260 2019-03-21 03:05 libcam.hal3a.v3.lsctbl.so
-rw-r--r-- root     root        55512 2019-03-21 03:05 libcam.hal3a.v3.nvram.so
-rw-r--r-- root     root       892160 2019-03-21 03:05 libcam.hal3a.v3.so
-rw-r--r-- root     root       431724 2019-03-21 03:05 libcam.halsensor.so
-rw-r--r-- root     root       215356 2019-03-21 03:05 libcam.iopipe.so
-rw-r--r-- root     root        70128 2019-03-21 03:05 libcam.jni.lomohaljni.so
-rw-r--r-- root     root       316984 2019-03-21 03:05 libcam.legacypipeline.so
-rw-r--r-- root     root        83504 2019-03-21 03:05 libcam.metadata.so
-rw-r--r-- root     root      1009256 2019-03-21 03:05 libcam.metadataprovider.so
-rw-r--r-- root     root       214148 2019-03-21 03:05 libcam.paramsmgr.so
-rw-r--r-- root     root        17968 2019-03-21 03:05 libcam.utils.cpuctrl.so
-rw-r--r-- root     root        26212 2019-03-21 03:05 libcam.utils.sensorlistener.so
-rw-r--r-- root     root        50736 2019-03-21 03:05 libcam.utils.so
-rw-r--r-- root     root        42604 2019-03-21 03:05 libcam.vhdr.so
-rw-r--r-- root     root        26212 2019-03-21 03:05 libcam.watermark.so
-rw-r--r-- root     root        26160 2019-03-21 03:05 libcam1_utils.so
-rw-r--r-- root     root       157284 2019-03-21 03:05 libcam3_app.so
-rw-r--r-- root     root       435820 2019-03-21 03:05 libcam3_hwnode.so
-rw-r--r-- root     root       136812 2019-03-21 03:05 libcam3_hwpipeline.so
-rw-r--r-- root     root       247344 2019-03-21 03:05 libcam3_pipeline.so
-rw-r--r-- root     root       149040 2019-03-21 03:05 libcam3_utils.so
-rw-r--r-- root     root        34404 2019-03-21 03:05 libcam_hwutils.so
-rw-r--r-- root     root        13820 2019-03-21 03:05 libcam_mmp.so
-rw-r--r-- root     root        13936 2019-03-21 03:05 libcam_platform.so
-rw-r--r-- root     root       124520 2019-03-21 03:05 libcam_utils.so
-rw-r--r-- root     root     16230528 2019-03-21 03:05 libcamalgo.so
-rw-r--r-- root     root        26164 2019-03-21 03:05 libcamdrv_imem.so
-rw-r--r-- root     root       105680 2019-03-21 03:05 libcamdrv_isp.so
-rw-r--r-- root     root        30316 2019-03-21 03:05 libcamdrv_tuning_mgr.so
-rw-r--r-- root     root        79412 2019-03-21 03:05 libcamdrv_twin.so
-rw-r--r-- root     root       181868 2019-03-21 03:05 libcamera_client.so
-rw-r--r-- root     root        36448 2019-03-21 03:05 libcamera_metadata.so
-rw-r--r-- root     root     20795700 2019-03-21 03:05 libcameracustom.so
-rw-r--r-- root     root       603848 2019-03-21 03:05 libcameraservice.so
-rw-r--r-- root     root        40076 2019-03-21 03:05 libccci_util.so
-rw-r--r-- root     root       241704 2019-03-21 03:05 libclcore.bc
-rw-r--r-- root     root       257264 2019-03-21 03:05 libclcore_debug.bc
-rw-r--r-- root     root       242232 2019-03-21 03:05 libclcore_neon.bc
-rw-r--r-- root     root        30272 2019-03-21 03:05 libcom_fingerprints_service.so
-rw-r--r-- root     root        50788 2019-03-21 03:05 libcommon_time_client.so
-rw-r--r-- root     root       536228 2019-03-21 03:05 libcommonpawrapper.so
-rw-r--r-- root     root        34304 2019-03-21 03:05 libcompiler_rt.so
-rw-r--r-- root     root        34436 2019-03-21 03:05 libcomutils.so
-rw-r--r-- root     root       674056 2019-03-21 03:05 libcrypto.so
-rw-r--r-- root     root       247424 2019-03-21 03:05 libcurl.so
-rw-r--r-- root     root        13840 2019-03-21 03:05 libcustom_jni.so
-rw-r--r-- root     root        70844 2019-03-21 03:05 libcustom_nvram.so
-rw-r--r-- root     root        17916 2019-03-21 03:05 libcustom_prop.so
-rw-r--r-- root     root        67304 2019-03-21 03:05 libcutils.so
-rw-r--r-- root     root        42752 2019-03-21 03:05 libcvsd_mtk.so
-rw-r--r-- root     root        26164 2019-03-21 03:05 libdcfdecoderjni.so
-rw-r--r-- root     root        62856 2019-03-21 03:05 libdidi_secure.so
-rw-r--r-- root     root        13872 2019-03-21 03:05 libdirect-coredump.so
-rw-r--r-- root     root         9492 2019-03-21 03:05 libdl.so
-rw-r--r-- root     root        34452 2019-03-21 03:05 libdngop.so
-rw-r--r-- root     root       550592 2019-03-21 03:05 libdpframework.so
-rw-r--r-- root     root       104036 2019-03-21 03:05 libdrmframework.so
-rw-r--r-- root     root        34640 2019-03-21 03:05 libdrmframework_jni.so
-rw-r--r-- root     root       602048 2019-03-21 03:05 libdrmmtkutil.so
-rw-r--r-- root     root        22136 2019-03-21 03:05 libdrmmtkwhitelist.so
-rw-r--r-- root     root       132708 2019-03-21 03:05 libeffecthal.base.so
-rw-r--r-- root     root        54892 2019-03-21 03:05 libeffecthal.cfb.so
-rw-r--r-- root     root        30316 2019-03-21 03:05 libeffecthal.jpg.so
-rw-r--r-- root     root        22064 2019-03-21 03:05 libeffects.so
-rw-r--r-- root     root        18008 2019-03-21 03:05 libem_audio_jni.so
-rw-r--r-- root     root        26356 2019-03-21 03:05 libem_bt_jni.so
-rw-r--r-- root     root        17936 2019-03-21 03:05 libem_gpio_jni.so
-rw-r--r-- root     root        30248 2019-03-21 03:05 libem_lte_jni.so
-rw-r--r-- root     root        17948 2019-03-21 03:05 libem_mbim_jni.so
-rw-r--r-- root     root        17916 2019-03-21 03:05 libem_modem_jni.so
-rw-r--r-- root     root        17996 2019-03-21 03:05 libem_sensor_jni.so
-rw-r--r-- root     root        13820 2019-03-21 03:05 libem_support_jni.so
-rw-r--r-- root     root        17920 2019-03-21 03:05 libem_usb_jni.so
-rw-r--r-- root     root        55344 2019-03-21 03:05 libem_wifi_jni.so
-rw-r--r-- root     root       173564 2019-03-21 03:05 libexif.so
-rw-r--r-- root     root        87340 2019-03-21 03:05 libexpat.so
-rw-r--r-- root     root        40764 2019-03-21 03:05 libext2_blkid.so
-rw-r--r-- root     root        17920 2019-03-21 03:05 libext2_com_err.so
-rw-r--r-- root     root        31040 2019-03-21 03:05 libext2_e2p.so
-rw-r--r-- root     root        22012 2019-03-21 03:05 libext2_profile.so
-rw-r--r-- root     root        22020 2019-03-21 03:05 libext2_uuid.so
-rw-r--r-- root     root       174132 2019-03-21 03:05 libext2fs.so
-rw-r--r-- root     root       197892 2019-03-21 03:05 libfamily_jni.so
-rw-r--r-- root     root       681552 2019-03-21 03:05 libfb.so
-rw-r--r-- root     root        34404 2019-03-21 03:05 libfdpp.so
-rw-r--r-- root     root        22020 2019-03-21 03:05 libfdpp_jni.so
-rw-r--r-- root     root        63184 2019-03-21 03:05 libfeature.face.so
-rw-r--r-- root     root        17976 2019-03-21 03:05 libfeature_cfb.so
-rw-r--r-- root     root        79472 2019-03-21 03:05 libfeature_eis.so
-rw-r--r-- root     root        17976 2019-03-21 03:05 libfeature_vfb.so
-rw-r--r-- root     root        26220 2019-03-21 03:05 libfeatureio.featurefactory.so
-rw-r--r-- root     root       124688 2019-03-21 03:05 libfgauge.so
-rw-r--r-- root     root        71248 2019-03-21 03:05 libfile_op.so
-rw-r--r-- root     root       124472 2019-03-21 03:05 libfilterfw.so
-rw-r--r-- root     root        17924 2019-03-21 03:05 libfilterpack_imageproc.so
-rw-r--r-- root     root        13868 2019-03-21 03:05 libfmcust.so
-rw-r--r-- root     root        46888 2019-03-21 03:05 libfmjni.so
-rw-r--r-- root     root        46964 2019-03-21 03:05 libfmjnicitlct.so
-rw-r--r-- root     root        21776 2019-03-21 03:05 libfpSensorImageCapture.so
-rw-r--r-- root     root        91412 2019-03-21 03:05 libfpdfpSensorExtension.so
-rw-r--r-- root     root       411184 2019-03-21 03:05 libft2.so
-rw-r--r-- root     root        30548 2019-03-21 03:05 libfusion.so
-rw-r--r-- root     root       265836 2019-03-21 03:05 libfvaudio_call.so
-rw-r--r-- root     root        30132 2019-03-21 03:05 libgabi++.so
-rw-r--r-- root     root        46772 2019-03-21 03:05 libgas.so
-rw-r--r-- root     root        22064 2019-03-21 03:05 libgatekeeper.so
-rw-r--r-- root     root        30280 2019-03-21 03:05 libged.so
-rw-r--r-- root     root       538432 2019-03-21 03:05 libgem.so
-rw-r--r-- root     root       106628 2019-03-21 03:05 libgetuiext.so
-rw-r--r-- root     root       137772 2019-03-21 03:05 libgf_algo.so
-rw-r--r-- root     root       124624 2019-03-21 03:05 libgf_hal.so
-rw-r--r-- root     root        91980 2019-03-21 03:05 libgifimage.so
-rw-r--r-- root     root        30396 2019-03-21 03:05 libgpu_aux.so
-rw-r--r-- root     root        22064 2019-03-21 03:05 libgralloc_extra.so
-rw-r--r-- root     root       423716 2019-03-21 03:05 libgui.so
-rw-r--r-- root     root       214332 2019-03-21 03:05 libh264enc_sa.ca7.so
-rw-r--r-- root     root       179988 2019-03-21 03:05 libh264enc_sb.ca7.so
-rw-r--r-- root     root        13820 2019-03-21 03:05 libhardware.so
-rw-r--r-- root     root        30244 2019-03-21 03:05 libhardware_legacy.so
-rw-r--r-- root     root       427620 2019-03-21 03:05 libharfbuzz_ng.so
-rw-r--r-- root     root        63084 2019-03-21 03:05 libhdrproc.so
-rw-r--r-- root     root        55248 2019-03-21 03:05 libhttpserver.so
-rw-r--r-- root     root        42564 2019-03-21 03:05 libhwm.so
-rw-r--r-- root     root       506432 2019-03-21 03:05 libhwui.so
-rw-r--r-- root     root      1501092 2019-03-21 03:05 libicui18n.so
-rw-r--r-- root     root      1148492 2019-03-21 03:05 libicuuc.so
-rw-r--r-- root     root         5360 2019-03-21 03:05 libimageio.so
-rw-r--r-- root     root       366304 2019-03-21 03:05 libimageio_plat_drv.so
-rw-r--r-- root     root       137080 2019-03-21 03:05 libimageio_plat_pipe.so
-rw-r--r-- root     root       255696 2019-03-21 03:05 libimagepipeline.so
-rw-r--r-- root     root        58980 2019-03-21 03:05 libimg_utils.so
-rw-r--r-- root     root        99968 2019-03-21 03:05 libimsma.so
-rw-r--r-- root     root       177848 2019-03-21 03:05 libimsma_rtp.so
-rw-r--r-- root     root        26256 2019-03-21 03:05 libimsma_socketwrapper.so
-rw-r--r-- root     root       128616 2019-03-21 03:05 libinput.so
-rw-r--r-- root     root       271920 2019-03-21 03:05 libinputflinger.so
-rw-r--r-- root     root        46648 2019-03-21 03:05 libinputservice.so
-rw-r--r-- root     root        13820 2019-03-21 03:05 libion.so
-rw-r--r-- root     root        17916 2019-03-21 03:05 libion_mtk.so
-rw-r--r-- root     root        36416 2019-03-21 03:05 libiprouteutil.so
-rw-r--r-- root     root     13260792 2019-03-21 03:05 libj2v8.so
-rw-r--r-- root     root       149172 2019-03-21 03:05 libja3m.so
-rw-r--r-- root     root       215964 2019-03-21 03:05 libjavacore.so
-rw-r--r-- root     root        98736 2019-03-21 03:05 libjavacrypto.so
-rw-r--r-- root     root        26160 2019-03-21 03:05 libjavastackimpl.so
-rw-r--r-- root     root      1158724 2019-03-21 03:05 libjeejenmsc.so
-rw-r--r-- root     root        51240 2019-03-21 03:05 libjhead.so
-rw-r--r-- root     root        13820 2019-03-21 03:05 libjni_load_serinum.so
-rw-r--r-- root     root        34508 2019-03-21 03:05 libjni_lomoeffect.so
-rw-r--r-- root     root        26692 2019-03-21 03:05 libjni_pq.so
-rw-r--r-- root     root       308804 2019-03-21 03:05 libjni_resource_drm.so
-rw-r--r-- root     root        13868 2019-03-21 03:05 libjnigraphics.so
-rw-r--r-- root     root       222716 2019-03-21 03:05 libjpeg.so
-rw-r--r-- root     root        17916 2019-03-21 03:05 libjtranscode.so
-rw-r--r-- root     root       104120 2019-03-21 03:05 libkeymaster1.so
-rw-r--r-- root     root        38448 2019-03-21 03:05 libkeymaster_messages.so
-rw-r--r-- root     root        17916 2019-03-21 03:05 libkeystore-engine.so
-rw-r--r-- root     root        50788 2019-03-21 03:05 libkeystore_binder.so
-rw-r--r-- root     root        13900 2019-03-21 03:05 liblic_divx.so
-rw-r--r-- root     root        13900 2019-03-21 03:05 liblic_s263.so
-rw-r--r-- root     root        34412 2019-03-21 03:05 liblog.so
-rw-r--r-- root     root        22012 2019-03-21 03:05 liblogwrap.so
-rw-r--r-- root     root       132824 2019-03-21 03:05 libm.so
-rw-r--r-- root     root        22012 2019-03-21 03:05 libm4u.so
-rw-r--r-- root     root        91776 2019-03-21 03:05 libmal.so
-rw-r--r-- root     root       137108 2019-03-21 03:05 libmal_datamngr.so
-rw-r--r-- root     root        46672 2019-03-21 03:05 libmal_epdga.so
-rw-r--r-- root     root        22092 2019-03-21 03:05 libmal_imsmngr.so
-rw-r--r-- root     root        38556 2019-03-21 03:05 libmal_mdmngr.so
-rw-r--r-- root     root        42792 2019-03-21 03:05 libmal_nwmngr.so
-rw-r--r-- root     root       232556 2019-03-21 03:05 libmal_rds.so
-rw-r--r-- root     root        79852 2019-03-21 03:05 libmal_rilproxy.so
-rw-r--r-- root     root        98400 2019-03-21 03:05 libmal_simmngr.so
-rw-r--r-- root     root        17916 2019-03-21 03:05 libmatv_cust.so
-rw-r--r-- root     root       444076 2019-03-21 03:05 libmdfx.so
-rw-r--r-- root     root        34436 2019-03-21 03:05 libmdloggerrecycle.so
-rw-r--r-- root     root        30204 2019-03-21 03:05 libmdnssd.so
-rw-r--r-- root     root       853640 2019-03-21 03:05 libmedia.so
-rw-r--r-- root     root       295820 2019-03-21 03:05 libmedia_jni.so
-rw-r--r-- root     root        26168 2019-03-21 03:05 libmedialogservice.so
-rw-r--r-- root     root        50840 2019-03-21 03:05 libmediandk.so
-rw-r--r-- root     root       755336 2019-03-21 03:05 libmediaplayerservice.so
-rw-r--r-- root     root        18000 2019-03-21 03:05 libmediatek_exceptionlog.so
-rw-r--r-- root     root        22116 2019-03-21 03:05 libmediautils.so
-rw-r--r-- root     root        13908 2019-03-21 03:05 libmemoryDumpEncoder.so
-rw-r--r-- root     root        34404 2019-03-21 03:05 libmemorydumper.so
-rw-r--r-- root     root        13820 2019-03-21 03:05 libmemtrack.so
-rw-r--r-- root     root       136812 2019-03-21 03:05 libmfllcore.so
-rw-r--r-- root     root        13908 2019-03-21 03:05 libmhalImageCodec.so
-rw-r--r-- root     root        63076 2019-03-21 03:05 libminikin.so
-rw-r--r-- root     root       614248 2019-03-21 03:05 libminiui.so
-rw-r--r-- root     root        17924 2019-03-21 03:05 libmiui_chromium_support.so
-rw-r--r-- root     root        17940 2019-03-21 03:05 libmiui_security.so
-rw-r--r-- root     root       128904 2019-03-21 03:05 libmiuibooster.so
-rw-r--r-- root     root       162136 2019-03-21 03:05 libmiuiclassproxy.so
-rw-r--r-- root     root        90624 2019-03-21 03:05 libmiuidiffpatcher.so
-rw-r--r-- root     root        17936 2019-03-21 03:05 libmiuiimageutilities.so
-rw-r--r-- root     root        51352 2019-03-21 03:05 libmiuinative.so
-rw-r--r-- root     root        79432 2019-03-21 03:05 libmiuindbg.so
-rw-r--r-- root     root        75444 2019-03-21 03:05 libmjc.so
-rw-r--r-- root     root        17996 2019-03-21 03:05 libmmprofile.so
-rw-r--r-- root     root        18012 2019-03-21 03:05 libmmprofile_jni.so
-rw-r--r-- root     root       136808 2019-03-21 03:05 libmmsdkservice.so
-rw-r--r-- root     root      2424216 2019-03-21 03:05 libmnl.so
-rw-r--r-- root     root      1754364 2019-03-21 03:05 libmorpho_easy_hdr.so
-rw-r--r-- root     root        66780 2019-03-21 03:05 libmorpho_hdr_checker.so
-rw-r--r-- root     root      1774852 2019-03-21 03:05 libmorpho_image_stab4.so
-rw-r--r-- root     root        13820 2019-03-21 03:05 libmorpho_memory_allocator.so
-rw-r--r-- root     root       341524 2019-03-21 03:05 libmorpho_panorama.so
-rw-r--r-- root     root       145028 2019-03-21 03:05 libmp3lame.so
-rw-r--r-- root     root       154124 2019-03-21 03:05 libmp4enc_sa.ca7.so
-rw-r--r-- root     root       197464 2019-03-21 03:05 libmp4enc_xa.ca7.so
-rw-r--r-- root     root        38664 2019-03-21 03:05 libmpe.driver.so
-rw-r--r-- root     root        26300 2019-03-21 03:05 libmpe.sensorlistener.so
-rw-r--r-- root     root        22116 2019-03-21 03:05 libmqsas.so
-rw-r--r-- root     root        17916 2019-03-21 03:05 libmrdump.so
-rw-r--r-- root     root        30308 2019-03-21 03:05 libmsbc_mtk.so
-rw-r--r-- root     root        26212 2019-03-21 03:05 libmt.so
-rw-r--r-- root     root        17996 2019-03-21 03:05 libmtcloader.so
-rw-r--r-- root     root        17992 2019-03-21 03:05 libmtk_drvb.so
-rw-r--r-- root     root        30308 2019-03-21 03:05 libmtk_mmutils.so
-rw-r--r-- root     root       186076 2019-03-21 03:05 libmtk_vt_service.so
-rw-r--r-- root     root       680564 2019-03-21 03:05 libmtk_vt_swip.so
-rw-r--r-- root     root        30800 2019-03-21 03:05 libmtk_vt_utils.so
-rw-r--r-- root     root        67264 2019-03-21 03:05 libmtk_vt_wrapper.so
-rw-r--r-- root     root       259644 2019-03-21 03:05 libmtkcam.featurepipe.streaming.so
-rw-r--r-- root     root        46596 2019-03-21 03:05 libmtkcamera_client.so
-rw-r--r-- root     root       239708 2019-03-21 03:05 libmtkjpeg.so
-rw-r--r-- root     root        18024 2019-03-21 03:05 libmtklimiter.so
-rw-r--r-- root     root        22144 2019-03-21 03:05 libmtkplayer.so
-rw-r--r-- root     root        18024 2019-03-21 03:05 libmtkshifter.so
-rw-r--r-- root     root        30320 2019-03-21 03:05 libmtksqlite3_android.so
-rw-r--r-- root     root        13820 2019-03-21 03:05 libmtksqlite3_custom.so
-rw-r--r-- root     root        91696 2019-03-21 03:05 libmtp.so
-rw-r--r-- root     root        67312 2019-03-21 03:05 libn3d3a.so
-rw-r--r-- root     root        17916 2019-03-21 03:05 libnativebridge.so
-rw-r--r-- root     root        18056 2019-03-21 03:05 libnativecheck-jni.so
-rw-r--r-- root     root        30208 2019-03-21 03:05 libnativehelper.so
-rw-r--r-- root     root        38448 2019-03-21 03:05 libnbaio.so
-rw-r--r-- root     root        17916 2019-03-21 03:05 libnetd_client.so
-rw-r--r-- root     root        22016 2019-03-21 03:05 libnetlink.so
-rw-r--r-- root     root        46596 2019-03-21 03:05 libnetutils.so
-rw-r--r-- root     root        77468 2019-03-21 03:05 libnl.so
-rw-r--r-- root     root        75620 2019-03-21 03:05 libnvram.so
-rw-r--r-- root     root        13820 2019-03-21 03:05 libnvram_daemon_callback.so
-rw-r--r-- root     root        13904 2019-03-21 03:05 libnvram_platform.so
-rw-r--r-- root     root        17996 2019-03-21 03:05 libnvram_sec.so
-rw-r--r-- root     root        30392 2019-03-21 03:05 libnvramagentclient.so
-rw-r--r-- root     root       170084 2019-03-21 03:05 liboctvm.so
-rw-r--r-- root     root        30212 2019-03-21 03:05 liboctvm_drv.so
-rw-r--r-- root     root       104036 2019-03-21 03:05 liboctvm_runtime.so
-rw-r--r-- root     root        22020 2019-03-21 03:05 liboctvm_utils.so
-rw-r--r-- root     root       235004 2019-03-21 03:05 libopus.so
-rw-r--r-- root     root      4071672 2019-03-21 03:05 libpac.so
-rw-r--r-- root     root        75276 2019-03-21 03:05 libpcre.so
-rw-r--r-- root     root      4228596 2019-03-21 03:05 libpdfium.so
-rw-r--r-- root     root        77276 2019-03-21 03:05 libperfservice.so
-rw-r--r-- root     root        26160 2019-03-21 03:05 libperfservicenative.so
-rw-r--r-- root     root       146140 2019-03-21 03:05 libpixelflinger.so
-rw-r--r-- root     root       153084 2019-03-21 03:05 libpng.so
-rw-r--r-- root     root        13824 2019-03-21 03:05 libpower.so
-rw-r--r-- root     root        17976 2019-03-21 03:05 libpowerkeeper_jni.so
-rw-r--r-- root     root        22116 2019-03-21 03:05 libpowermanager.so
-rw-r--r-- root     root       128516 2019-03-21 03:05 libpq_cust.so
-rw-r--r-- root     root        83528 2019-03-21 03:05 libpq_prot.so
-rw-r--r-- root     root        80376 2019-03-21 03:05 libpqservice.so
-rw-r--r-- root     root        17916 2019-03-21 03:05 libprocessgroup.so
-rw-r--r-- root     root       579188 2019-03-21 03:05 libprotobuf-cpp-full.so
-rw-r--r-- root     root        99956 2019-03-21 03:05 libprotobuf-cpp-lite.so
-rw-r--r-- root     root        50788 2019-03-21 03:05 libradio.so
-rw-r--r-- root     root        13820 2019-03-21 03:05 libradio_metadata.so
-rw-r--r-- root     root        58936 2019-03-21 03:05 libradioservice.so
-rw-r--r-- root     root        38416 2019-03-21 03:05 libreference-ril.so
-rw-r--r-- root     root        46648 2019-03-21 03:05 libresourcemanagerservice.so
-rw-r--r-- root     root        72888 2019-03-21 03:05 libril.so
-rw-r--r-- root     root       152572 2019-03-21 03:05 librilmtk.so
-rw-r--r-- root     root       152572 2019-03-21 03:05 librilmtkmd2.so
-rw-r--r-- root     root        83196 2019-03-21 03:05 librilproxy.so
-rw-r--r-- root     root        17916 2019-03-21 03:05 librilproxyutils.so
-rw-r--r-- root     root        17916 2019-03-21 03:05 librilutils.so
-rw-r--r-- root     root        38472 2019-03-21 03:05 librpc.so
-rw-r--r-- root     root        13820 2019-03-21 03:05 librrc.so
-rw-r--r-- root     root        48048 2019-03-21 03:05 librs_jni.so
-rw-r--r-- root     root       120652 2019-03-21 03:05 librtp_jni.so
-rw-r--r-- root     root        57876 2019-03-21 03:05 libsdk_patcher.so
-rw-r--r-- root     root        17920 2019-03-21 03:05 libsec_mem.so
-rw-r--r-- root     root        22244 2019-03-21 03:05 libsechook.so
-rw-r--r-- root     root        26192 2019-03-21 03:05 libsecurity_device_credential_sdk.so
-rw-r--r-- root     root        63124 2019-03-21 03:05 libselinux.so
-rw-r--r-- root     root        79464 2019-03-21 03:05 libsensorservice.so
-rw-r--r-- root     root        17968 2019-03-21 03:05 libserviceutility.so
-rw-r--r-- root     root        30308 2019-03-21 03:05 libshell.so
-rw-r--r-- root     root        17976 2019-03-21 03:05 libshell_jni.so
-rw-r--r-- root     root        51024 2019-03-21 03:05 libshowlogo.so
-rw-r--r-- root     root        13820 2019-03-21 03:05 libsigchain.so
-rw-r--r-- root     root       149120 2019-03-21 03:05 libsink.so
-rw-r--r-- root     root      4003740 2019-03-21 03:05 libskia.so
-rw-r--r-- root     root        22144 2019-03-21 03:05 libsoftkeymaster.so
-rw-r--r-- root     root        63224 2019-03-21 03:05 libsoftkeymasterdevice.so
-rw-r--r-- root     root        17916 2019-03-21 03:05 libsonic.so
-rw-r--r-- root     root       346308 2019-03-21 03:05 libsonivox.so
-rw-r--r-- root     root        38644 2019-03-21 03:05 libsoundpool.so
-rw-r--r-- root     root        50788 2019-03-21 03:05 libsoundtrigger.so
-rw-r--r-- root     root        58936 2019-03-21 03:05 libsoundtriggerservice.so
-rw-r--r-- root     root       132744 2019-03-21 03:05 libsource.so
-rw-r--r-- root     root       474340 2019-03-21 03:05 libspeech_enh_lib.so
-rw-r--r-- root     root        31648 2019-03-21 03:05 libspeexresampler.so
-rw-r--r-- root     root       410720 2019-03-21 03:05 libsqlite.so
-rw-r--r-- root     root        38396 2019-03-21 03:05 libsqlite_jni.so
-rw-r--r-- root     root       181808 2019-03-21 03:05 libssl.so
-rw-r--r-- root     root      2411688 2019-03-21 03:05 libstagefright.so
-rw-r--r-- root     root        58928 2019-03-21 03:05 libstagefright_amrnb_common.so
-rw-r--r-- root     root        30204 2019-03-21 03:05 libstagefright_avc_common.so
-rw-r--r-- root     root        13820 2019-03-21 03:05 libstagefright_enc_common.so
-rw-r--r-- root     root       116328 2019-03-21 03:05 libstagefright_foundation.so
-rw-r--r-- root     root        17924 2019-03-21 03:05 libstagefright_http_support.so
-rw-r--r-- root     root       161336 2019-03-21 03:05 libstagefright_httplive.so
-rw-r--r-- root     root       206404 2019-03-21 03:05 libstagefright_omx.so
-rw-r--r-- root     root       472892 2019-03-21 03:05 libstagefright_soft_aacdec.so
-rw-r--r-- root     root       497208 2019-03-21 03:05 libstagefright_soft_aacenc.so
-rw-r--r-- root     root       108152 2019-03-21 03:05 libstagefright_soft_amrdec.so
-rw-r--r-- root     root        71224 2019-03-21 03:05 libstagefright_soft_amrnbenc.so
-rw-r--r-- root     root       172060 2019-03-21 03:05 libstagefright_soft_amrwbenc.so
-rw-r--r-- root     root       370232 2019-03-21 03:05 libstagefright_soft_avcdec.so
-rw-r--r-- root     root       359332 2019-03-21 03:05 libstagefright_soft_avcenc.so
-rw-r--r-- root     root       165440 2019-03-21 03:05 libstagefright_soft_flacenc.so
-rw-r--r-- root     root        26168 2019-03-21 03:05 libstagefright_soft_g711dec.so
-rw-r--r-- root     root        34516 2019-03-21 03:05 libstagefright_soft_gsmdec.so
-rw-r--r-- root     root       489236 2019-03-21 03:05 libstagefright_soft_hevcdec.so
-rw-r--r-- root     root        79416 2019-03-21 03:05 libstagefright_soft_mp3dec.so
-rw-r--r-- root     root       116280 2019-03-21 03:05 libstagefright_soft_mpeg2dec.so
-rw-r--r-- root     root        99896 2019-03-21 03:05 libstagefright_soft_mpeg4dec.so
-rw-r--r-- root     root       132664 2019-03-21 03:05 libstagefright_soft_mpeg4enc.so
-rw-r--r-- root     root        30264 2019-03-21 03:05 libstagefright_soft_opusdec.so
-rw-r--r-- root     root        26168 2019-03-21 03:05 libstagefright_soft_rawdec.so
-rw-r--r-- root     root        30264 2019-03-21 03:05 libstagefright_soft_vorbisdec.so
-rw-r--r-- root     root       460420 2019-03-21 03:05 libstagefright_soft_vpxdec.so
-rw-r--r-- root     root       685624 2019-03-21 03:05 libstagefright_soft_vpxenc.so
-rw-r--r-- root     root       419584 2019-03-21 03:05 libstagefright_wfd.so
-rw-r--r-- root     root        22012 2019-03-21 03:05 libstagefright_yuv.so
-rw-r--r-- root     root        17968 2019-03-21 03:05 libstagefrighthw.so
-rw-r--r-- root     root       403400 2019-03-21 03:05 libstatic-webp.so
-rw-r--r-- root     root        21972 2019-03-21 03:05 libstdc++.so
-rw-r--r-- root     root       267940 2019-03-21 03:05 libsurfaceflinger.so
-rw-r--r-- root     root        13820 2019-03-21 03:05 libsurfaceflinger_ddmconnection.so
-rw-r--r-- root     root        22048 2019-03-21 03:05 libsuspend.so
-rw-r--r-- root     root        13820 2019-03-21 03:05 libsync.so
-rw-r--r-- root     root        38448 2019-03-21 03:05 libsysutils.so
-rw-r--r-- root     root       102924 2019-03-21 03:05 libteeclientjni.so
-rw-r--r-- root     root        13852 2019-03-21 03:05 libthemeutils_jni.so
-rw-r--r-- root     root        18048 2019-03-21 03:05 libthermalalgo.so
-rw-r--r-- root     root        26224 2019-03-21 03:05 libtimestretch.so
-rw-r--r-- root     root        26324 2019-03-21 03:05 libtinyalsa.so
-rw-r--r-- root     root        22172 2019-03-21 03:05 libtinycompress.so
-rw-r--r-- root     root        42676 2019-03-21 03:05 libtinyxml.so
-rw-r--r-- root     root        30352 2019-03-21 03:05 libtlcWidevineClassicDrm.so
-rw-r--r-- root     root        91848 2019-03-21 03:05 libtlcWidevineModularDrm.so
-rw-r--r-- root     root        34956 2019-03-21 03:05 libtouchfilter.so
-rw-r--r-- root     root        63116 2019-03-21 03:05 libudf.so
-rw-r--r-- root     root        91748 2019-03-21 03:05 libui.so
-rw-r--r-- root     root        67116 2019-03-21 03:05 libunwind.so
-rw-r--r-- root     root        50788 2019-03-21 03:05 liburee_meta_drmkeyinstall.so
-rw-r--r-- root     root        22012 2019-03-21 03:05 libusbhost.so
-rw-r--r-- root     root       104052 2019-03-21 03:05 libutils.so
-rw-r--r-- root     root       778856 2019-03-21 03:05 libvc1dec_sa.ca7.so
-rw-r--r-- root     root        39636 2019-03-21 03:05 libvcodec_cap.so
-rw-r--r-- root     root         9408 2019-03-21 03:05 libvcodec_oal.so
-rw-r--r-- root     root        63188 2019-03-21 03:05 libvcodec_utility.so
-rw-r--r-- root     root      1036656 2019-03-21 03:05 libvcodecdrv.so
-rw-r--r-- root     root       109720 2019-03-21 03:05 libviagpsrpc.so
-rw-r--r-- root     root       269228 2019-03-21 03:05 libviatelecom-withuim-ril.so
-rw-r--r-- root     root       300824 2019-03-21 03:05 libvie.so
-rw-r--r-- root     root        26476 2019-03-21 03:05 libvie_jni.so
-rw-r--r-- root     root       716236 2019-03-21 03:05 libvixl.so
-rw-r--r-- root     root       669908 2019-03-21 03:05 libvoicerecognition.so
-rw-r--r-- root     root        34932 2019-03-21 03:05 libvoicerecognition_jni.so
-rw-r--r-- root     root       121364 2019-03-21 03:05 libvorbisidec.so
-rw-r--r-- root     root       333812 2019-03-21 03:05 libvp8dec_sa.ca7.so
-rw-r--r-- root     root       263300 2019-03-21 03:05 libvp8enc_sa.ca7.so
-rw-r--r-- root     root       302764 2019-03-21 03:05 libvp9dec_sa.ca7.so
-rw-r--r-- root     root        17916 2019-03-21 03:05 libvsim-adaptor-client.so
-rw-r--r-- root     root        51280 2019-03-21 03:05 libvsim-client.so
-rw-r--r-- root     root        30308 2019-03-21 03:05 libvsim.so
-rw-r--r-- root     root        30324 2019-03-21 03:05 libvsimservice.so
-rw-r--r-- root     root        22192 2019-03-21 03:05 libvt_avsync.so
-rw-r--r-- root     root        14492 2019-03-21 03:05 libvt_custom.so
-rw-r--r-- root     root        22196 2019-03-21 03:05 libvt_socketbind.so
-rw-r--r-- root     root       490568 2019-03-21 03:05 libvtmal.so
-rw-r--r-- root     root       419448 2019-03-21 03:05 libwebrtc_audio_preprocessing.so
-rw-r--r-- root     root        17916 2019-03-21 03:05 libwebviewchromium_loader.so
-rw-r--r-- root     root        17924 2019-03-21 03:05 libwebviewchromium_plat_support.so
-rw-r--r-- root     root       125208 2019-03-21 03:05 libwifi-service.so
-rw-r--r-- root     root       177776 2019-03-21 03:05 libwilhelm.so
-rw-r--r-- root     root        22016 2019-03-21 03:05 libwpa_client.so
-rw-r--r-- root     root       198196 2019-03-21 03:05 libyoga.so
-rw-r--r-- root     root       108128 2019-03-21 03:05 libz.so
-rw-r--r-- root     root       572220 2019-03-21 03:05 mtk-ril.so
-rw-r--r-- root     root       572220 2019-03-21 03:05 mtk-rilmd2.so
-rw-r--r-- root     root       610740 2019-03-21 03:05 mtk-rilproxy.so
drwxr-xr-x root     root              2019-03-21 03:05 soundfx
-rw-r--r-- root     root       136776 2019-03-21 03:05 volte_imsm.so
```



+ /system/media/  保存系统提示音、系统铃声
+ /system/usr/ 该目录用来保存用户的配置。如键盘布局、共享、时区文件等
+ /data/app data目录包含了用户大部分数据信息。其中,/data/app/这个目录包含了用户安装的App或者升级的App
+ /data/data/ 这个目录应该是开发者访问最多的目录了。这里包含了App的数据、文件信息、数据库信息等，以包名的方式来区分各个应用
+ /data/system/ 这个目录包含了手机的各项系统信息



#### 3.Android App 文件目录



### 四、Android开发工具

#### 1.Android Studio

+ 配置 
  + JDK
+ 使用技巧
  + 更新 工具栏 SDK Manager 可以在 **AndroidDevTools**网站中找到最新的镜像地址和端口。

#### 2.ADB命令使用技巧

+ adb version 

```
Android Debug Bridge version 1.0.41
Version 29.0.5-5949299
Installed as /usr/local/bin/adb
```



+ adb shell 进入命令行
+ adb intall 应用程序
+ adb push source destination
+ adb pull remote local
+ adb shell 
  + logcat | grep ""
+ adb remount (重新挂在系统分区，使系统分区重新可写)
+ adb shell df 查看系统盘符
+ adb shell pm list package -f 输出所用已经安装的应用
+ adb shell input keyevent 模拟按键输入
+ adb shell input  touchscreen swipe 18 665 18 350 模拟滑动输入
+ adb shell dumpsys
+ adb shell am start -n 包名/包名 + 类名
+ adb shell screenrecord /sdcard/demo.mp4
+ adb reboot
+ adb命令来源
  + \system\core\toolbox和\frameworks\base\cmds就是我们所有ADB命令和Shell命令的来源了。


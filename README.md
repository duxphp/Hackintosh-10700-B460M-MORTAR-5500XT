# Hackintosh-10700-B460M-MORTAR-5500XT

适用于 10700 + B460M迫击炮(无wifi) + (5500//5600//5700)XT 黑苹果引导文件 

基于 OpenCore 0.7.8 版本，机型 Imac 20,1，系统 MacOS 12.2.1

本 EFI 参考其他基于 B460M 引导与查阅资料，去除不必要的驱动并更新到最新版本

集成 5X00XT 显卡温度显示传感器驱动

USB定制在15个端口内，只去除了主板神光USB，MacOS 反正无法使用

# 注意事项

本引导适用于 B460M 迫击炮主板，主板BIOS开启 D.T.M 一键黑苹果

该主板暂时无法获取风扇转速或等SMCSuperIO更新

本引导默认适用于i7 10700 CPU，i5与i9 请自行更换集显加速ID代码

集显用户请自行更改集显ID与增加HDMI注入代码

经实机测试 5500XT、5700XT等显卡不需要加入独显代码注入或ACPI方式的任何注入，MacOS12.2.1下实际跑分并无多大差别

注入 AirportBrcmFixup 使943602cs达到 1300M 连接速率但是需要关闭 节能 - 唤醒已供网络访问 该驱动会导致睡眠唤醒后蓝牙触控板异常( 尝试加入BlueToolFixup.kext 解决问题)

在27寸 4K 显示器下开机进入登录界面会默认保持 HIDPI 的默认分辨率(1080P)显示，登录系统后恢复系统设置分辨率，该问题经过更换显卡后问题依旧暂时无解，调查后该问题普遍出现于 5X00XT 与 6X00XT系列，但进入系统后不影响正常使用，注销后登录界面分辨率正常


# 本机配置

| 配置        | 型号                                          |
|-----------|---------------------------------------------|
| CPU       | intel i7 10700                              |
| 主板        | MSI MAG B460M MORTAR（无 WiFi）                |
| 显卡        | 华擎 AMD Radeon RX 5500 XT Challenger D 8G OC |
| 内存        | 金士顿 3200MHz 16G * 2                         |
| SSD       | 铠侠 RC10 500G NVME SSD                       |
| 机箱        | 蓝宝石NITRO M01 银角大王 (前面板双 USB 3.0)            |
| 电源        | 长城金牌 V5 500W 全模组                            |
| CPU 风扇    | 利民 AS120 Plus                               |
| WiFi + 蓝牙 | BCM943602CS (PCI+USB转接卡)                    |


# 目录浏览

```
└── EFI
    ├── BOOT
    │     └── BOOTx64.efi
    └── OC
        ├── ACPI
        │     ├── SSDT-AWAC.aml
        │     └── SSDT-PLUG.aml
        ├── Drivers
        │     ├── AudioDxe.efi
        │     ├── HfsPlus.efi
        │     ├── OpenCanopy.efi
        │     └── OpenRuntime.efi
        ├── Kexts
        │     ├── AppleALC.kext
        │     ├── Lilu.kext
        │     ├── LucyRTL8125Ethernet.kext
        │     ├── NVMeFix.kext
        │     ├── RadeonSensor.kext
        │     ├── SMCProcessor.kext
        │     ├── SMCRadeonGPU.kext
        │     ├── SMCSuperIO.kext
        │     ├── USBPorts.kext
        │     ├── VirtualSMC.kext
        │     ├── WhateverGreen.kext
        │     ├── AirportBrcmFixup.kext
        │     └── XHCI-unsupported.kext
        ├── OpenCore.efi
        ├── Resources
        │     ├── Audio
        │     ├── Font
        │     ├── Image
        │     └── Label
        ├── Tools
        │     └── OpenShell.efi
        └── config.plist

```


# 更新记录
2022-02-24
加入 BlueToolFixup.kext 补丁，无论 BCM 或 Intel 网卡 MACOS 12 需要该驱动解决蓝牙睡醒等问题
更换USB定制为 USBMap.kext

2022-02-19
注入声卡id为11，取消启动声卡注入

2022-02-18
基础版本，基于 OC 0.7.8



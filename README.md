# Hackintosh-10700-B460M-MORTAR-5500XT

适用于 10700 + B460M迫击炮(无wifi) + 5500XT 黑苹果引导文件 

基于 OpenCore 0.7.9 版本，机型 Imac 20,1，系统 MacOS 12.2.1

本 EFI 参考其他基于 B460M 引导与查阅资料，去除不必要的驱动并更新到最新版本

USB定制在15个端口内，只去除了主板神光USB，MacOS 反正无法使用

# 注意事项

本引导适用于 B460M 迫击炮主板，主板BIOS开启 D.T.M 一键黑苹果

该主板暂时无法获取风扇转速或等SMCSuperIO更新

本引导默认适用于i7 10700 CPU，i5与i9 请自行更换集显加速ID代码

集显用户如果睡眠有问题请将机型改为 macmini 并重新定制USB

经实机测试 5X00XT等显卡不需要加入独显代码注入或ACPI方式的任何注入，MacOS12.2.1下实际跑分并无多大差别

注入 AirportBrcmFixup 使943602cs达到 1300M 连接速率但是需要关闭 节能 - 唤醒已供网络访问

~~PCI-E 转接卡蓝牙会导致休眠唤醒蓝牙失效采用注入BCM蓝牙补丁方式解决~~
睡眠唤醒后会导致蓝牙失效，经过测试与查阅外网资料 94360CD原生为PCIe卡，其他94360系列大部分原生为M2接口，所以94360CD无任何问题，如果使用943602CS等转pice卡会导致睡眠后唤醒的问题

在27寸 4K 显示器下开机进入登录界面会默认保持 HIDPI 的默认分辨率(1080P)显示，登录系统后恢复系统设置分辨率，该问题经过更换显卡后问题依旧暂时无解，调查后该问题普遍出现于 5X00XT 与 6X00XT系列，但进入系统后不影响正常使用，注销后登录界面分辨率正常

更换RX560显卡后不会出现登录界面分辨率不一致问题，经过查找资料发现RX560为官网支持显卡

# 本机配置

| 配置        | 型号                                                          |
|-----------|-------------------------------------------------------------|
| CPU       | intel i7 10700                                              |
| 主板        | MSI MAG B460M MORTAR（无 WiFi）                                |
| 显卡        | 华擎 AMD Radeon RX 5500 XT Challenger D 8G OC |
| 内存        | 金士顿 3200MHz 16G * 2                                         |
| SSD       | 铠侠 RC10 500G NVME SSD                                       |
| 机箱        | 蓝宝石NITRO M01 银角大王 (前面板双 USB 3.0)                            |
| 电源        | 长城金牌 V5 500W 全模组                                            |
| CPU 风扇    | 利民 AS120 Plus                                               |
| WiFi + 蓝牙 | BCM94360CD (PCI+USB转接卡)                                     |


# 更新记录

2022-03-09
升级引导文件到0.7.9，升级驱动到最新版

2022-03-02
删除非必要驱动，重新恢复bios后usb定制失效，重新引入ACPI，只保留5500xt版本

2022-02-28
增加 rx5x0显卡配置，增加独显配置，默认为集显配置

2022-02-27
去除蓝牙补丁，经测试94360CD并没有该问题

2022-02-24
加入 BlueToolFixup.kext  BrcmPatchRAM3.kext 补丁，无论 BCM 或 Intel 网卡 MACOS 12 需要该驱动解决蓝牙睡醒等问题
更换USB定制为 USBMap.kext

2022-02-19
注入声卡id为11，取消启动声卡注入

2022-02-18
基础版本，基于 OC 0.7.8



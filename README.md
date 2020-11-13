# desktop_soyo_maxsun_H110_ql3x_ql2x_opencore_EFI

#### 介绍
台式机 梅捷H110（魔改H310或铭瑄H310 BIOS）QL3X（i7 7820HK 魔改U）黑苹果 efi

#### 说明

CPU：QL3X（魔改i7 7820HK，QL2X应该也一样适用），曾经在MacBookPro 14,1上使用,核显注入缓冲帧AAPL,ig-platform-id：591B0000（实际填写需反序）


实测:59120000，591B0000，19160000等缓冲帧都可以支持单显示器正常输出（如果出现紫屏可以用显示器EDID注入或者一键HiDPi脚本解决），所有尝试的缓冲帧都在NVRAM参数里面

结果多次优化，目前感觉最优选择是：
1.  启动参数加入  -disablegfxfirmware（由于主板ME问题导致睡眠异常，不加此参数会卡核显） igfxonln=1 （多个显示器强制上线，单显示器请无视）
2.  缓冲帧591B0000
3.  SMBIOS选择iMac19,1（很重要，否则双接口及唤醒始终不正常）VGA（主）+HDMI（副）两个接口工作正常



#### 硬件

| 部件 | 配置 | 备注 |
| :----:| :----: | :----: |
| CPU | ql3x | 魔改i7 7820HK，主板锁全核4.0g |
| 内存 | 16G  | DDR3单条 |
| 显卡 | HD630 | 可以仿冒HD530或UHD630 |
| 声卡 | ALC662 |   |
| 网卡 | realtek8139 |  百兆 |
| 硬盘 | SSD240G |    |
| 显示器 | BenQ19inch 1080p +梦想家32inch 2k |    |
| 主板核显接口 | VGA+HDMI+VESA | VESA接口似乎不好用，win10下也无效   |


#### 问题说明

1.  QL3X魔改U，无法睡眠，具体可参见B站UP主司波图视频。
2.  休眠唤醒后，HDMI显示器不显示，通过远程桌面可以看到，也就是有信号，怀疑是梅捷主板HDMI口唤醒供电不足，解决办法：打开偏好设置-显示器-按住option(Alt)键点击“检测显示器”(可能需要多次，本人最少需要两次)，可以唤醒HDMI接口显示器。
3.  主板网卡居然是8139百兆，黑果驱动要用rtl8100.kext，而且需要使用kext utility.app进行安装，否则可能掉驱动。

#### 特别感谢

1.  什么值得买：我叫马路啊
2.  B站：司波图、电脑乐园



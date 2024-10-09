下载好最新固件后，按住BOOT键（FN键）同时将硬件连接电脑，在终端用下面命令刷固件：

```
esptool.py --chip auto --port [PORT] write_flash -z 0 arcade.v0.9_mpy_v1.23.0.bin
```

**注意下载硬件对应版本的固件，EDU 版固件和 LITE 版固件不兼容。**

> 一下功能仅 LITE 版本支持，LITE 版本对应[开源版硬件](https://github.com/BlockCodeLab/arcade-lite)，方便大家自制出属于自己的硬件。

如果需要自定义显示屏和按键的 GPIO 配置，请编辑一个`io_config.py`文件，复制并修改下面的内容到文件中，然后将文件传入游戏机中。

```python
# io_config.py
#
# 显示屏 GPIO 默认配置
LCD = {
    # 显示屏背光
    "backlight": 21,
    # 显示屏 SCK
    "sck": 12,
    # 显示屏 MOSI
    "mosi": 11,
    # 显示屏 CS
    "cs": 10,
    # 显示屏 DC
    "dc": 45,
    # 显示屏 RESET
    "reset": 46,
    # 显示屏旋转，可用值【0 - 3】：0 和 2 是竖屏，1 和 3 是横屏
    "rotation": 3,
    # 显示屏颜色反转
    "inversion": True,
    # 显示屏颜色字节高低位交换，部分屏幕需要交换才能正常显示颜色
    "swap_color_bytes": True,
}

# 按键 GPIO 默认配置
Keys = {
    "up": 16,
    "right": 15,
    "down": 14,
    "left": 13,
    "fn": 0,
    "a": 39,
    "b": 5,
    "x": 9,
    "y": 4,
}
```

可以使用 `mpremote` 命令行工具或者 [Arduino Lab for MicroPython](https://labs.arduino.cc/en/labs/micropython)、Thonny 等软件将文件传入。

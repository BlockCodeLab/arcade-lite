下载好最新固件后，按住BOOT键（FN键）同时将硬件连接电脑，在终端用下面命令刷固件：

```
esptool.py --chip auto --port [PORT] write_flash -z 0 arcade_lite.v0.9_mpy_v1.23.0.bin
```

如果需要自定义显示屏和按键的 GPIO 配置，请编辑一个`io_config.py`文件，复制并修改下面的内容到文件中，然后将文件传入游戏机中。

```python
# io_config.py
#
# 显示屏 io 口配置
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
    # 显示屏颜色字节高低位交换，部分屏幕需要交换才能正常显示颜色
    "swap_color_bytes": True,
}

# 按键 io 口配置
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

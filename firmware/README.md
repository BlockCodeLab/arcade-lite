下载好最新固件后，按住BOOT键（FN键）同时将硬件连接电脑，在终端用下面命令刷固件：

```
esptool.py --chip auto --port [PORT] write_flash -z 0 arcade_lite.v0.9_mpy_v1.23.0.bin
```

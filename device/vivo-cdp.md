# vivo-CDP
## 特征:
1. 发布时间在2014-2015
2. 开发平台为CDP，board-id是<1 1>
3. 有特殊性的410设备，出厂版本是Andriid4.4.4，底层为32位。

## 支持设备:

| 型号 | 代号 | 面板 | 触控 | 主线 |
|------|------|------|------|------|
| vivo Y13L <br> vivo Y613F <br> vivo Y913 | pd1304 | nt35510s | edt | Y |
| vivo Y23L <br> vivo Y623 <br> vivo Y923 | pd1419 | nt35510s | goodix | Y |
| vivo Y27L <br> vivo Y627 <br> vivo Y927 | pd1410 | hx8394a | — | — |
| vivo Y28L <br> vivo Y628 <br> vivo Y928 | pd1403 | hx8389b | synaptics | P |

## 刷入说明
### 第一步.解锁bootloader
使用专用fastboot工具解锁
项目地址: [vivo解锁](https://github.com/Linux-On-QcomPhone/bbk_vivo_unlock/)

解锁命令:
```
fastboot bbk unlock_vivo
```
### 第二步.刷写64位底层
由于原厂是安卓4.4.4，底层的tz和hyp只能引导32位，不能启动64位内核
msm8916的早期设备是没有安全启动的，可以自由刷写底层分区。
可以把原厂的tz和hyp替换为dragonboard410c的tz和hyp，另外需要用lk1st替换原厂的aboot分区。
这里准备了pd1304和pd1419的底层，注意不要错刷，底层的rmp与sbl1不同，混用会砖！

底层采用一键刷机脚本刷机，解压后使用flash.bat即可刷入底层


### 第三步.刷写系统
1. 刷入emmc: 对于

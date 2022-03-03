## 0x00 Hardware
| Index | Name              | Model                   |
| ----- | ----------------- | ----------------------- |
| 1     | CPU               | i7-8700K                |
| 2     | Motherboard       | ROG MAXIMUS X CODE      |
| 3     | RAM               | G.Skill DDR4 3200 8GBx2 |
| 4     | Solid State Drive | SAMSUNG 970 EVO 256G    |
| 5     | Network Card      | BCM943602CS             |

## 0x01 Image

[macOS Big Sur 11.6.4 20G417](https://mp.weixin.qq.com/s/vqoyCM69cToEJNc4ul4DKQ)

使用 [balenaEthcher](https://www.balena.io/etcher)制作U盘

U盘制作好以后，使用DiskGenius软件，用EFI文件夹中的文件去替换U盘第一个分区（EFI）中对应文件夹（文件），记得备份原EFI

## 0x02 Bois

bois设置参考：[bois设置](https://apple.sqlsec.com/3-%E5%87%86%E5%A4%87%E5%B7%A5%E4%BD%9C/3-1.html#reloaded)

**CFG Lock**在CPU设置中

## 0x03 遇到的问题

1. 设置启动盘为U盘的第一个分区（OC引导）

2. USB必须定制：[USB定制教程](https://apple.sqlsec.com/6-%E5%AE%9E%E7%94%A8%E5%A7%BF%E5%8A%BF/6-1.html#reloaded)

3. 将系统从U盘写入磁盘后，无法启动（无限重启），此时改为U盘启动项为第二个分区，使用Clover引导可以启动，继续安装磁盘上的macOS，安装完成以后，再次切换为OC引导，至此完成系统的安装

4. 多系统引导：[参考](https://apple.sqlsec.com/5-%E5%AE%9E%E6%88%98%E6%BC%94%E7%A4%BA/5-6.html#reloaded)

   1. 安装好UEFI插件后，使用map命令查看硬盘表，（GPT的id可以通过**EasyUEFI** 辅助查看）

   2. 进入对应的盘符，使用 map > map.txt 保存

   3. config.plist  Misc-其他设置 Entries-自定义条目，新增一条

   4. for example

      ```bash
      Path:
      PciRoot(0x0)/Pci(0x1D,0x0)/Pci(0x0,0x0)/NVMe(0x1,BF-B2-B2-81-56-38-25-00)/HD(1,GPT,B3F36FFC-1803-45E9-BDEE-1922417EB517,0x800,0x96000)/\EFI\Microsoft\BOOT\bootmgfw.EFI
      Name:
      Windows
      Flavour:
      Windows:Windows	(前者对应name，后者对应图标)


​		5. 把OC拷贝到Mac盘的EFI文件夹中（BOOT文件夹不需要）

## 0x04 尚未解决的问题

1. 休眠问题

## 0x05 参考资料

1. [国光](https://apple.sqlsec.com/)
2. [EFI-Z390-ROG-MAXIMUS-XI-HERO-WIFI-i7-8700K](https://github.com/ttdevs/EFI-Z390-ROG-MAXIMUS-XI-HERO-WIFI-i7-8700K)
2. [OpenCore文档](https://dortania.github.io/OpenCore-Post-Install/)

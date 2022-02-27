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
2. 只有一个USB2.0接口可使用（待解决）
3. 将系统从U盘写入磁盘后，无法启动（无限重启），此时改为U盘启动项为第二个分区，使用Clover引导可以启动，继续安装磁盘上的macOS，安装完成以后，再次切换为OC引导，至此完成系统的安装

## 0x04 尚未解决的问题

1. 只有一个USB2.0可用
2. EFI未写入磁盘，且无法启动多系统
3. 休眠问题


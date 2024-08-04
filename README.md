# 内网穿透方案

## 背景介绍
在雏雁计划“基于计算机视觉的电梯客流量实时监测系统”中用到的内网穿透方案
考虑到本应用的实际使用场景应该要集中处理多场所拍摄画面，经过调研决定选用具有图传功能的高性价比ESP32-cam开发板将拍摄画面上传到公网IP的某些特定端口，以供后台访问做进一步处理。使用FRP内网穿透方案实现过程如下:

## 方案介绍
![](https://raw.githubusercontent.com/Mateogic/FRP/main/Images/frp.png)
## 实现过程
1. 使用ESP32-cam开发板将摄像头ov2640拍摄画面以mjpeg格式传输至内网某IP的80端口，完成该操作即可通过**内网**访问查看拍摄画面。

  ![](https://raw.githubusercontent.com/Mateogic/FRP/main/Images/1.png)
  ![](https://raw.githubusercontent.com/Mateogic/FRP/main/Images/1.1.png)

2. 配置FRPS服务器(腾讯云)

  ![](https://raw.githubusercontent.com/Mateogic/FRP/main/Images/2.png)

3. 配置FRPC客户端(中转设备)

  ![](https://raw.githubusercontent.com/Mateogic/FRP/main/Images/3.png)
  
4. 通过FRP内网穿透建立内网上述某IP的80端口与公网IP设定的7081端口映射，完成上述操作即可通过外网访问查看拍摄画面。

  ![](https://raw.githubusercontent.com/Mateogic/FRP/main/Images/4.png)
  ![](https://raw.githubusercontent.com/Mateogic/FRP/main/Images/4.1.png)

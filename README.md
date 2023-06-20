# 内网穿透方案

## 背景介绍
在雏雁计划“基于计算机视觉的电梯客流量实时监测系统”中用到的内网穿透方案
考虑到本应用的实际使用场景应该要集中处理多场所拍摄画面，经过调研决定选用具有图传功能的高性价比ESP32-cam开发板将拍摄画面上传到公网IP的某些特定端口，以供后台访问做进一步处理。使用FRP内网穿透方案实现过程如下:

## 方案介绍
![](https://gitee.com/Mateogic/IntranetPenetration/raw/master/Images/frp%E5%86%85%E7%BD%91%E7%A9%BF%E9%80%8F%E7%A4%BA%E6%84%8F%E5%9B%BE.png)
## 实现过程
1. #### 使用ESP32-cam开发板将摄像头ov2640拍摄画面以mjpeg格式传输至内网某IP的80端口，完成该操作即可通过**内网**访问查看拍摄画面。

  ![](https://gitee.com/Mateogic/IntranetPenetration/raw/master/Images/(1)esp32-cam%E5%BC%80%E5%8F%91%E6%9D%BF%E5%B0%86%E6%91%84%E5%83%8F%E5%A4%B4ov2640%E6%8B%8D%E6%91%84%E7%94%BB%E9%9D%A2%E4%BB%A5mjpeg%E6%A0%BC%E5%BC%8F%E4%BC%A0%E8%BE%93%E8%87%B3%E5%86%85%E7%BD%91ip3%E7%9A%8480%E7%AB%AF%E5%8F%A3.png)
  ![](https://gitee.com/Mateogic/IntranetPenetration/raw/master/Images/(1.1)%E5%86%85%E7%BD%91%E8%AE%BF%E9%97%AE%E6%95%88%E6%9E%9C.png)
2. #### 配置FRPS服务器(腾讯云)

  ![](https://gitee.com/Mateogic/IntranetPenetration/raw/master/Images/(2)frps%E4%BA%91%E6%9C%8D%E5%8A%A1%E5%99%A8%E9%85%8D%E7%BD%AE.png)
3. #### 配置FRPC客户端(中转设备)

  ![](https://gitee.com/Mateogic/IntranetPenetration/raw/master/Images/(3)frpc%E6%9C%AC%E5%9C%B0%E5%AE%A2%E6%88%B7%E7%AB%AF%E9%85%8D%E7%BD%AE.png)
4. #### 通过FRP内网穿透建立内网上述某IP的80端口与公网IP设定的7081端口映射，完成上述操作即可通过外网访问查看拍摄画面。

  ![](https://gitee.com/Mateogic/IntranetPenetration/raw/master/Images/(4)frp%E4%B8%AD%E8%BD%AC%E8%AE%BE%E5%A4%87%E6%98%A0%E5%B0%84.png)
  ![](https://gitee.com/Mateogic/IntranetPenetration/raw/master/Images/(4.1)%E5%85%AC%E7%BD%91%E8%AE%BF%E9%97%AE%E6%95%88%E6%9E%9C.png)
# rasp-eye tcp传输部分
DJI 入职作业

## 说明（基于树莓派的远程智能相机）
树莓派采集视频，由后台GPU服务器进行目标检测。用户打开浏览器访问远程视频及检测结果。

本分支处理传输相关程序

### 树莓派:
1) 数据传输协议采用TCP协议，保证数据传输的可靠性。
2) 树莓派作为Server，根据Client请求提供H.264视频流？

### 谷歌云（Ubuntu 16.04）：
1）搭建ngrok服务器，提供内网穿透功能

### Ubuntu PC:
1) Ubuntu PC作为Client，向树莓派发出视频请求？
2) 基于YOLO网络检测视频中的目标。
3) 输出MJPEG视频流，并推送至HTTP服务器。
<div align="center">
  <img src="https://github.com/w111liang222/rasp-eye/blob/master/images/flowchart.jpg"><br><br>
</div>



## 依赖项
### 树莓派:

### 谷歌云：
goalang

## 编译
```shell
mkdir build
cd build
cmake ..
make
```

## 使用
Ubuntu PC的可执行程序为rasp_eye_pc
```shell
./rasp_eye_pc -h

Usage: ./rasp_eye_pc image/video \[Options\]
Options:
  -d            specify the detector to use
                coco
                tiny-coco
                voc
                tiny-voc
  -i            specify the input file
  -w            set image width
  -h            set image height
  -fps          set fps of video
  -g            use gpu index
  -nogpu        don't use gpu
  -thresh       threshold of detector
  -hier
  -h            for help

```
视频访问:http://127.0.0.1:8080/?action=stream

## Reference
[ngrok](https://github.com/inconshreveable/ngrok.git)

## Contact
david.yao.sh.dy@gmail.com

## License
[GPL-3.0](LICENSE)







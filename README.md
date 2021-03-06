[![Build Status](https://travis-ci.org/kentokura/raspimouse_ros.svg?branch=master)](https://travis-ci.org/kentokura/raspimouse_ros)
# pimouse_ros

fxck.pyは、ROSを用いて、使用しているラズパイのsdカードに指定した文字を上書きします。 
大量の文字を上書きすることで、SDカードのもうみたくないデータとおさらば出来ます。

## 環境設定
- Raspberry Pi 3 Model B
- Ubuntu 16.04
- ROS (Kinetic Kame)

以下のバッシュスクリプトを用いるとよい。  
[ros_setup_scripts_Ubuntu16.04_server](https://github.com/ryuichiueda/ros_setup_scripts_Ubuntu16.04_server)

## 使い方
端末を立ち上げ以下を実行
```
roscore
```
もう一つ端末を立ち上げ、以下を実行
```
roscd pimouse_ros/scripts/
chtmod +x fxck.py
rosrun pimouse_ros fxck.py
ln -s fxck.py buzzer.py
roslaunch pimouse_ros test.launch
```
その後、上書きしたい文字列をトピックで送る。（/dev/zeroを用いると0で埋め尽くせる)
```
rostopic pub -1 '/buzzer' std_msgs/UInt16 "送りたい文字列"
```

 
-----
 ### 参考文献
 
 上田隆一(2017)『Raspberry Piで学ぶ ROSロボット入門』日経BP社.  
 [ロボットシステム学第10回（ROS）](https://www.youtube.com/watch?v=PL85Pw_zQH0)

# ROS2-Ubuntu24.04  
Ubuntu24.04にROS2をぶち込んでやる  
今までのROS2-foxyは入らんからROS2-jazzyっていう後継のを使うぞ  
ROS2-jazzyはUbuntu24.04に対応してるやつでRaspberry Pi5の公式推奨Ubuntuが24.04以降なので  
これを使ってやらんといかん  

Raspberry Pi5でしか動作確認してないんでとりあえずはかんばってくれ  
以下のサイトからとりあえずRaspberri Pi Imagerを引っ張ってきてUbuntu24.04 のOSを入れてくれ  
この[サイト](https://www.raspberrypi.com/software/)から取ってきた  
筆者はUbuntu Desktop 24.04.1 LTS(64-bit)  
を入れて作業した  

んで、立ち上げたらいろいろ初期設定してから  
terminalを開いて以下のプログラムを入れる  
まず初めにパッケージインストールとリポジトリを入れてくれ  
```
sudo apt update
sudo add-apt-repository universe
```
続いて、ROS2のリポジトリの暗号鍵の取得とリポジトリをいれてくれ
```
sudo apt update && sudo apt install curl -y
sudo curl -sSL https://raw.githubusercontent.com/ros/rosdistro/master/ros.key -o /usr/share/keyrings/ros-archive-keyring.gpg 
echo "deb [arch=$(dpkg --print-architecture) signed-by=/usr/share/keyrings/ros-archive-keyring.gpg] http://packages.ros.org/ros2/ubuntu $(. /etc/os-release && echo $UBUNTU_CODENAME) main" | sudo tee /etc/apt/sources.list.d/ros2.list > /dev/null
```
次にROS2のインストールをしてくれ
```
sudo apt update
sudo apt install ros-gazzy-desktop
```
めっちゃ時間かかるから暇だと思うけど時間つぶして待ってろ

ここまで入れられたらとりあえずROS2入ってるから以下の入れてみてとりあえずROS2入ってるか見てほしい
1つターミナル開いて
1つ目で以下の
```
ros2 run demo_nodes_cpp talker
```
2つ目で以下の
```
ros2 run demo_nodes_py listener
```
入れて各ターミナルに
Hello Worldの結果が二つとも同じ数値を同時に受け渡せていれば大丈夫

ダメそうならちょっと教えてくれると大変うれしいどす

このあととりあえずタートルシムっていう亀動かして遊ぶやつやるなら
```
ros2 run turtlesim turtlesim_node
```
これでとりあえずカメの画像が出てくる
そのあともう一つターミナル開いて
```
ros2 run turtlesim turtle_teleop_key

```
これ入れて矢印キー操作すると亀が自由に動かせるからやってみて

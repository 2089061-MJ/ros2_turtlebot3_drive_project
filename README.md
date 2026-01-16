# ROS2 주행 프로젝트
Python 기반의 Theta* + Regulated Pure Pursuit를 활용한 주행 프로젝트입니다.

## 요구 사항
1. ROSBridge가 제공하는 웹 소켓 서버를 활성화 합니다.
2. 터틀봇3의 bringup 노드, 카메라 노드(파이카메라)를 활성화 합니다.
3. Remote pc에서 ros 패키지 런치 파일을 실행합니다.(rpp_test.launch.py)
4. 웹서버를 활성화 해야합니다.

## 적용하기
리눅스 우분투 22.04 환경 기준으로 작성하였습니다.

### ros2 humble을 활성화합니다.
    $ source /opt/ros/humble/setup.bash
  
### 터틀봇3 라즈베리파이에 9090번 포트로 ROSBridge 서버를 실행합니다.
    $ ros2 run rosbridge_server rosbridge_websocket --port 9090

### 터틀봇3의 bringup 노드를 활성화합니다.
    $ export TURTLEBOT3_MODEL=waffle_pi
    $ ros2 launch turtlebot3_bringup robot.launch.py

### 터틀봇3의 카메라 노드를 활성화합니다.
    $ ros2 run v4l2_camera v4l2_camera_node

### ros 패키지로 이동해서 빌드를 합니다.
    $ cd ros2_turtlebot3_drive_project
    $ colcon build

### 빌드 후 source 적용을 합니다.
    $ source install/setup.bash

### 런치 파일을 실행합니다.
    $ ros2 launch my_robot_pkg rpp_test.launch.py
    

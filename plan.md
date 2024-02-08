# Wheel Leg Balance Control Research and Design Plan

## 1 Fundamental Balance Control

Fixed leg length, straight line movement on the ground, verification of basic principles of balance control

- [x] Kinetic Analysis
- [x] Control Algorithm
- [x] Simplified Model Simulation Verification
- [x] Kinematic Analysis of Leg Linkage
- [x] Balancing + Simulation Verification of Leg Control
- [ ] ~~Nonlinear Control*~~

## 2 Overall Motion Control

Implement basic movement functions, and optimize movement behavior

~~Route 1~~

- [ ] Leg Coordination
- [ ] Leg Length Control
- [ ] Steering Control
- [ ] Roll Angle

Route 2（Complete Model）

- [x] Whole Body Dynamics Modeling
- [x] Control Algorithm
- [x] Simulation Verification

## 3 Actual Robot Control

- [x] Wireless Debugger +  Serial Port Testing
- [x] Gyroscope Calibration
- [x] Circuit Connection Design
- [x] Joint Motor Drive
- [x] Implementation of Motor Force Control + Verification
- [x] Verification of Leg Kinematics
- [x] Implementation of Control Algorithms
- [x] Test


## 4 Advance Capabilities

Enhance robustness and achieve advanced functions such as jumping and disturbance adaptation.

- [x] Stationary in place (try increasing the speed loop coefficient + reducing the speed loop input limit + decreasing the angle coefficient, if the effect is not good, try force position hybrid control)
- [x] Test the effect of different leg lengths on getting up, and shortening the leg length in a large-angle state
- [x] Disturbance observer
- [x] Slipping detection (observer + force level hybrid control)
- [x] Lift-off detection + landing (ground support force can be estimated through leg length PID output, and roll PID coefficient is expressed as a function of leg length PID)
- [x] Gyroscopic translation (eccentric rotation, periodic velocity planning)
- [x] Active jumping (jumping in motion/in-place)
- [ ] Automatic jumping motion planning
- [x] Power limitation
- [x] Test

## 5 Whole Vehicle

Prepare the competition vehicle to the starting state

Hardware

- [x] Wiring Management
- [x] Slip Ring Welding Wire
- [x] Gimbal
- [x] Wheel Motor ID + Wire Change
- [x] Mini PC
- [x] Camera
- [x] Referee System
- [x] Capacitance
- [x] Relay
- [x] Protect
- [x] Maintenance + Spare Parts


Software

- [x] Board Program
- [x] Pan Tilt Program
- [x] Remote Control Operation
- [x] Mouse and Keyboard Operation
- [x] Aim Bot
- [x] Power Limit
- [ ] UI


---


# 轮腿平衡控制研发计划

## 1 基础平衡控制

固定腿长，平地直线运动，平衡控制基本原理验证

- [x] 动力学分析
- [x] 控制算法
- [x] 简化模型仿真验证
- [x] 腿部连杆运动学分析
- [x] 平衡+腿部控制仿真验证
- [ ] ~~非线性控制*~~

## 2 整体运动控制

实现基本的运动功能，优化运动性能

~~路线1~~

- [ ] 双腿协调
- [ ] 腿长控制
- [ ] 转向控制
- [ ] 横滚角

路线2（完整模型）

- [x] 全身动力学建模
- [x] 控制算法
- [x] 仿真验证

## 3 实际机器人控制

- [x] 无线调试器+串口测试
- [x] 陀螺仪校准
- [x] 线路连接设计
- [x] 关节电机驱动
- [x] 电机力控实现+验证
- [x] 腿部运动学验证
- [x] 控制算法实现
- [x] 测试

## 4 进阶功能

提升鲁棒性，实现一些进阶功能如跳跃、扰动自适应等。

- [x] 原地静止（尝试增大速度环系数+速度环输入限幅缩小+减小角度系数，效果不好则尝试力位混控）
- [x] 测试不同腿长起身效果，大角度状态缩短腿长
- [x] 扰动观测器
- [x] 打滑检测（观测器+力位混控）
- [x] 离地检测+落地（通过腿长PID输出可估计地面支持力，roll PID系数表示为腿长PID的函数）
- [x] 陀螺平移（偏心旋转，周期速度规划）
- [x] 主动跳跃（运动中跳跃/原地）
- [ ] 自动跳跃运动规划
- [x] 功率限制
- [x] 测试

## 5 整车

比赛用车整备至上场状态

硬件

- [x] 走线整理
- [x] 滑环焊线
- [x] 云台
- [x] 轮电机id+换线
- [x] minipc
- [x] 相机
- [x] 裁判系统
- [x] 电容
- [x] 继电器
- [x] 保护
- [x] 保养+备件

软件

- [x] 上板程序
- [x] 云台程序
- [x] 遥控器操作
- [x] 键鼠操作
- [x] 自瞄
- [x] 功率限制
- [ ] ui

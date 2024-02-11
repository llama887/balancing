# Shanghai Jiao Tong University Open Source Balancing System Documentation

## General

This is an open-source document for the balancing control system of Shanghai Jiao Tong University’s Jiao Long team, providing an index of open-source content and research development approach. The contents of this open-source project primarily focus on the design documentation of the control system as well as reference test video.

This open-source project is from Shanghai Jiao Tong University’s Jiao Long team for technical use only and cannot be used for any commercial purposes without the creator’s permission.

Reproduction must indicate the source of the work, and the creator reserves the right to pursue illegal reproduction through legal means.

## Index

### Document
1. Dynamical Model - [WBR_control](WBR_control.html)
2. Leg Mechanism Analysis - [WBR_leg](WBR_leg.html)
3. Controller Design - [WBR_control](WBR_control.html)

### Research Development Plan
1. Research Development Plan Documentation - [plan](plan.md)

### Handwritten Manuscript
The following content has yet to be organized into an electronic format, thus the open source is in handwritten form. Such content includes power limitation, adaptive adjustment, anti-slip strategy, gyroscope translation, etc. In addition, during the organization process, there may have been some information regarding the modeling analysis and control that was overlooked. These handwriting manuscripts can also be used as a reference.

All manuscripts have been translated and placed in this [document](https://docs.google.com/document/d/1GZG_sZS-NjTip8aB8_fAdbVojVIyzdiJpsQk-gfD-3A/edit?usp=sharing).
1. Modeling Analysis - [modelling](note/modelling/modeling_1.jpg)
2. Leg Mechanism Analysis - [leg](note/leg/leg_1.jpg)
3. Power Limitation - [power](note/power/power_1.jpg)
4. Adaptive Adjustment - [predictor](note/predictor_and_controller.jpg)
5. Gyroscope Translation & Leg Weight Coefficient - [other](note/other.jpg)

### Control System Flowchart
Provided flowcharts for core components of the control system (balancing motion control, movement, locomotion control- height, horizontal roll). The system is made up of 4 parts: (1) target state input, (2) controller, (3) robot model, (4) observer.
1. System Flowchart - [system](assets/control_system/system.jpg)
2. Controller - [controller](assets/control_system/controller.jpg)
3. Locomotion Controller - [locomotion_controller](assets/control_system/locomotion_controller.jpg)
4. Leg Controller - [leg_controller](assets/control_system/leg_controller.jpg)
5. Observer - [observer](assets/control_system/observer.jpg)

### Simulation
The assets/sim_WBR_control folder contains simulink simulation video and simulation state curve.

### Test Video
The assets/test_video folder contains test videos for various functions that can serve as references for movement and robustness performance.

## Hardware Plan
Drive wheel: 3508 Motor + Self-Controlled Planetary Reducer (14:1 Reduction Ratio)
Joint Motor: HT04
Main Controller: STM32F407 (Type-C Development Board)
IMU: BMI088 (Integrated with C board)

## Research and Development Approach
Our balanced infantry adopts a wheeled leg design, which has certain advantages in undulating road sections, slopes, and lateral movement, and the corresponding control system is also relatively complex. Considering the complexity of the model and the resource consumption when running on a microcontroller, LQR is adopted to achieve balancing movement control.

In the 2022 season, the balancing robot of the Chuang Meng Zhi Yi team of Harbin Engineering University showed excellent performance in the competition, and after the end of the season, they also published an open-source document for the balancing control system [1]. We referenced such documentation in the process of designing our own control system.

Previously, most models of wheeled-legged robots were simplified as two-stage inverted pendulums [1] [2] [3], and the handling of the two legs was not perfect. At the same time, the control of the wheel motor was divided into two parts: balanced movement and rotation, which were not completely decoupled. Therefore, we believe that the turning performance of the wheeled-legged robot in high-speed movement has not been fully utilized. Thus, after preliminarily verifying the balance control algorithm based on the inverted pendulum model, we have re-established a full-body dynamics model of the robot containing both legs and designed a decoupled control system based on this model.

After completing the core balance, motion control, and leg control, to further improve the performance and robustness of balanced infantry on the field, we conducted a series of optimizations and functional development.

An adaptive regulator was designed for the scene of bullets on the field, and the basic idea for designing this regulator is still to control the output decoupling. Compared to relying on additional sensors to determine whether the projectile or wheel is hovering, this regulator does not disrupt the integrity of the original model and control system. Instead, it intervenes only when the system deviates from the model through a trajectory-tracking approach, ensuring the robustness of the system.

Compared to traditional four-wheeled infantry, the power limitation of balanced vehicles is relatively difficult to achieve, and some methods use supercapacitors and open loops. However, on the one hand, it is easy to exceed the power when the capacitor runs out of power (many teams on the field experience continuous exceeding the power after the balancing is stuck on the wall), and on the other hand, it is also difficult to fully utilize the sporty performance of balanced vehicles. There are currently two ways to limit the power of a balanced vehicle: one is to use NMPC control, which utilizes the constrained optimization characteristics of NMPC to limit the power (refer to the Youth Union defense of Guangdong University of Technology DynamicX team in the 23rd season [4]). This method has a relatively intuitive idea, but requires high computational power for the calculation platform; Another way is to analyze the control law and obtain power-limiting conditions with very low computational consumption, which can run at 1 kHz on a microcontroller.

Due to the inability of balanced infantry to achieve omnidirectional movement, there are many limitations in operation on the field. But in the gyro state, the variable speed balance vehicle can achieve approximate omnidirectional translation, which can effectively improve the maneuverability and survival ability of balance on the track.

Finally, the stability of the car is particularly important in competitions. A balanced car can maintain stability in the event of collisions, stepping down, jumping, and other situations, and restore balance in an extremely short period, to support the operator in completing various operations with confidence.

## Reference Material
[1] [RoboMaster平衡步兵机器人控制系统设计](https://zhuanlan.zhihu.com/p/563048952)（哈尔滨工程大学创梦之翼战队，2022）  
[2] S. Wang et al., "Balance Control of a Novel Wheel-legged Robot: Design and Experiments," 2021 IEEE International Conference on Robotics and Automation (ICRA), 2021, pp. 6782-6788, doi: 10.1109/ICRA48506.2021.9561579.  
[3] V. Klemm et al., "Ascento: A Two-Wheeled Jumping Robot," 2019 International Conference on Robotics and Automation (ICRA), 2019, pp. 7515-7521, doi: 10.1109/ICRA.2019.8793792.  
[4] [RMUC 2023青工会技术答辩-广东工业大学-无下位机电控、平衡步兵模型预测控制](https://www.bilibili.com/video/BV18F41117QZ)


---


# 上海交通大学交龙战队平衡步兵控制系统开源说明文档

## 概述

本文档为上海交通大学交龙战队平衡步兵控制系统开源说明文档，给出了开源内容的索引和研发思路。本次开源的内容主要为控制系统的设计文档以及一些用于参考的测试视频。

本开源项目出自上海交通大学交龙战队，仅用于技术交流，未经作者允许，不得作任何商业用途。

转载需注明作品出处，对非法转载者，作者保留采用法律手段追究的权利。

## 索引

### 文档

1. 动力学模型-[WBR_control](WBR_control.html)
2. 腿部机构分析-[WBR_leg](WBR_leg.html)
3. 控制器设计-[WBR_control](WBR_control.html)

### 研发计划

1. 研发计划文档-[plan](plan.md)

### 手写稿

部分内容未整理成电子版，以手写稿形式开源，包括功率限制、自适应调节（防打滑策略）、陀螺平移等。此外建模分析和控制部分的电子稿在整理过程中可能有一些遗漏，手写稿也可作为一定参考。

1. 建模分析-[modelling](note/modelling/modeling_1.jpg)
2. 腿部机构分析-[leg](note/leg/leg_1.jpg)
3. 功率限制-[power](note/power/power_1.jpg)
4. 自适应调节-[predictor](note/predictor_and_controller.jpg)
5. 陀螺平移&腿部自重系数-[other](note/other.jpg)

### 控制系统框图

给出控制系统核心部分（运动控制-平衡、移动、旋转，腿部控制-高度、横滚）控制框图。系统由4部分组成：(1)目标状态输入，(2)控制器，(3)机器人模型，(4)观测器。

1. 系统框图-[system](assets/control_system/system.jpg)
2. 控制器-[controller](assets/control_system/controller.jpg)
3. 运动控制器-[locomotion_controller](assets/control_system/locomotion_controller.jpg)
4. 腿部控制器-[leg_controller](assets/control_system/leg_controller.jpg)
5. 观测器-[observer](assets/control_system/observer.jpg)

### 仿真

assets/sim_WBR_control 文件夹包含simulink仿真视频和仿真的状态曲线

### 测试视频

assets/test_video 文件夹中包含各项功能的测试视频，可作为运动性能和鲁棒性的参考。

## 硬件方案

- 驱动轮：3508电机+自制行星减速箱（14:1减速比）
- 关节电机：HT04
- 主控：STM32F407（C型开发板）
- IMU：BMI088（C板集成）

## 研发思路

我们的平衡步兵采用轮腿设计，轮腿结构在起伏路段、斜坡、横向移动等方面均有一定优势，相应的控制系统也相对复杂。考虑到模型的复杂性以及在单片机上运行的资源消耗等因素，采用LQR实现平衡运动控制。

2022赛季哈尔滨工程大学创梦之翼战队的平衡步兵在比赛中表现出了非常优秀的性能，赛季结束后他们也开源了平衡步兵的控制系统[1]。我们的控制系统在设计时一些处理参考了其思路。

此前轮腿机器人的模型多数简化为两级倒立摆[1][2][3]，对于两条腿的处理并不完善，同时轮电机的控制分为平衡移动和旋转两部分，不完全解耦。由此我们认为轮腿机器人在高速移动中的转向性能仍没有被完全发挥，因此在根据倒立摆模型初步验证了平衡控制算法后，重新建立了包含双腿的机器人全身动力学模型，并基于该模型设计了解耦的控制系统。

在完成核心的平衡、运动控制和腿部控制后，为了进一步提升平衡步兵在赛场上的性能和鲁棒性，我们又做了一系列优化和功能开发。

针对赛场上满地弹丸的场景设计了自适应调节器，设计该调节器的基本思路依然是希望控制输出解耦。相比根据额外的传感器判断是否踩到弹丸或轮子悬空，这种调节器不会破坏原有模型和控制系统的完整性，而是通过类似于轨迹跟踪的方式，仅在系统偏离模型的状态下介入，保证了系统的鲁棒性。

相比传统的四轮步兵，平衡车的功率限制相对难实现，也有采用超级电容+开环的做法，但一方面这样在电容没电时很容易超功率（赛场上不少队伍出现平衡卡墙后连续超功率的情况），另一方面也难以充分发挥平衡车的运动性能。平衡车功率限制的方式目前有两种：一种是采用NMPC控制，利用NMPC带约束优化的特性对功率进行限制（可参考广东工业大学DynamicX战队23赛季青工会答辩[4]），这种方式思路相对直观，但对计算平台算力要求很高；另一种方式是通过分析控制律，得到计算消耗非常低的功率限制条件，可在单片机上以1Khz运行。

由于平衡步兵无法实现全向移动，在赛场上操作存在许多制约。但在陀螺状态下，通过变速平衡车可以近似实现全向平移，这一功能在赛场上能有效提升平衡的机动性和生存能力。

最后，车的稳定性在比赛中尤为重要，平衡车具备在发生冲撞、下台阶、跳跃等情况时保持不翻，并在极短时间恢复平衡的能力才能支持操作手放心地完成各种操作。

## 参考资料

[1] [RoboMaster平衡步兵机器人控制系统设计](https://zhuanlan.zhihu.com/p/563048952)（哈尔滨工程大学创梦之翼战队，2022）  
[2] S. Wang et al., "Balance Control of a Novel Wheel-legged Robot: Design and Experiments," 2021 IEEE International Conference on Robotics and Automation (ICRA), 2021, pp. 6782-6788, doi: 10.1109/ICRA48506.2021.9561579.  
[3] V. Klemm et al., "Ascento: A Two-Wheeled Jumping Robot," 2019 International Conference on Robotics and Automation (ICRA), 2019, pp. 7515-7521, doi: 10.1109/ICRA.2019.8793792.  
[4] [RMUC 2023青工会技术答辩-广东工业大学-无下位机电控、平衡步兵模型预测控制](https://www.bilibili.com/video/BV18F41117QZ)

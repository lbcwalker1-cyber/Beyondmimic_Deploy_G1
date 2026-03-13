# Beyondmimic_sim2sim
Sim2sim based on Unitree_rl_gym.

# 模型说明 / Model Description

本项目是基于 **BeyondMimic** 动作模仿算法，针对 **Unitree G1** 人形机器人实现的 sim2sim 及 sim2real 部署框架。

| 项目 | 说明 |
|------|------|
| 机器人型号 | Unitree G1 人形机器人 |
| 强化学习算法 | BeyondMimic（whole_body_tracking） |
| 训练配置 | Tracking-Flat-G1-Wo-State-Estimation-v0（不带状态估计） |
| 观测空间维度 | 154 维 |
| 动作空间维度 | 29 个关节 |
| 策略模型格式 | ONNX（policy_zuiwu_48000.onnx，"zuiwu"= 醉舞 drunken-dance style，48000 = training iteration） |
| 参考动作数据集 | LAFAN，dance2_subject4 动作片段 |

> This project is a sim2sim / sim2real deployment framework for the **Unitree G1** humanoid robot, based on the **BeyondMimic** motion-imitation reinforcement-learning algorithm.
> The provided policy (`policy_zuiwu_48000.onnx`, where *zuiwu* (醉舞) means "drunken dance" and *48000* is the training iteration) was trained with the `Tracking-Flat-G1-Wo-State-Estimation-v0` configuration (no state estimation), using a dance motion clip from the LAFAN dataset.
> Observation space: **154-dim**. Action space: **29 joints**. Policy format: **ONNX**.

# 基于Unitree_rl_gym搭的beyondmimic复现


需要修改输入的motion和policy。
请大家一起讨论哈，争取完善。
提供的模型是基于lafan训练的dance2_subject4。

2025.9.5更新
# 基于Unitree_rl_gym搭的sim2real部分

修改了unitree_rl_gym中的deploy_real部分。增加了bydmimic文件夹存储motion和onnx模型。重新写了配置文件g1_for_bydmimic.yaml。
部署需要修改的路径：
1. config路径，位于主函数中，搜索config_path进行对应修改，改到config_path = f"你的文件夹/{args.config}"
2. motion路径，位于deploy_real4bydmimic.py中，可以进行搜索npz找到对应行。修改成你的文件夹即可self.motion = np.load("外部文件夹/deploy_real/bydmimic/dance_zui.npz")
3. model路径，位于config中，policy_path: "外部文件夹/deploy/deploy_real/bydmimic/policy_zuiwu_48000.onnx"修改即可。
   
# 注意！！！
1. 本次运行提供的模型动作难度很高，存在机器人脖子着地托马斯回旋的情况，建议只用来测试是否可行。
   更新：！笔者动了二三十秒就摔了，可以测试，但不要运行时间过长！！
   可以替换为自己的模型测试，摔倒的原因应该是训练中的碰撞mesh差别，机器人腿打到自己。
2. 手柄操作和原本的行走是一样的，先进调试模式，运行命令行后按start进入默认位置，再按A进入舞蹈模式。
3. 进入默认位置后，建议先检查终端中打印的四元数是否接近1 0 0 0。如果不是请不要进行运动。
4. 由于作者调试很不方便，只测试了运动的一小部分，确定没有问题。在使用中如果出现机器人损坏等问题，请使用者自己负责。
5. 本项目拒绝盈利行为，引用本项目请标明。

配置环境部分请参考Unitree_rl_gym
部署命令行：python  deploy_real4bydmimic.py enp4s0  g1_for_bydmimic.yaml

# 注意
本代码基于的是beyondmimic作者开源算法中不带状态估计的训练配置，即Tracking-Flat-G1-Wo-State-Estimation-v0。
这种训练方式的状态空间维度为154维。
如果希望使用原本的配置来进行测试，请在anchorori的obs前增加三维度的相对位置，以及在angvel前增加三维度的根坐标系速度。

# Acknowledgement：
[1] Beyondmimic训练源码：https://github.com/HybridRobotics/whole_body_tracking

[2] Unitree_rl_gym仓库： https://github.com/unitreerobotics/unitree_rl_gym


特别感谢[Owen-SuQ](https://github.com/Owen-SuQ) [642X](https://github.com/642X) 对本项目的支持

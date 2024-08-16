# 简历
张书源 - [邮箱](rayzhang707@gmail.com) - [网站](sanbingyouyong.github.io)

## 教育背景
- 伦敦帝国理工学院 (2024 ~ 2025)
    - Advanced Computing硕士(攻读中)
- 爱丁堡大学 (2020 ~ 2024)
    - 计算机科学学士（With Honours）
    - 加权平均成绩: 78 (一等学位)

## 亮点

### 计算机视觉 / 计算机图形学
- 爱丁堡大学课程：*计算机图形学：渲染* & *计算机图形学：几何与模拟*
    - 从零开始学习C++并实现**光线追踪**，包括高级功能如纹理、基于BVH的加速层次结构、路径追踪、像素采样、镜头/光圈采样和光源采样
    - 从点云进行**3D模型重建**，离散分析与参数化
- 爱丁堡大学本科毕业论文：*逆向程序化建模：从手绘到建筑*
    - 基于有向无环图（DAG）构建建筑的程序化模型
    - 扰动3D模型并渲染为2D手绘风格图片；通过参数采样生成训练数据
    - Encoder-decoder和Multi-task decoder，基于输入手绘图片预测DAG参数以构建合适的3D建筑模型
    - 开发Blender插件作为用户界面

### 自然语言处理
- 爱丁堡大学课程：*自然语言处理基础* & *自然语言理解、生成与机器翻译*
    - N-gram模型，贝叶斯概率，RNN，GRU，LSTM，Transformer和Attention机制
    - 课程*机器学习实践*的小组项目：通过GPT Prompting进行的Query-focused Summarization
- 课外应用：
    - 基于中文诗歌的N-gram模型概率，为游戏Stellaris开发了古风命名组mod，拥有500+订阅。

### 大型语言模型
- 应用：
    - Prompt Engineering，Multi-agent系统，OpenAI API，Ollama API
    - 通过设计和实现Multi-agent系统来细分任务以提高性能和大语言模型的稳健性
    - 为低资源任务生成微调数据
    - 部署在远程服务器上的[QAnything](https://github.com/netease-youdao/QAnything)作为LLM后端，附带知识库

### 数字人
- 部署在远程服务器上，扩展并贡献到开源数字人音视频生成框架[Linly_Talker](https://github.com/Kedreamix/Linly-Talker)，自定义集成了QAnything，作为数字人的文本生成方法
- 部署在远程服务器上的[GPT-SoVITS](https://github.com/RVC-Boss/GPT-SoVITS)用于语音克隆模型的微调
- 部署在远程服务器上的[metahuman-stream](https://github.com/lipku/metahuman-stream)作为实时数字人流媒体方法

### 物联网
- 爱丁堡大学课程：*物联网系统的原理与设计*
    - 通过可穿戴设备收集人类活动数据
    - 设计、实现和训练神经网络（CNN，RNN，LSTM与Model Ensemble）以识别活动和呼吸状态
    - 开发安卓应用程序以部署训练好的模型，通过蓝牙连接可穿戴传感器，并实时分类人类活动/呼吸症状

### 系统工程
- 小组项目：一个基于TurtleBot、Lego电机、3D打印部件和安卓应用程序通过蓝牙连接机器人的多米诺骨牌放置机器人项目，为课程*系统设计项目*而开发
    - 设计多米诺骨牌的重新加载和自动放置机制
    - 设计和建模3D打印部件
    - 编写控制Lego电机的Python脚本
    - 协调安卓应用程序开发
    - 设计并实现服务器、机器人和应用程序之间的通信方法

## 工作经历
- 华工科技 - 新技术产品研发组实习生 (2024年夏)
    - 从事数字人相关工作，直接或使用Docker容器在计算服务器上部署各种服务，本地托管一个由Streamlit驱动的网页以跟踪服务状态
- 玩瞳科技 - 算法实习生 (2024年6月)
    - 通过分解复杂任务并设计/实现Multi-agent系统，提高LLM在聊天回复生成和决策中的性能和稳健性
- 爱丁堡大学IPAB GraphviX实验室 - 暑期研究实习 (2023年夏)
    - 研究基于手绘的逆向程式化建模课题。基于Blender几何节点及其API实现形状文法。训练神经网络从手绘图片中推断形状参数，并将上述流程集成为Blender插件。这些技术栈的一部分也是我本科毕业论文的一部分。
- 爱丁堡大学 - Tutor (2023)
    - 一个有偿职位，每周为课程*推理与代理*提供两小时的tutorial授课
- EUFS - 软件基础设施 (2022 ~ 2023/24)
    - 无人驾驶车辆的软件基础设施团队
        - 维护、重构并扩展Python中的命令行工具`eufs_cli`
            - 将每个命令中70行重复代码重构为5行
        - 提供围绕git、colcon等的辅助功能
        - 为EUFS-Testing-Application的服务器后端贡献代码
        - 更新无人驾驶赛车在不同任务下的启动配置
- 武汉天喻信息 - 算法实习生 (2021年夏)
    - 使用OpenCV-Python和YOLOv5进行目标检测任务，训练模型专注于人流和交通分析任务。编写脚本处理大量ArUco码。收集、清理和增强数据集以进行训练

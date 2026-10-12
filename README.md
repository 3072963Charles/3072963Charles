<div align="center">
  <img src="assets/banner_home.svg" width="100%" alt="Charles (Zonkit) - 功率半导体器件建模 x AIoT 智能硬件"/>
</div>

<br/>

<h2 align="center">你好，我是 Charles（Zonkit）👋</h2>

<p align="center">
  <em>电子科技大学 × 格拉斯哥大学 联合培养（格拉斯哥海南学院）· 通信 / 电子工程</em>
</p>

<p align="center">
  专注 <b>功率半导体器件建模（SiC MOSFET SPICE）</b> 与 <b>AIoT 智能辅助硬件</b> 的科研与工程实践——<br/>
  一个能从器件物理做到智能硬件的全栈实践者：既能做 TCAD 仿真与机器学习建模，也能写 STM32 固件与 AI 服务。
</p>

<p align="center">
  <img src="https://img.shields.io/badge/GitHub-3072963Charles-181717?style=for-the-badge&logo=github&logoColor=white"/>
  <img src="https://img.shields.io/badge/GPA-3.97%2F4.0-7c3aed?style=for-the-badge"/>
  <img src="https://img.shields.io/badge/研究方向-功率半导体%20%7C%20AIoT-0ea5e9?style=for-the-badge"/>
  <img src="https://img.shields.io/badge/荣誉-中国高校计算机大赛%20省二等奖-16a34a?style=for-the-badge"/>
</p>

---

## 🧭 关于我

| |  |
|---|--|
| 🎓 **教育背景** | 电子科技大学 × 格拉斯哥大学 联合培养（格拉斯哥海南学院）· 通信 / 电子工程（两校三区） |
| 📚 **学术表现** | 本科 GPA **3.97 / 4.0** |
| 🔬 **研究兴趣** | 功率半导体器件建模与仿真 · 物理信息神经网络（PINN）· AIoT 智能硬件 · 计算机视觉 · 嵌入式系统 |
| 🏆 **代表性荣誉** | 中国高校计算机大赛 **海南省二等奖** |
| 👥 **学生工作** | 新生导生 · 讲师团团长 · 多个社团负责人 |

---

## 🚀 重点项目

### ① 明眸 BrightEyes 智能导盲眼镜 —— 软硬件一体化视障辅助系统

> 面向视障人士的端到端智能导航与辅助系统，覆盖 **盲道导航、过马路辅助、物品查找、实时语音交互** 全流程：硬件端负责多传感器感知与语音预警，软件端负责 AI 视觉理解与智能决策。
>
> 本项目为本人独立整理、开发与维护的完整版本（软件端 + 硬件端），以本账号下的仓库为准，与任何外部同名或相似项目相互独立。

| 维度 | 内容 |
|------|------|
| 🎯 **项目做了什么** | 盲道导航（YOLO 分割 + Lucas-Kanade 光流稳定）、过马路辅助（斑马线 + 红绿灯识别 + 对齐引导）、物品查找（YOLO-E 开放词汇检测 + ByteTrack 追踪 + MediaPipe 手部引导）、实时语音交互（Paraformer ASR + Qwen-Omni-Turbo）；硬件端以 STM32H743 为核心融合 URM09 超声波 + 4×VL53L0X ToF（前/左/右/下）+ JQ8900 语音模块，实现三级危险分级与实时中文语音预警 |
| 🧑‍💻 **我的工作** | 系统总体架构设计（软硬件分层 + 导航状态机）；软件端 FastAPI 服务与 AI 算法集成；硬件端 STM32 固件**从零开发**（传感器驱动、多传感器融合决策引擎、语音仲裁系统）；软硬件联调与实机验证 |
| 🧭 **工作领域** | AIoT 智能硬件 · 计算机视觉 · 嵌入式系统 · 语音交互 |
| 🎓 **学到了什么** | YOLO 实例分割与开放词汇检测、ByteTrack 多目标追踪、Lucas-Kanade 光流稳定、状态机架构设计；STM32H743 HAL 驱动开发、I2C / UART 通信协议、多传感器融合与防抖滤波、语音模块控制与仲裁策略 |
| 🧰 **使用工具** | Python · FastAPI · PyTorch · YOLO / YOLO-E · MediaPipe · OpenCV · ESP32-CAM · STM32H743（HAL + CMake）· Three.js |
| 🏆 **主要成果** | 中国高校计算机大赛 **海南省二等奖**；完整可运行的软硬件一体化原型；**三级危险分级** + **11 条中文语音预警轨道**；Web 实时监控（含 IMU 3D 姿态可视化） |

<p align="center">
  <a href="https://github.com/3072963Charles/OpenAIglasses_for_Navigation"><img src="https://img.shields.io/badge/软件端仓库-OpenAIglasses_for_Navigation-0ea5e9?style=for-the-badge&logo=github&logoColor=white"/></a>
  <a href="https://github.com/3072963Charles/blindglasses-stm32"><img src="https://img.shields.io/badge/硬件端仓库-blindglasses%20stm32-f97316?style=for-the-badge&logo=github&logoColor=white"/></a>
</p>

---

### ② PINN-SiC-MOSFET —— 大创项目：PINN 驱动的 SiC MOSFET SPICE 参数提取

> 面向 **1.2 kV 4H-SiC 垂直 DMOSFET** 功率器件，利用**物理信息神经网络（PINN）** 从 Silvaco TCAD 仿真数据中**自动提取 SPICE Level-3 紧凑模型物理参数**，输出可直接用于电路仿真的标准 SPICE `.SUBCKT / .MODEL` 文件。

| 维度 | 内容 |
|------|------|
| 🎯 **项目做了什么** | 将 PINN 引入 SPICE 紧凑模型参数逆向提取：用可微分的 SPICE Level-3 物理模型（13 个物理参数）承载器件物理，用神经网络残差修正与 TCAD 数据的偏差，一次训练得到物理可解释、全工作范围（V_GS∈[0,20]V · V_DS∈[0,1200]V · T∈[298,448]K）可用的 SPICE 模型 |
| 🧑‍💻 **我的工作** | 独立完成大创项目全流程：文献调研（2021–2026 SiC 建模 / PINN 参数提取方向）→ 技术方案设计（物理残差架构）→ Silvaco TCAD 仿真数据生成 → PINN 模型实现与训练（PyTorch）→ 物理参数提取与 SPICE 生成 → 多仿真器精度验证与迭代优化 |
| 🧭 **工作领域** | 功率半导体器件建模与仿真 · 物理信息机器学习 · 电路仿真与模型提取 |
| 🎓 **学到了什么** | 4H-SiC 器件物理（阈值电压、迁移率退化、载流子饱和、DIBL、温度特性）；SPICE Level-3 紧凑模型理论；PINN 工程实现（物理残差、单调性约束、亚阈值专项损失、分离学习率）；Silvaco TCAD 仿真流程；模型验证方法论（Gummel 对称性测试、分区域 / 分温度 MAPE 评估） |
| 🧰 **使用工具** | Python · PyTorch · Silvaco TCAD · LTspice · ngspice · HSPICE · MATLAB |
| 🏆 **主要成果** | 整体 MAPE **0.957%**（目标 < 3%，超越 **3.1×**）；R² = **0.99904**；**13 个物理参数**自动提取；Gummel 对称性误差 **0.67%**（通过）；SPICE 模型兼容 LTspice / ngspice / HSPICE；大创项目结题 |

<p align="center">
  <a href="https://github.com/3072963Charles/PINN-SiC-MOSFET"><img src="https://img.shields.io/badge/项目仓库-PINN%20SiC%20MOSFET-6366f1?style=for-the-badge&logo=github&logoColor=white"/></a>
</p>

---

## 🛠️ 技术栈

| 领域 | 技术 |
|------|------|
| 器件建模与仿真 | <img src="https://img.shields.io/badge/Python-3776AB?style=flat-square&logo=python&logoColor=white"/> <img src="https://img.shields.io/badge/PyTorch-EE4C2C?style=flat-square&logo=pytorch&logoColor=white"/> <img src="https://img.shields.io/badge/Silvaco%20TCAD-2f6f9f?style=flat-square"/> <img src="https://img.shields.io/badge/LTspice-1d4ed8?style=flat-square"/> <img src="https://img.shields.io/badge/MATLAB-0076A8?style=flat-square&logo=mathworks&logoColor=white"/> |
| AI 与后端 | <img src="https://img.shields.io/badge/FastAPI-009688?style=flat-square&logo=fastapi&logoColor=white"/> <img src="https://img.shields.io/badge/YOLO-00FFFF?style=flat-square&logo=yolo&logoColor=black"/> <img src="https://img.shields.io/badge/OpenCV-5C3EE8?style=flat-square&logo=opencv&logoColor=white"/> <img src="https://img.shields.io/badge/MediaPipe-0097A7?style=flat-square"/> |
| 嵌入式 | <img src="https://img.shields.io/badge/STM32-03234B?style=flat-square&logo=stmicroelectronics&logoColor=white"/> <img src="https://img.shields.io/badge/ESP32-E7352C?style=flat-square&logo=espressif&logoColor=white"/> <img src="https://img.shields.io/badge/C%2FC%2B%2B-00599C?style=flat-square&logo=c%2B%2B&logoColor=white"/> <img src="https://img.shields.io/badge/CMake-064F8C?style=flat-square&logo=cmake&logoColor=white"/> |
| 工具链 | <img src="https://img.shields.io/badge/Git-F05032?style=flat-square&logo=git&logoColor=white"/> <img src="https://img.shields.io/badge/Linux-FCC624?style=flat-square&logo=linux&logoColor=black"/> <img src="https://img.shields.io/badge/VS%20Code-007ACC?style=flat-square&logo=visualstudiocode&logoColor=white"/> |

---

## 📬 联系

<p align="center">
  <img src="https://img.shields.io/badge/GitHub-3072963Charles-181717?style=for-the-badge&logo=github&logoColor=white"/>
  <img src="https://img.shields.io/badge/Email-3169548541%40qq.com-D14836?style=for-the-badge&logo=gmail&logoColor=white"/>
</p>

<p align="center">
  欢迎交流<b>功率半导体建模、AIoT 硬件与开源项目合作</b> 🚀
</p>

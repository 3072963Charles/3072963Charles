# 你好，我是 Charles（AI-FanGe）

> 电子科技大学 × 格拉斯哥大学 联合培养（格拉斯哥海南学院）· 通信 / 电子工程方向

专注 **功率半导体器件建模（SiC MOSFET SPICE）** 与 **AIoT 智能辅助硬件** 的科研与工程实践。

---

## 个人简介

- 本科 GPA 3.97 / 4.0，主修通信工程与电子信息（两校三区联合培养）
- 研究方向：功率半导体器件建模与仿真、嵌入式系统、AIoT 智能硬件、计算机视觉
- 代表性荣誉：中国高校计算机大赛 海南省二等奖
- 学生工作：新生导生、讲师团团长、多社团负责人

---

## 重点项目

### 1. 明眸 BrightEyes 智能导盲眼镜（软硬件一体化视障辅助系统）

面向视障人士的端到端智能导航与辅助系统，覆盖 **盲道导航、过马路辅助、物品查找、实时语音交互** 全流程，硬件端负责多传感器感知与语音预警，软件端负责视觉理解与智能决策。

#### 软件端 · OpenAIglasses_for_Navigation

![Stars](https://img.shields.io/github/stars/AI-FanGe/OpenAIglasses_for_Navigation)
![Forks](https://img.shields.io/github/forks/AI-FanGe/OpenAIglasses_for_Navigation)

| 功能 | 实现 |
|------|------|
| 盲道导航 | YOLO 分割实时识别盲道 + Lucas-Kanade 光流稳定掩码 + 转弯/避障引导 |
| 过马路辅助 | 斑马线检测 + HSV/YOLO 红绿灯识别 + 对齐引导 |
| 物品查找 | YOLO-E 开放词汇检测 + ByteTrack 追踪 + MediaPipe 手部引导 + 抓取确认 |
| 语音交互 | 阿里云 Paraformer 实时 ASR + Qwen-Omni-Turbo 多模态对话 |
| Web 监控 | FastAPI + WebSocket 实时视频流 + Three.js IMU 3D 姿态可视化 |

**系统架构**

```
ESP32-CAM / 浏览器 / 移动端（客户端层）
        │  WebSocket
FastAPI 主服务（app_main.py）
        │
NavigationMaster 状态机（IDLE / CHAT / BLINDPATH_NAV / CROSSING / ITEM_SEARCH…）
        │
模型推理层（YOLO 分割 · YOLO-E 检测 · MediaPipe 手部 · 光流稳定）
        │
阿里云 DashScope（Paraformer ASR · Qwen-Omni 多模态）
```

- 技术栈：Python / FastAPI / PyTorch / YOLO / YOLO-E / MediaPipe / OpenCV / Three.js / ESP32-CAM
- 硬件端：ESP32-CAM + ICM42688 IMU，Arduino 固件
- 开源协议：MIT

[进入软件端仓库 →](https://github.com/AI-FanGe/OpenAIglasses_for_Navigation)

#### 硬件端 · BlindGlasses STM32 Sensor Hub

![Stars](https://img.shields.io/github/stars/3072963Charles/blindglasses-stm32)

STM32H743 多传感器感知与语音预警固件：**URM09 超声波 + 4×VL53L0X ToF 激光测距（前/左/右/下）+ JQ8900 语音播报**，实时监测前方障碍、两侧狭窄与台阶风险。

| 能力 | 实现 |
|------|------|
| 多传感器融合 | URM09 前向主测距（0–500 cm）+ 4×VL53L0X 四向 ToF（mm） |
| 三级危险分级 | SAFE / WARNING / EMERGENCY，动态风险升级 + 防抖滤波 |
| 语音仲裁 | 三级优先级抢占 / 排队 / 方向冷却，11 条中文预警轨道 |
| 组合判定 | 三面受阻、前左/前右受阻、两侧狭窄、台阶检测与引导提示 |

- MCU：STM32H743（Cortex-M7），STM32CubeMX + CMake / Ninja / arm-none-eabi
- 决策引擎：多阈值分级 + 递减升级 + 防抖 + 语音抢占仲裁（详见 `obstacle.c`）

[进入硬件端仓库 →](https://github.com/3072963Charles/blindglasses-stm32)

---

### 2. PINN-SiC-MOSFET：SiC 功率 MOSFET SPICE 紧凑模型参数提取

![Stars](https://img.shields.io/github/stars/3072963Charles/PINN-SiC-MOSFET)

面向 1.2 kV 4H-SiC 垂直 DMOSFET，使用**物理信息神经网络（PINN）**从 Silvaco TCAD 数据自动提取 SPICE Level-3 紧凑模型物理参数，输出可直接用于电路仿真的 `.SUBCKT / .MODEL` 文件。

**核心创新**

- 物理残差架构：`I_total = I_phys × exp(δ_log)`，13 个可训练物理参数全程可微分
- 亚阈值专项损失（3× 加权），针对性提升弱反型区精度
- 全工作范围覆盖：V_GS ∈ [0, 20] V · V_DS ∈ [0, 1200] V · T ∈ [298, 448] K
- 双端对称导通，通过 Gummel 对称性测试（0.67%）

**验证结果**

| 指标 | 结果 |
|------|------|
| 整体 MAPE | **0.957%**（目标 < 3%，超越 3.1×） |
| 亚阈值 MAPE | 4.59% |
| 强反型 MAPE | 0.21% |
| R² | 0.99904 |

- 技术栈：Python / PyTorch / Silvaco TCAD / LTspice / MATLAB
- 流水线：TCAD 数据 → PINN 混合模型 → 参数提取 → SPICE 模型生成 → 精度验证
- 兼容 LTspice / ngspice / HSPICE

[进入项目仓库 →](https://github.com/3072963Charles/PINN-SiC-MOSFET)

---

## 技术栈

| 领域 | 技术 |
|------|------|
| 器件建模与仿真 | PyTorch / PINN / Silvaco TCAD / LTspice / MATLAB |
| 后端与 AI | Python / FastAPI / YOLO / MediaPipe / Qwen |
| 嵌入式 | ESP32 / STM32 / Arduino / RTOS |
| 其他 | 信号与系统 / 计算机网络 / 数字系统设计 |

---

## 联系

- GitHub: [3072963Charles](https://github.com/3072963Charles)（代码仓库）· [AI-FanGe](https://github.com/AI-FanGe)（AIoT 项目）
- Email: 3169548541@qq.com

欢迎交流功率半导体建模、AIoT 硬件与开源项目合作。

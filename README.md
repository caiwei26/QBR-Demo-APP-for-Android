# QBR - Quad Bayer Remosaic (Android)

> **2026 Quad Bayer Remosaic Project**
> **Designed by SUN Yuxin, UESTC**

![Android](https://img.shields.io/badge/Platform-Android-green)
![PyTorch](https://img.shields.io/badge/AI-PyTorch%20Mobile-orange)
![OpenCV](https://img.shields.io/badge/Vision-OpenCV-blue)
![License](https://img.shields.io/badge/License-Academic-lightgrey)

## 📖 简介 (Introduction)

**QBR (Quad Bayer Remosaic)** 是一个基于深度学习的 Android 端侧图像处理应用。本项目旨在解决 Quad Bayer 传感器在非 Binning 模式下的分辨率损失问题，通过部署轻量化但高性能的深度残差网络（Deep Residual Network），在移动端实现从 RAW 数据到高清 RGB 图像的端到端重建。

与传统插值算法相比，本应用利用 **PyTorch Mobile** 和 **OpenCV**，在骁龙等移动平台上实现了 **SOTA 级别** 的重建质量（PSNR > 40dB），并支持无损 PNG 导出。

## ✨ 核心特性 (Features)

*   **🧪 双模式工作流**：
    *   **仿真实验 (Simulation)**：输入 Ground Truth，自动下采样并重建，实时计算 **PSNR/SSIM** 指标，用于学术评估。
    *   **真实增强 (Real-world)**：针对真实拍摄照片，支持 **分块推理 (Tiled Inference)** 技术，可处理 12MP+ 高分辨率大图而不发生 OOM。
*   **🧠 端侧 AI 推理 (Edge AI)**：
    *   完全离线运行，无需上传云端，保护用户隐私。
    *   集成 **纯净 (Clean)** 与 **抗噪 (Robust)** 双模型，适配不同光照场景。
*   **🎨 专业后处理**：
    *   内置 OpenCV 边缘感知去马赛克 (Edge-Aware Demosaicing)。
    *   支持自适应 **USM 锐化**。
    *   支持 **PNG 无损格式** 保存到相册。
*   **📱 沉浸式 UI**：
    *   适配 Android 13+，采用 Material Design 风格，全屏沉浸式体验。

## 📸 应用截图 (Screenshots)

<!-- 请在仓库中创建一个 screenshots 文件夹，放入截图后取消注释 -->
<!--
| 主界面 | 仿真模式 | 增强模式 |
|:---:|:---:|:---:|
| <img src="screenshots/home.jpg" width="200"/> | <img src="screenshots/sim.jpg" width="200"/> | <img src="screenshots/real.jpg" width="200"/> |
-->

## 🛠️ 技术栈 (Tech Stack)

*   **语言**: Kotlin
*   **推理引擎**: PyTorch Mobile (Lite Interpreter)
*   **图像处理**: OpenCV Android SDK 4.x
*   **架构**: MVVM, Coroutines (异步处理)
*   **关键算法**: Coordinate Attention, Tiled Inference

## 📅 更新日志 (Changelog)

### v26.2.3 (2026-02-16)
- **⚡ 性能优化**：
    - 引入分块推理 (Tiled Inference) 机制，彻底解决大分辨率图像 (3MB+) 处理时的内存溢出 (OOM) 问题。
    - 针对移动端 CPU (如 Snapdragon 8 Gen 3) 进行了多线程并行优化。
- **🎨 UI 升级**：
    - 重构主界面为全沉浸式白色顶栏，优化了视觉层级。
    - 增加了详细的使用说明引导。
- **💾 功能增强**：
    - 新增 PNG 无损导出功能，确保重建画质不被压缩。
    - 修复了部分机型上的红蓝通道反转 (RB-Swap) 问题。

### v26.2.2 (2026-02-10)
- 初始版本发布。
- 完成基础模型 (Clean/Robust) 的移动端部署。
- 实现基础的仿真实验功能。

## 📥 安装与使用 (Installation)

1.  进入本仓库的 [Releases](../../releases) 页面下载最新版 APK (`QBR_v1.0.apk`)。
2.  在 Android 设备上允许“安装未知来源应用”。
3.  安装并打开应用，授予**相册访问权限**（用于读取测试图片及保存结果）。
4.  **使用建议**：
    *   建议使用搭载 **Snapdragon 888** 或更高性能芯片的设备以获得最佳推理速度。
    *   处理大图时请耐心等待，AI 运算需要时间。

## ⚠️ 系统要求 (Requirements)

*   **系统**: Android 8.0 (Oreo) 及以上 (推荐 Android 13+)
*   **架构**: arm64-v8a (仅支持 64 位设备)
*   **内存**: 建议 6GB RAM 以上

## 📄 许可证 (License)

本项目仅供 **电子科技大学 (UESTC)** 毕业设计学术交流与研究使用，未经作者许可不得用于商业用途。

## 📧 联系方式 (Contact)

*   **作者**：SUN Yuxin (孙宇新)
*   **学校**：电子科技大学 (UESTC)
*   **学院**：集成电路科学与工程学院

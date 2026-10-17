# 灵录 ScreenFlow — Windows 发行包

**灵录 ScreenFlow** 是一款轻量级跨平台本地录屏工具（基于 Electron 构建），支持屏幕录制、音视频处理与本地语音转写（ASR）。本目录为 Windows x64 免安装（unpacked）发行包。

## 快速开始

1. 解压或进入 `win-unpacked/` 目录。
2. 双击运行 `灵录 ScreenFlow.exe` 即可启动，无需安装。
3. 首次使用语音转写功能时，可在应用设置页按需下载 ASR 模型。

## 目录结构

```
LingLu_release/
├── builder-debug.yml          # electron-builder 打包调试配置
└── win-unpacked/              # Windows x64 免安装包
    ├── 灵录 ScreenFlow.exe     # 应用主程序
    ├── resources/
    │   ├── app.asar           # 应用代码包（linglu-screenflow v0.1.0）
    │   ├── ffmpeg.exe         # 音视频转码
    │   ├── ffplay.exe         # 音视频播放
    │   ├── ffprobe.exe        # 媒体信息探测
    │   ├── whisper/           # whisper.cpp 本地语音识别运行时（含多平台 CPU 后端）
    │   └── model-manifest.json# ASR 模型下载清单（含 SHA256 校验与镜像源）
    └── locales/               # Chromium 多语言资源
```

## 语音转写（ASR）模型

应用内置 whisper.cpp 本地推理引擎，模型来源为 Hugging Face `ggerganov/whisper.cpp`，支持多语言（含中文）：

| 模型 | 大小 | 说明 |
|------|------|------|
| Tiny | 74 MB | 随应用分发，启动即可用；适合低配机型（≥1 GB 内存）快速预览，准确率偏低 |
| Small（推荐） | 488 MB | 体积与准确率的最佳平衡点，中文日常场景表现良好（≥2 GB 内存），需在设置页下载 |

- 下载支持断点重试（3 次）与 SHA256 校验，主源不可用时自动切换国内镜像（hf-mirror.com）。
- 全部转写在本地完成，无需联网上传音视频。

## 运行环境

- Windows 10 / 11（64 位）
- 内存：建议 4 GB 及以上
- 磁盘空间：约 500 MB（不含可选 ASR 模型）

## 许可

- 应用本体：私有软件（UNLICENSED），版权归 yajunjiao 所有。
- Electron 与 Chromium 组件许可见 `win-unpacked/LICENSE.electron.txt` 与 `win-unpacked/LICENSES.chromium.html`。
- FFmpeg、whisper.cpp 等第三方组件遵循其各自的开源许可。

# Stable Diffusion WebUI 本地运行指南

## 环境要求

- Python 3.10.x（推荐 3.10.6）
- Git
- NVIDIA GPU（建议 6GB 以上显存）
- Windows 10/11

## 模型文件放置

在运行之前，需要将模型文件放到指定目录：

| 文件类型 | 存放路径 |
|---------|---------|
| 主模型（.safetensors / .ckpt） | `models/Stable-diffusion/` |
| VAE 模型 | `models/VAE/` |
| LoRA 模型 | `models/Lora/` |

## 启动方式

在 `stable-diffusion-webui` 目录下运行：

```batch
webui-user.bat
```

首次运行时，脚本会自动：
1. 创建 Python 虚拟环境（`venv` 目录）
2. 安装所有依赖包
3. 下载必要的模型组件

## 自定义启动参数

编辑 `webui-user.bat` 文件，在 `COMMANDLINE_ARGS=` 后添加参数：

```batch
set COMMANDLINE_ARGS=--xformers --autolaunch
```

常用参数说明：

| 参数 | 说明 |
|-----|------|
| `--xformers` | 启用 xformers 加速，减少显存占用 |
| `--autolaunch` | 启动后自动打开浏览器 |
| `--medvram` | 中等显存优化（6-8GB 显存） |
| `--lowvram` | 低显存优化（4GB 显存） |
| `--listen` | 允许局域网访问 |
| `--port 7860` | 指定端口号 |

## 访问 Web 界面

启动成功后，在浏览器中访问：

```
http://127.0.0.1:7860
```

## 使用 LoRA 模型

1. 将 LoRA 文件复制到 `models/Lora/` 目录
2. 在 WebUI 的 txt2img 或 img2img 页面中，点击 "Lora" 标签
3. 选择你的 LoRA 模型
4. 在提示词中使用以下格式调用：

```
<lora:模型名:权重>
```

示例：

```
<lora:Chinese_painting:0.8>
```

权重范围为 0-1，建议从 0.6-0.8 开始调整。

# 🧬 Polyploid Gene Family AI Pipeline

> **An AI Skill for automated polyploid gene family analysis and seamless cloning primer design.**

[![License: MIT](https://img.shields.io/badge/License-MIT-blue.svg)](LICENSE)
[![Platform](https://img.shields.io/badge/Platform-Windows%20%2B%20WSL2-lightgrey)]()
[![AI Agent](https://img.shields.io/badge/AI-DeepSeek--v4--Pro-orange)]()

This repository provides a reusable **AI Skill** that transforms a complex multi-step bioinformatics workflow into a standardized and reproducible SOP. It integrates genome-wide gene family identification, comparative genomics, evolutionary analysis, cross-platform execution (Windows + WSL2), and seamless cloning primer design into a single AI-driven workflow.

本项目旨在帮助研究人员（尤其是生信基础较弱的实验人员）快速完成从**参考基因组**到**湿实验验证**的完整分析流程，实现真正意义上的 Dry-lab → Wet-lab 自动化。

最初为解析同源四倍体紫花苜蓿（*Medicago sativa*）等复杂多倍体基因组而设计，本流水线能够通过本地大语言模型（如 DeepSeek），自动调度 Windows 与 WSL2 (Ubuntu) 双系统资源，实现从原始参考基因组到无缝克隆引物设计的一键式产出。

## ✨ 核心功能 (Core Features)

- 🔍 **多倍体基因家族智能挖掘**：自动跨平台调用 HMMER，执行结构域搜索与转录本去冗余。
- 📊 **单倍型变异解析 (PAV/CNV)**：自动映射并计算同源基因保留率（1:4 严格保守）、拷贝数变异（CNV）与存在/缺失变异（PAV）。
- 🌳 **系统发育与候选集降噪**：自动调用 MAFFT 与 FastTree，结合表达量与进化保守性计算“候选基因优先级评分”。
- 🧪 **湿实验级引物自动化设计**：解析载体文件（如 pCAMBIA1300），自动根据靶点 SNP 修正简并碱基（IUPAC），输出带同源臂的无缝克隆（Seamless Cloning）完整引物与实验 Protocol。

## 📂 仓库结构 (Repository Structure)

```text
Polyploid-GeneFamily-AI-Pipeline/
│
├── README.md                 ← 项目说明（本文件）
├── LICENSE                   ← 开源协议
├── SKILL.md                  ← 🤖 核心 AI 提示词库（包含 YAML 元数据，可直接导入 Agent 平台）        
└── environment_consistency_check/ 
    ├── check_env.py          ← 🛠️ Windows-WSL2 混合环境一键自检脚本
    └── operating_manual.txt  ← 说明文档

```

## 🚀 快速开始 (Quick Start)

### 1. 环境准备与自检

本流水线依赖 Windows (Python) 与 WSL2 (Ubuntu) 的协同工作。请确保已安装相关的生信工具（HMMER, MAFFT, FastTree）。

将代码克隆到本地后，在包含参考基因组（如 `ZM4_V2/`）的工作目录下运行自检脚本：

```bash
python check_env.py

```

> **注：** 脚本会自动检测 Python 依赖库与 WSL2 内部工具链，若有缺失将输出明确的修复指令（如 `sudo apt-get install`）。

### 2. 唤醒 AI Agent

1. 打开您的本地 AI 客户端（如 WorkBuddy）或直接使用 DeepSeek 对话框。
2. 打开本仓库中的 `SKILL.md` 文件，将其中的**主体 Prompt 模板**完整复制并发送给大模型（或将其配置为 Agent 的 System Prompt）。

### 3. 提交分析任务

按照 AI 的引导，提供以下参数即可全自动完成分析：

```text
目标基因家族：...
PFAM ID：PF00000
目标性状：...
载体线性化方式：KpnI 单酶切

```

## ⚠️ 使用注意事项 (Important Notes)

* **零污染原则**：本流水线内置硬性约束，严格区分不同单倍型（如 V2 与 HAP1）的输出路径。
* **环境桥接**：所有重型计算任务将由 AI 自动生成带有 `wsl -d Ubuntu-24.04 --` 前缀的 Python 代码进行调用，避免了复杂的环境配置。
* **审慎验证**：虽然 AI 会自动处理简并碱基与 Tm 值平衡，但在向合成公司提交引物订单前，建议人工抽查靶点的 SNP 匹配情况。

## 🤝 贡献与反馈

欢迎通过 Issue 提交您在使用过程中遇到的问题，或通过 Pull Request 补充对其他多倍体物种（如小麦、甘蔗）的适配优化。

## 📄 许可证

本项目采用 MIT License 开源许可证。

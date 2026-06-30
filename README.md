# MiniCode Python

<p align="center">
  <strong>轻量级本地终端编程助手 — 可观测、可恢复、可检验的 coding agent</strong>
</p>

<p align="center">
  <a href="https://github.com/LiuMengxuan04/MiniCode">MiniCode Main</a> |
  <a href="https://github.com/QUSETIONS/MiniCode-Python">Python Repo</a>
</p>

<p align="center">
  <img alt="Python" src="https://img.shields.io/badge/Python-3.11%2B-3776AB?style=flat-square&logo=python&logoColor=white">
  <img alt="Tests" src="https://img.shields.io/badge/tests-1000%2B%20passed-brightgreen?style=flat-square">
</p>

MiniCode Python 是 MiniCode 家族的 Python 运行时，聚焦于**会话持久化、编辑可回退、内存连续性、运行时可观测**。

---

## 快速开始

```bash
# 安装
git clone https://github.com/QUSETIONS/MiniCode-Python.git
cd MiniCode-Python
pip install -e .[dev]

# 启动交互模式
minicode-py

# 单次执行模式
minicode-headless "Explain what this repo does."
```

---

## 常用命令

| 命令 | 作用 |
|------|------|
| `/session` | 查看当前会话快照 |
| `/sessions` | 列出已保存的会话 |
| `/session-replay` | 回放会话 |
| `/memory` | 查看记忆系统状态 |
| `/checkpoints` | 查看检查点历史 |
| `/rewind-preview` | 预览回退 |
| `/rewind` | 执行回退 |
| `/readiness` | 检查运行时健康状态 |

---

## 架构

```
User → agent_loop → turn_kernel (phase policy, widening, verify)
         ↕              ↕
      Memory Stack    Local Tools (files, search, edit, shell)
         ↕
   CyberneticOrchestrator (compact, checkpoint, rewind, recover)
```

---

## 核心模块

| 模块 | 职责 |
|------|------|
| `agent_loop.py` | 主循环：模型调用、工具调度、事件流 |
| `turn_kernel.py` | 步骤策略、阶段切换、拓宽、验证门 |
| `session.py` | 持久化会话、回放、检查点、回退 |
| `memory.py` / `working_memory.py` / `memory_pipeline.py` | 记忆系统：长短期记忆、检索注入、反思写回 |
| `cybernetic_orchestrator.py` | 运行时控制面：压缩、预算、回退、恢复 |
| `cost_tracker.py` | API 成本与用量追踪 |
| `model_switcher.py` | 模型降级与故障转移 |

---

## 仓库结构

| 路径 | 说明 |
|------|------|
| `minicode/` | 主包 |
| `tests/` | 测试套件 |
| `benchmarks/` | 性能基准、压力测试、发布检查 |
| `docs/` | 架构文档与优化记录 |

---

## MiniCode 家族

| 版本 | 仓库 | 定位 |
|------|------|------|
| TypeScript | [LiuMengxuan04/MiniCode](https://github.com/LiuMengxuan04/MiniCode) | 主终端 agent，TUI，MCP，Skills |
| Python | [QUSETIONS/MiniCode-Python](https://github.com/QUSETIONS/MiniCode-Python) | 本地优先，会话/回退/可观测性 |
| Rust | [harkerhand/MiniCode-rs](https://github.com/harkerhand/MiniCode-rs/tree/master) | 系统级实现 |
| Java | [hobbescalvin414-tech/minicode4j](https://github.com/hobbescalvin414-tech/minicode4j) | Java 实现 |

---

## 当前状态

```text
1030 passed, 2 skipped
```

核心运行时、会话、回放、检查点、回退、就绪检查功能已就绪。项目仍在持续打磨中。

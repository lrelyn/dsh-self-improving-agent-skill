# dsh-self-improving-agent-skill

DeepSeek Harness 的「自我改进型智能体」技能（Skill），把单个任务做得更稳、把经验跨会话积累下来。

## 这是什么

一个可复用的 DSH 本地技能，核心工作循环：**执行 → 观察 → 反思 → 固化 → 复用**。

适用于：
- 任务失败或反复出问题，需要找根因并避免重犯
- 做完一个重要/长任务后沉淀经验
- 跨会话做同一类工作，希望越做越稳

## 安装

把 `SKILL.md` 放入 DSH 全局技能目录：

```
<DSH_HOME>/skills/self-improving-agent/SKILL.md
```

（`<DSH_HOME>` 默认 `~/.dsh`，Windows 下为 `C:\Users\<用户名>\.dsh`）

同时创建全局经验库：

```
<DSH_HOME>/skills/_reflections/REFLECTIONS.md
```

## 结构

```
self-improving-agent/
└── SKILL.md        # 技能指令（本文件）
```

- **SKILL.md**：自我改进工作流指令
- **REFLECTIONS.md**（另建）：跨会话共享的唯一经验库，各会话往里追加复盘

## 使用

DSH 在情境匹配到"自我改进 / 复盘 / 固化经验"时会加载此 skill。加载后按其中的「任务执行协议」执行。

## 授权

MIT
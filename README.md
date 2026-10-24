# WPS C++ 编码规范 Skill

将金山办公《C++编码规范（2026高校版）》整理为 Codex 可复用的编码 skill，用于编写、修改、重构和审查 C++ 代码。

- Skill 名称：`wps-cpp-standard`
- 依据文档：[C++编码规范（2026高校版）](https://365.kdocs.cn/l/ccsMRFK0iQLx?openfrom=docs)
- 阅读快照：2026-10-24，文档版本 6，共 17 页
- 覆盖范围：11 章，46 个编号小节，以及第 11 章其他规范
- 自动匹配：已启用；适用于 C++，不用于纯 C 或其他语言

## 内容

```text
wps-cpp-standard/
├── SKILL.md                    执行入口、适用范围与自审流程
├── agents/
│   └── openai.yaml             显示信息与自动匹配设置
└── references/
    ├── rules.md                按原文节号整理的完整规则
    └── source-notes.md         来源、原文冲突、实施限定与代码示例
```

[阅读 Skill](wps-cpp-standard/SKILL.md) · [完整规则](wps-cpp-standard/references/rules.md) · [来源与纠错](wps-cpp-standard/references/source-notes.md)

## 安装和使用

在支持 `skill-installer` 的 Codex 中输入：

```text
使用 $skill-installer 安装 https://github.com/wangzhiyao-sys/C-programming/tree/main/wps-cpp-standard
```

也可将仓库克隆到固定位置，再把其中的 `wps-cpp-standard` 目录链接到个人技能发现目录 `~/.agents/skills/`。若已有同名技能，应先核对现有安装，不要创建重复条目或直接覆盖个人改动。

安装后可自然描述 C++ 编码任务，也可显式调用：

```text
使用 $wps-cpp-standard 实现这个 C++ 功能，并在交付前按规范自审。
```

```text
使用 $wps-cpp-standard 审查这些 C++ 文件，按位置、条款和修改建议列出问题。
```

Codex 根据 skill 的描述决定是否自动调用；显式调用能明确指定本次使用的规范。若安装后列表尚未更新，重新打开 Codex。

## 执行边界

规则保留原文“必须/禁止”和“建议/优先”的强度差别，遵守用户当前指令及适用项目约束，保留必要的框架接口和兼容性例外。启用 skill 不代表自动格式化整个仓库。

原文的智能指针、getter、include 顺序等示例存在笔误或冲突。头文件 guard 的双下划线写法还涉及 C++ 保留标识符。修正依据与原文写法均保留在 [来源与纠错](wps-cpp-standard/references/source-notes.md)，没有把修正伪装成原文要求。

## 验证与维护

初始版本已完成：

- 使用 `skill-creator` 的 `quick_validate.py` 校验 skill 结构。
- 核对 46 个编号小节及相对引用链接。
- 核对 `agents/openai.yaml`，启用 `allow_implicit_invocation`。
- 使用 Apple Clang，以 C++11 和 C++17、`-Wall -Wextra -Wpedantic -Werror` 编译并运行文中的最小示例。

这些结果验证结构和小范围示例，不代表已测试每一种真实项目中的调用和代码生成行为。

更新规范时，同时核对 `SKILL.md`、完整规则、纠错说明和元数据；记录新的原文版本与阅读日期。原始在线文档的变化不会自动同步到此仓库。通过复制方式安装的个人 skill 也不会随仓库更新自动变化，需要同步已核对的文件。

技能机制与本地发现目录可参见 [Codex 官方技能文档](https://learn.chatgpt.com/docs/build-skills)。

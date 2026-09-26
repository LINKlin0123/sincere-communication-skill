# sincere-communication-skill（真诚沟通 skill）

![Stars](https://img.shields.io/github/stars/LINKlin0123/sincere-communication-skill?style=flat-square)
![Forks](https://img.shields.io/github/forks/LINKlin0123/sincere-communication-skill?style=flat-square)
![Issues](https://img.shields.io/github/issues/LINKlin0123/sincere-communication-skill?style=flat-square)
![License](https://img.shields.io/github/license/LINKlin0123/sincere-communication-skill?style=flat-square)
![Version](https://img.shields.io/github/v/tag/LINKlin0123/sincere-communication-skill?style=flat-square)

一个给 AI agent 用的沟通 skill。帮你写**道歉、心里话（情书/表白/纪念日）、高难度对话脚本**。

它不堆漂亮话。它先问清楚到底发生了什么，再按成熟的沟通框架组织语言，最后把 AI 味洗掉，写到像你本人发微信。

---

## 目录

- [解决什么问题](#解决什么问题)
- [它和"直接让AI写"差在哪](#它和直接让ai写差在哪)
- [快速演示](#快速演示)
- [安装](#安装)
- [怎么用（重要）](#怎么用重要)
- [工作流程](#工作流程)
- [三种场景怎么触发](#三种场景怎么触发)
- [目录结构](#目录结构)
- [工作原理](#工作原理)
- [常见问题](#常见问题)
- [参考资料](#参考资料)
- [License](#license)

---

## 解决什么问题

你一定干过这种事：跟对象吵完架，打了一长段字，读了三遍，全删了。发出去怕显得卑微，不发又堵得慌。

或者纪念日想写点什么，打开对话框，敲出来全是"你是我的光""余生请多指教"——这种话连你自己都不信，发出去对方一眼就知道是抄的。

又或者想提意见，话到嘴边又咽回去，怕一开口就变成吵架。

这个 skill 就是管这些时刻的。

## 它和"直接让AI写"差在哪

直接跟 AI 说"帮我写封道歉信"，它会给你这种东西：

> "我错了，请求你的原谅。这段时间我反思了很多，我们都要珍惜彼此。"

你根本发不出去。因为它不知道你俩昨天到底为什么吵、对方说了哪句话、你心里哪句是真的。

这个 skill 换了个做法：

1. **先问你**：具体发生了什么、对方什么反应、你到底想要什么结果。你给不出细节，它会直接说"给我个具体画面，不然写出来你不敢发"，而不是瞎编。
2. **套框架**：道歉用《道歉的五种语言》（*The Five Languages of Apology*），对话用《非暴力沟通》（*Nonviolent Communication*）。
3. **洗 AI 味**：对照一张自检清单，把排比、升华、工整的四段结构全拆掉，写到像微信一句句蹦出来的。

## 快速演示

你给它这段背景：

> "昨晚打游戏，女朋友连发几条问我几点结束，我嫌烦回了句'能不能别老催我'。其实她是身体不舒服想找我。"

它输出（见 [`examples/apology-example.md`](examples/apology-example.md)）：

> 昨晚你连着发消息，我回你那句"能不能别老催我"，是我不对。你不是在催我，是不舒服想找我说一声，我却只顾着游戏把你顶回去了。
>
> 换我，难受的时候等来这么一句，也会觉得自己还不如一局游戏重要。
>
> 以后打游戏我先跟你说几点结束。你有事直接打电话，我一定接。

短、碎、有具体细节，没有"我错了行了吧"，也没有空头保证。

三种场景的完整示例：

- 道歉：[`examples/apology-example.md`](examples/apology-example.md)
- 心里话：[`examples/letter-example.md`](examples/letter-example.md)
- 高难度对话：[`examples/conversation-example.md`](examples/conversation-example.md)

## 安装

本 skill 是一个标准目录，把整个 `sincere-communication-skill/` 文件夹放进对应 agent 的 skills 目录即可。不需要装依赖，不需要联网，不需要 GPU。

### Claude Code

把文件夹放到：

```
~/.claude/skills/sincere-communication-skill/
```

放好后重启 Claude Code，新开一个对话就能用。

### Cursor

把文件夹放到项目里的 `.cursor/skills/`，或 Cursor 的全局 skills 目录。

### OpenClaw、Codex、其他兼容 Agent Skills 的 agent

放进各自识别的 skills 目录，确保 agent 能读到里面的 `SKILL.md`。路径随版本变化，以对应 agent 官方文档为准。

## 怎么用（重要）

装好了，**别一上来就说"帮我写情书"**。那样它还是会给你套话。

正确姿势是把它当一个采访你的人。第一次对话，把背景一次性说清楚：

```
我想道歉。昨晚打游戏，她连发消息问我几点结束，
我嫌烦回了句"能不能别老催我"。其实她是不舒服想找我。
我想和好，但不想显得卑微。
```

它会追问你缺的细节。**你给的细节越真，写出来越能发。** 至少告诉它这四样：

1. **发生了什么**：什么时候、在哪、谁说了什么
2. **现在的状态**：对方是冷战、哭了、还是表面没事
3. **你想要什么**：和好 / 让对方知道 / 只是把话说开
4. **一个具体细节**：对方的某个小动作，或者你俩之间的某件小事

它写出来之后，**自己读一遍再发**。哪句不像你说的，直接让它改："这句太肉麻了，重写。"

## 工作流程

```
你说需求
   │
   ▼
它问你要背景（具体事件 / 对方状态 / 你要的结果 / 细节）
   │  给不出 → 它追问，不替你编
   ▼
按场景选框架
   ├ 道歉 → 道歉三段 + 五种道歉语言
   ├ 心里话 → 细节驱动，不写套话
   └ 对话 → 非暴力沟通，把话揉碎了说
   ▼
洗 AI 味（拆工整结构、删升华、删套话）
   │
   ▼
对照自检清单过一遍 → 给你成稿
```

## 三种场景怎么触发

直接用大白话就行：

| 你想干嘛 | 可以这么说 |
|---|---|
| 道歉 | "我做错了事，帮我想想要怎么开口" |
| 写心里话 | "纪念日想给他/她写段话，不想太肉麻" |
| 表白 | "我喜欢一个人，想跟他说，帮我理一下怎么说" |
| 提意见/谈敏感事 | "他打游戏太吵，我想提一下又怕吵架" |
| 回消息 | "他发了这句，我该怎么回" |

## 目录结构

```
sincere-communication-skill/
├── SKILL.md                    # 入口：触发条件 + 总流程
├── references/
│   ├── apology.md               # 道歉三段 + 五种道歉语言
│   ├── letter.md                # 心里话框架
│   ├── conversation.md          # 非暴力沟通四要素
│   ├── de-ai-rules.md           # 去 AI 味规则（负面清单）+ 自检
│   └── real-patterns.md         # 真人说话模式（正面清单，从真实案例提炼）
├── examples/
│   ├── apology-example.md       # 道歉示例
│   ├── letter-example.md        # 心里话示例
│   └── conversation-example.md  # 对话示例
├── README.md
└── LICENSE                      # MIT
```

## 工作原理

- `SKILL.md` 顶部有一段 frontmatter（名称和描述），agent 读到后判断什么时候该启用这个 skill
- 启用后，它会按里面写的流程走，需要时再读 `references/` 下的具体框架
- `references/de-ai-rules.md` 里有一张自检清单，输出前强制过一遍
- 所有内容基于你给的真实背景，它不替你编故事

## 常见问题

**它会替我编内容吗？**
不会。背景不够它会追问，或者把拿不准的地方标出来让你确认。

**只能谈恋爱用吗？**
不是。给朋友、家人、同事道歉，职场提意见、谈敏感话题都能用。

**写出来对方就一定会原谅我吗？**
不能保证。它只负责让你说得清楚、真诚、不踩雷。原不原谅取决于事情本身和你们的关系。它也不会帮你逼对方立刻原谅。

**为什么限制 200 字？**
道歉和心里话越长越像抄的。短而具体，对方才信。

**我心理上很难受，这能当心理咨询用吗？**
不能。它是表达辅助工具，不是心理治疗。严重的情绪或关系问题，请找专业心理咨询。

## 参考资料

- Gary Chapman & Jennifer Thomas，《道歉的五种语言》（*The Five Languages of Apology*）
- Marshall Rosenberg，《非暴力沟通》（*Nonviolent Communication: A Language of Life*）
- 去 AI 味规则参考了 [`avoid-ai-writing`](https://github.com/conorbronsdon/avoid-ai-writing)（去AI写作，4.7k 星）的分级思路

## License

[MIT](LICENSE)

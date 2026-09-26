# sincere-communication-skill（真诚沟通 skill）

![Stars](https://img.shields.io/github/stars/LINKlin0123/sincere-communication-skill?style=flat-square)
![Forks](https://img.shields.io/github/forks/LINKlin0123/sincere-communication-skill?style=flat-square)
![Issues](https://img.shields.io/github/issues/LINKlin0123/sincere-communication-skill?style=flat-square)
![License](https://img.shields.io/github/license/LINKlin0123/sincere-communication-skill?style=flat-square)

一个给 AI agent 用的沟通 skill。主打**道歉**，附带高难度对话。

它不帮你写一封漂亮的道歉信。它帮你想清楚：先发什么、等什么反应、他回了怎么接、他不回怎么办。给两个版本（稳妥版/自然版），分步执行，不是一段长文。

---

## 快速开始

**装：** 把整个文件夹下载下来，丢进你 agent 的 skills 目录：

```
Claude Code:  ~/.claude/skills/sincere-communication-skill/
Cursor:       你的项目/.cursor/skills/sincere-communication-skill/
其他 agent:    放进各自识别的 skills 目录
```

**用：** 重启 agent，新开对话，直接说人话就行：

> "我跟她吵架了，两天没说话了，帮我想想要怎么开口"

它会先问你情绪和背景，然后给你分步方案——先发什么、他回了怎么接、不回怎么办。

**就这么简单。** 不需要装依赖，不需要联网，不需要配置。

---

## 解决什么问题

跟对象吵完架，打了一长段字，读了三遍，全删了。发出去怕卑微，不发堵得慌。

或者想提意见，话到嘴边咽回去，怕一开口就变成吵架。

这个 skill 管这些。

## 和直接让 AI 写道歉有什么区别

直接跟 AI 说"帮我写道歉信"，它给你一段完整的话：

> "我错了，请求你的原谅。这段时间我反思了很多，我们都要珍惜彼此。"

你发不出去。

这个 skill 不这么干。它：

1. **先接情绪**——你现在是慌还是气，先认这个
2. **再问事实**——具体发生了什么，他现在什么状态
3. **给两个版本**——稳妥版和自然版，你挑
4. **分步给方案**——第一条发什么，他回了怎么接，不回怎么办，不是一次写完
5. **洗 AI 味**——写成微信分条发，不是道歉函

## 怎么用

直接说人话：

```
我想道歉。昨晚打游戏，她连发消息问我几点结束，
我嫌烦回了句"能不能别老催我"。其实她是不舒服想找我。
她现在两天没回我了。
```

它会先问你情绪，再补问细节，然后给你分步方案。

## 输出长什么样

不是一段长文，是这样的：

> **第一条先发：**
> 还生气吗
>
> **她回了"你说"，你发：**
> 昨晚那句"能不能别老催我"，挺伤人的。
>
> **她没回，等到晚上再发：**
> 我知道你不想理我。你先忙你的。
>
> **她回了很冷淡：**
> 以后打游戏我先跟你说几点结束。你有事直接打电话。

完整示例见 [`examples/apology-example.md`](examples/apology-example.md)。

## 触发方式

| 你想干嘛 | 可以这么说 |
|---|---|
| 道歉 | "我做错了事，帮我想想要怎么开口" |
| 吵架了不知道怎么回 | "他发了这句，我该怎么回" |
| 提意见/谈敏感事 | "他打游戏太吵，我想提一下又怕吵架" |
| 对方冷战了 | "他两天没理我了，怎么办" |

## 目录结构

```
sincere-communication-skill/
├── SKILL.md                    # 入口：流程 + 硬规则
├── references/
│   ├── apology.md               # 道歉框架 + 分步策略 + 应对分支
│   ├── conversation.md          # 非暴力沟通
│   ├── de-ai-rules.md           # 去 AI 味规则（负面清单）
│   └── real-patterns.md         # 真人说话模式（正面清单）
├── examples/
│   ├── apology-example.md       # 道歉分步示例
│   └── conversation-example.md  # 对话分步示例
├── README.md
└── LICENSE                      # MIT
```

## 安装

把整个目录放进 agent 的 skills 文件夹即可。不需要依赖。

## 常见问题

**写出来对方就会原谅我吗？**
不能保证。它只帮你说得清楚、不踩雷。原不原谅取决于事情本身。

**能帮我写情书吗？**
不能。这个 skill 只做道歉和高难度对话。

**我心理很难受，能当心理咨询用吗？**
不能。严重的情绪问题找专业心理咨询。

## 更新日志

见 [CHANGELOG.md](CHANGELOG.md)

## License

[MIT](LICENSE)

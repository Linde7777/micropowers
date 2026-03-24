# bionic-ai-coding

让AI编程助手像人类工程师一样记忆、计划、写代码

根据我的实践，AI在代码上的品味依然很糟糕，而垃圾代码又会加大AI写代码的难度 & 我不敢把一个我不熟悉的代码数量庞大的代码交给客户使用。AI coding 的瓶颈在于人类审查代码的速度，而不是AI写代码的速度。本技能合集并非为了快速产出代码而设计，而是为了代码质量而设计。

- AGENTS.md（放在~/.codex）: 包含了记忆机制。我最近在我的Agent项目上测试一个新版的流程，如果效果更好会改编到这里。

- create-plan: 个人认为比官方的plan mode和openai版本的create-plan都更好用。功能：
  - 不会让计划过于省略，以至于你理解的计划和ai想的计划不一致，也不会太详细，以至于和直接写代码差不多。
  - 代码质量控制。我之前加过`- 最小化改动：以最少的新抽象和文件变动实现目标`，但是发现这会让它不去修改不合理的设计（不修改就是最小化改动）。

- incremental-code-writing: 分步骤写代码，降低理解代码的难度，另外中途发现错了也可以立刻纠正。

## 致谢
本项目的部分内容受到了以下项目的启发：
OpenAI的create-plan
gstack
superpowers


## 另附：使用codex cli的注意事项

什么样难度的任务就要用什么样的推理程度，那种几行、十几行代码就能搞定的功能，你用 high 极大概率会过度工程化。

GPT-5.x-codex模型，我个人感觉这种模型，相对于GPT-5.x，显著缺乏常识，导致你在做功能的时候，要写清楚那些非常显而易见的东西，很麻烦。我在GPT-5.4上就感觉到了这一点

### 前端

OpenAI专门训练了GPT-5.4做前端： https://developers.openai.com/blog/designing-delightful-frontends-with-gpt-5-4

tldr: 

在 Codex 应用内运行以下命令来安装 frontend-skill：
```
$skill-installer frontend-skill
```

使用低、中等推理程度，对于更复杂的页面再用更高推理程度


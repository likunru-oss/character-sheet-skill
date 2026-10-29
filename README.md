# character-sheet · 人物三视图提示词技能

一个 [Claude Code](https://claude.com/claude-code) 技能（skill）：把一句人设，变成一条可以直接文生图的**超写实人物三视图**提示词，适配 Nano Banana Pro。

> **English summary:** A Claude Code skill that turns a short character brief into one production-ready, text-to-image prompt for a photoreal character sheet (Nano Banana Pro). Layout: head-and-shoulders close-up on the right; invisible-mannequin front full-body and back full-body on the left. The prompts are written in Chinese.

## 它解决什么问题

用 AI 生成真人风格角色做广告、短片分镜时，最难的是**同一个人在不同镜头里长得一样**。这个技能用一套反复出图验证过的固定模板，一次出齐角色的三个参考面板：

| 位置 | 内容 | 作用 |
|---|---|---|
| 右侧 | 头部和肩部特写 | 锁定脸 |
| 左侧上/前 | 正面全身照（隐形模特，无头，有手） | 锁定服装正面 |
| 左侧下/后 | 背面全身照（有头） | 锁定发型、肤色、体型 |

## 特点

- **一条提示词直接出图**：纯文生图，不需要参考图。
- **固定模板逐字照搬**：只替换方括号里的角色信息，版式和画质描述永远一致，出图稳定。
- **面部描写极细**：按"脸型 → 额头 → 眉 → 眼 → 皱纹 → 鼻 → 唇 → 下颌 → 胡须 → 发型 → 辨识特征 → 肤色"的固定顺序写。
- **只有一个辨识特征**：避免痣、斑在不同面板间漂移。
- **电影肖像式超写实风格**：后面再按角色单独写肤质、毛发、服装质感三行。
- **不用浅景深**：背景干净，适合当后续分镜的参考资产。
- **附出图验收清单和常见翻车对策**：版式跑偏、隐形模特长出头、自动加文字标签等，都有对应改法。
- **多角色选项表**：一次给 2–4 个候选人设，辨识特征不重样。

## 安装

把整个文件夹放到 Claude Code 的个人技能目录里：

```bash
git clone https://github.com/likunru-oss/character-sheet-skill.git ~/.claude/skills/character-sheet
```

重新打开 Claude Code 后自动生效。

## 使用

直接用中文说需求就会触发，例如：

- "帮我做一个人物三视图：35 岁拉丁裔女性加油站店员"
- "给主角出 3 个人设方案"
- "做一张 character sheet（人物设定图）"

技能只会追问缺失的关键项（角色定位、年龄、族裔、性别、身高、气质、服装方向），其余给默认值，交付时列出来让你改。

## 文件结构

```
character-sheet/
├── SKILL.md                 # 技能主体：输入收集、固定模板、写法规则、验收清单、翻车对策
└── references/
    └── examples.md          # 8 个完整示例（不同年龄、族裔、性别）
```

## 输出示例（节选）

```
生成人物三视图。
人物：一位 35 岁的墨西哥裔美国女性加油站便利店店员，身材中等偏丰满，肩膀圆润。鹅蛋脸偏圆，颧骨饱满……下唇右下方有一颗深棕色小痣作为辨识特征。……原创面孔，不像任何真实名人。
服装：不戴帽子，深红色翻领短袖棉质工作衫（无品牌标）……
……
面部瑕疵真实可见。
```

完整提示词见 `references/examples.md`。

## 注意

- 所有角色都是原创面孔，提示词里固定写明"不像任何真实名人"，也请不要用它模仿真实人物。
- 推荐比例 16:9，文件命名 `C-<编号>-sheet.png`。

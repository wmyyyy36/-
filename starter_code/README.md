# 第 5 周 · 任务槽位对照表（starter_code）

本目录按课程《第 5 周：意图造物与 ReAct 闭环编程实战》的任务槽位组织，一格一个可独立双击运行的单文件应用。
除 `03_buggy_practice` 是**故意保留报错**的演练件外，其余每一格都是本人从零迭代的成果，且与仓库 Git 历史中的具体提交一一对应。

| 槽位 | 对应任务 | 技术要点 | 来源提交 / 标签 | 实测状态 |
| --- | --- | --- | --- | --- |
| `01_mvp/index.html` | 任务二 意图造物 | Canvas 渲染 + `requestAnimationFrame` + RK4 定步长积分，无交互面板 | 由 `week05-interactive-baseline` 剥离面板得到（190 行） | 0 报错，画面正常摆动 |
| `02_interactive/index.html` | 任务三 渐进演进 | 摆长/重力/阻尼三滑块 + 数值标签实时联动 + 45° 复位 | 标签 `week05-interactive-baseline`（提交 `eb1a074`） | 0 报错，重置按钮生效 |
| `03_buggy_practice/index.html` | 任务四 报错自愈演练 | **故意注入**：按钮内联 `onclick="resetAnimation()"`，而真实函数名为 `resetSimulationState` 且未绑定 | 提交 `7621187` 的修复前状态还原 | 点击即抛 `Uncaught ReferenceError: resetAnimation is not defined`（第 167 行），报错可稳定复现 |
| `04_fixed_solution/index.html` | 任务四 自愈后基线 | 删除内联 `onclick`，改在脚本作用域内 `addEventListener('click', resetSimulationState)` | 提交 `7621187` | 0 报错；把摆角强设为 0.123 后点重置，实测回到 π/4 并继续正常摆动 |
| `bonus_a_double_pendulum/index.html` | 进阶挑战 A（选做） | 双摆拉格朗日方程 + RK4（步长 1/480 s）+ 320 点彩虹衰减拖尾 + 指针拖拽摆球 | 提交 `c932fc7`（`week07/index.html` 同源副本） | 0 报错；能量漂移 -0.0000% |
| `bonus_b_celestial_persistence/index.html` | 进阶挑战 B（选做） | 地球/月球/木星/太空四胶囊 + easeOutCubic 重力补间 + `localStorage` 自动存盘与刷新恢复 | 提交 `f1e0d1f`（`week05/index.html` 同源副本） | 0 报错；g=0 时理论周期显示"∞（失重·无恢复力）" |
| `template_report/` | 任务五 实验交付 | 标准 `.gitignore` 规则 + 实验报告骨架 + 人机协同三反思入口 | 提交 `da060bf` 之后 | 见 `template_report/README.md` |

## 关于"同源副本"

`02_interactive`、`bonus_a_double_pendulum`、`bonus_b_celestial_persistence` 三格与仓库内的权威文件**逐字节相同**，不做任何标题改写，目的是让批阅者能直接用 `git show` 对得上：

```
git show week05-interactive-baseline:week05/index.html   # = 02_interactive/index.html
git show HEAD:week07/index.html                          # = bonus_a_double_pendulum/index.html
git show HEAD:week05/index.html                          # = bonus_b_celestial_persistence/index.html
```

要改代码请改 `week05/index.html` / `week07/index.html` 这些权威文件，不要改这里的副本。

## 六格统一实测方法

在同一浏览器内用同源 `iframe` 依次加载六个槽位，每格挂载 `window.addEventListener('error')` 后模拟点击其重置按钮（`bonus_b` 额外点击"月球"胶囊），等待 0.7 秒采样：六格 Canvas 均正常创建，除 `03_buggy_practice` 按设计抛出唯一一条 `ReferenceError` 外，其余五格控制台 0 报错。

## 打包进提交包时的位置

提交包 `week05_Lab_7903126018_王梦芸.zip` 解压后，本目录的七个槽位文件夹直接位于压缩包顶层（不带 `starter_code/` 前缀），本对照表改名为顶层 `SLOT_MAP.md`，详细报告改名为顶层 `REPORT.md`，截图放在顶层 `screenshots/`。仓库内的权威路径仍是 `starter_code/…` 与 `week05/…`。

顶层这些"批阅视图"文件与仓库内权威文件**逐字节相同**，为避免同内容出现两份让 `git status` 刷屏，压缩包内 `.git/info/exclude` 追加了这 10 条顶层路径（该文件是本地忽略，不影响任何提交内容与历史）。校验对应关系请用：

```
git show week05-interactive-baseline:week05/index.html   # = 顶层 02_interactive/index.html
git show HEAD:week07/index.html                          # = 顶层 bonus_a_double_pendulum/index.html
git show HEAD:week05/index.html                          # = 顶层 index.html = 顶层 bonus_b_.../index.html
git show HEAD:starter_code/README.md                     # = 顶层 SLOT_MAP.md
```

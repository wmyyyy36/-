# 人机协同程序设计 · 第 5 周实验报告

## 一、实验信息

| 项目 | 内容 |
| :--- | :--- |
| 课程 | 人机协同程序设计（2026–2027 学年第一学期） |
| 周次 | 第 5 周 · 意图造物与 ReAct 闭环编程实战 |
| 姓名 | 王梦芸 |
| 学号 | 7903126018 |
| 专业 | 食品质量与安全 |
| 完成日期 | 2026-10-13 |
| GitHub 作品集 | https://github.com/wmyyyy36/- |
| 本周目录 | https://github.com/wmyyyy36/-/tree/main/week05 |

## 二、任务与提交物映射

| 实验任务 | 本包位置 | 状态 |
| :--- | :--- | :--- |
| 任务二 意图造物（MVP） | `01_mvp/index.html` | 已通过，控制台 0 报错 |
| 任务三 渐进演进（参数面板） | `02_interactive/index.html` | 已通过，三滑块实时联动 |
| 任务四 报错自愈演练 | `03_buggy_practice/index.html` | 按设计抛 `ReferenceError`，可复现 |
| 任务四 自愈后基线 | `04_fixed_solution/index.html` | 已通过，重置后角度回 45°，0 报错 |
| 进阶挑战 A 双摆混沌 | `bonus_a_double_pendulum/index.html` | 已完成（选做） |
| 进阶挑战 B 天体预设 + 持久化 | `bonus_b_celestial_persistence/index.html` | 已完成，即最终提交版 |
| 任务五 实验交付 | 本文件 + 仓库根 `README.md`、`week05/README.md` | 已提交并推送 |

## 三、验收摘要（实测，非声称）

1. **单摆周期公式交叉校验**：摆长 200 px、阻尼 0 时，HUD 实测周期 —— 地球（g=9.8）2.84 s、木星（g=24.79）1.78 s、月球（g=1.62）6.97 s，与 `T = 2π√(L/g)` 量级一致。
2. **天体预设切换**：点击 4 枚胶囊，重力在 700 ms 内平滑补间到目标值，滑块与数值标签同步跟随；`aria-pressed` 状态正确迁移。
3. **失重边界**：选「太空」后 g=0，周期显示 `∞（失重·无恢复力）`，不出现 `NaN`。
4. **持久化**：改动参数后 400 ms 自动写入 `localStorage`（键 `fmu.week05.pendulum`）；刷新页面参数完整恢复；篡改存储为非法值时被 `clamp()` 夹回合法区间。
5. **任务四报错复现**：`03_buggy_practice` 点击重置按钮，控制台输出 `Uncaught ReferenceError: resetAnimation is not defined`；`04_fixed_solution` 同操作 0 报错。

## 四、人机协同三反思

正文见仓库根目录 `README.md` 的「人机协同个人复盘（王梦芸 本人撰写）」一节，涵盖：

- 一、意图清晰度反思 —— 把「做一个漂亮的物理动画」拆成可验证的字面约束；
- 二、闭环控制反思 —— ReAct 轮次、验证手段与一次误判的纠正过程；
- 三、主体地位确认（HOTL）—— 哪些决策由本人拍板，哪些交给 AI 执行。

## 五、打包与提交规范

- 提交包命名：`week05_Lab_7903126018_王梦芸.zip`
- 包内含 `.git/`，可用 `git -C <解压目录> log --oneline` 验证提交历史（≥3 条清晰 Commit + 4 个 `weekXX-*-baseline` 标签）。
- 远端同步：`git push` 已完成，可用 `git rev-list --count origin/main..HEAD` 验证为 `0`。
- 忽略规则见同目录 `.gitignore`。

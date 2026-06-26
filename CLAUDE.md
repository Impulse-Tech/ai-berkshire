# AI Berkshire — 项目指令

## 项目概述

基于 Claude Code 的价值投资研究 Skill 合集。四大师框架：巴菲特、芒格、段永平、李录。
GitHub: xbtlin/ai-berkshire

## 项目结构

```
~/Development/ai-berkshire/          — 源代码（本地克隆，不存报告）
  skills/          — 投研 Skill 定义（.md），复制到 ~/.claude/commands/ 使用
  tools/           — 辅助工具（financial_rigor.py 精确计算）
  assets/          — 图片等静态资源

~/Dropbox/ai/shared/ai-berkshire-runtime/   — 运行时（报告输出，Dropbox同步）
  reports/         — 所有投研报告输出（Tab键可补全，不含纯中文路径）
```

## 报告目录结构

**报告存放路径：`~/Dropbox/ai/shared/ai-berkshire-runtime/reports/`**（不是源码目录）

公司文件夹命名：**`{股票代码}{公司名}`**（代码前缀，Tab可补全，ls按代码排序）

```
ai-berkshire-runtime/reports/
├── 000725京东方/            — A股: 6位代码前缀
│   ├── 000725-research-20260626.md
│   └── 000725-investment-team-report-20260626.md
├── 600519贵州茅台/
├── 700腾讯/                 — 港股: 不补零
├── AI产业研究/              — 行业/主题研究（无代码，用行业名）
│   ├── AI五层蛋糕-产业全景研究-20260605.md
│   └── AI五层蛋糕-公众号-20260605.md
├── 核电-industry-20260409.md — 行业报告放根目录
├── AI算力-funnel-20260509.md  — 漏斗筛选报告放根目录
├── AI-轮动判断-20260509.md    — 主题级综合判断报告放根目录
└── portfolio-latest.md       — 组合报告放根目录
```

## 报告命名规范

| Skill | 文件命名格式 | 示例 |
|------|---------|------|
| /investment-team | `{code}-investment-team-report-{YYYYMMDD}.md` | `000725-investment-team-report-20260626.md` |
| /investment-research | `{code}-research-{YYYYMMDD}.md` | `000725-research-20260626.md` |
| /investment-checklist | `{code}-checklist-{YYYYMMDD}.md` | `000725-checklist-20260626.md` |
| /industry-research | `{行业名}-industry-{YYYYMMDD}.md`（根目录） | `核电-industry-20260409.md` |
| /industry-funnel | `{行业名}-funnel-{YYYYMMDD}.md`（根目录） | `AI算力-funnel-20260509.md` |
| /private-company-research | `{公司名}-private-{YYYYMMDD}.md` | `字节跳动/字节跳动-private-20260408.md` |
| /earnings-review | `{code}-earnings-{期间}.md` | `000725-earnings-2025Q4.md` |
| /earnings-team | `{code}-earnings-team-{期间}.md` | `000725-earnings-team-2025Q4.md` |
| /thesis-tracker | `{code}-thesis.md`（长期维护） | `000725-thesis.md` |
| /portfolio-review | `portfolio-latest.md`（根目录，持续更新） | `portfolio-latest.md` |
| /management-deep-dive | `{code}-management-{YYYYMMDD}.md` | `000725-management-20260626.md` |

## /investment-team 文件结构

```
ai-berkshire-runtime/reports/{code}{公司名}/
├── {code}-investment-team-report-{YYYYMMDD}.md   — Team Lead 综合报告（主文件）
├── {code}-research-{YYYYMMDD}.md                 — investment-research 单公司深度（可选）
└── ... 其他同公司报告
```

## 投研分析核心原则（最高优先级）

- **客观、客观、客观**——所有投研分析必须基于事实和数据，严禁主观臆断
- 严格区分"事实"与"观点"：事实用数据支撑，观点必须明确标注为"观点"或"推测"
- **不预设立场**：不预设看多或看空，先摆数据、再推逻辑、最后得结论。结论必须从数据中自然推出
- 禁止使用"我认为"、"我觉得"、"显然"等主观表述，改用"数据显示"、"证据表明"、"根据XX来源"
- **呈现正反两面**：每个核心判断都必须附带反面论据（"但另一方面..."），让读者自己权衡
- 对不确定的事情诚实说"不确定"或"数据不足"，不要用推测填充确定性
- 所有skill（investment-team、investment-research、earnings-review等）在执行时都必须遵守以上原则

## 报告语言与风格

- 所有报告使用**中文**
- 风格：直接、犀利、不说废话
- 数据必须标注来源，关键数据至少2个来源交叉验证
- 估计值必须注明"估计"
- 评分使用★符号（★1-5），不含半星
- 穿插巴菲特/芒格/段永平/李录的语录点评

## GitHub 操作

- 本地克隆路径：`~/Development/ai-berkshire/`
- 运行时路径：`~/Dropbox/ai/shared/ai-berkshire-runtime/`（报告在此，不在源码目录）
- 远程仓库：`https://github.com/xbtlin/ai-berkshire.git`
- 推送前先 `git pull --rebase origin main`（远程经常有新提交）
- commit message 用中文，描述清楚改了什么
- 不要推送中间过程文件（如 data_collection.md），只推最终报告

## 常用命令

```bash
# 工具路径
cd ~/Development/ai-berkshire/tools

# 报告路径
ls ~/Dropbox/ai/shared/ai-berkshire-runtime/reports/

# 推送 skill/tool 改动到 GitHub
cd ~/Development/ai-berkshire
git add skills/xxx.md tools/xxx.py
git commit -m "添加xxx"
git pull --rebase origin main
git push origin main
```

## 注意事项

- 市值必须手算校验：股价 × 总股本，与报告市值对比
- 货币单位要明确（港币/人民币/美元），防止混淆
- PE/ROE等指标用 tools/financial_rigor.py 精确计算
- 报告写完后主动询问是否推送到GitHub

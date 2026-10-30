# Apple Silicon Ladder · M1 → M6 笔记本芯片天梯

这是一个单文件网页，把 MacBook Air / Pro 搭载过的 Apple M 系列芯片（M1 到 M6，每个 CPU / GPU 核数组合单独算一档）按 **Geekbench 6** 成绩排成天梯。

每颗芯片同时显示 **单核、多核、GPU（Metal）** 三条进度条。可以选按哪一项排序，也可以把任意芯片设为基准（= 100），其余芯片按比例换算。

## 功能

- **三项同屏**：每行同时显示单核、多核、GPU 三条进度条。用来排序的那一项会高亮。
- **排序切换**：可按单核、多核或 GPU 排序。同分的配置名次并列。
- **设置基准**：点击每行最左侧的「设基准」，该芯片三项都变为 100，其余芯片按比例换算。默认基准是 **M1（8 核 CPU / 7 核 GPU）**。
  - 进度条上的黄色竖线标出基准芯片的位置。
  - 选过的基准会存在浏览器本地（localStorage），下次打开还在。
  - 点右上角「恢复 M1」可以改回默认。
- **筛选**：可按世代（M1–M6）和档位（基础款 / Pro / Max）筛选。
- **标注推算值**：样本少或推算得出的分数前面标 `≈`。
- **发售年份**：每行机型后面标注发售年份。同一配置用在不同年份的机型上时（如 M3 的 Air 与 Pro 14），按机型分别标注。

## 收录范围

共 32 档配置，只收录笔记本：

| 世代 | 配置 |
|---|---|
| M1 | M1 8/7、8/8 · M1 Pro 8/14、10/14、10/16 · M1 Max 10/24、10/32 |
| M2 | M2 8/8、8/10 · M2 Pro 10/16、12/19 · M2 Max 12/30、12/38 |
| M3 | M3 8/8、8/10 · M3 Pro 11/14、12/18 · M3 Max 14/30、16/40 |
| M4 | M4 10/8、10/10 · M4 Pro 12/16、14/20 · M4 Max 14/32、16/40 |
| M5 | M5 10/8、10/10 · M5 Pro 15/16、18/20 · M5 Max 18/32、18/40 |
| M6 | M6 12/12 |

（格式为 CPU 核数 / GPU 核数）

## 数据来源与说明

- **CPU 单核 / 多核**：Geekbench 6 笔记本机型平均分，主要来自 [EveryMac](https://everymac.com/mac-benchmarks/index-mac-benchmarks.html) 的汇总。同一配置有多种机身时，取相近值。
- **GPU**：Geekbench 6 Metal 分数，来自 Notebookcheck、MacRumors、gpu-monkey 等的公开测试。样本不足的配置是按同代比例推算的，误差约 ±5%。
- **M6**：14 寸 M6 MacBook Pro 于 2026-11-06 发货，暂时用 M6 Mac mini 的 Geekbench 6 中位数代替。目前没有 M6 Pro / Max，OLED 触屏 MacBook Pro 仍用 M5 Pro / Max。
- **Max 的两个 GPU 档位**：同代 Max 不同 GPU 档位的 CPU 核数相同，所以 CPU 分数一致。
- **Air 与 Pro**：Air 没有风扇。Geekbench 是短时测试，分数与 Pro 接近，但长时间满载时 Air 会降频。
- **不要与 Geekbench 7 混比**：Geekbench 7 已于 2026 年 7 月发布，它的 CPU 分数整体比 Geekbench 6 低，两者不能直接比较。

数据截至 2026 年 10 月。

## 使用

不需要构建，也没有依赖：

```bash
git clone https://github.com/muinocriz/apple-silicon-ladder.git
open apple-silicon-ladder/index.html
```

也可以开启 GitHub Pages（Settings → Pages → Deploy from branch → `main` / root），直接在线访问。

## 更新数据

数据在 `index.html` 的 `D` 数组中，每行格式如下：

```js
["芯片名", 世代, "base|Pro|Max", CPU核, GPU核, "机型 · 发售年份", 单核, 多核, Metal, "估算标记"]
// 估算标记：s = 单核为推算值，m = 多核为推算值，g = GPU 为推算值，可以组合使用，如 "smg"
```

## License

MIT

---

# Apple Silicon Ladder · M1 → M6 Laptop Chip Ranking (English)

A single-file web page that ranks every Apple M-series chip configuration shipped in a **MacBook Air or MacBook Pro**, from M1 to M6, by **Geekbench 6** score. Each CPU / GPU core-count combination is its own entry.

Every chip shows **single-core, multi-core, and GPU (Metal)** bars side by side. You choose which metric to sort by, and you can set any chip as the baseline (= 100) so all other chips are rescaled relative to it.

## Features

- **All three metrics at once**: each row shows single-core, multi-core and GPU bars. The metric used for sorting is highlighted.
- **Sort switch**: sort by single-core, multi-core or GPU. Configurations with equal scores share a rank.
- **Set baseline**: click "设基准" (Set baseline) at the left of any row. That chip's three scores become 100 and every other chip is rescaled. The default baseline is **M1 (8-core CPU / 7-core GPU)**.
  - A yellow vertical line on each bar marks the baseline chip's position.
  - The chosen baseline is saved in your browser (localStorage) and restored next time.
  - "恢复 M1" (Reset to M1) in the top-right corner restores the default.
- **Filters**: filter by generation (M1–M6) and tier (base / Pro / Max).
- **Estimates flagged**: scores with few samples or derived by estimation are prefixed with `≈`.
- **Release year**: each row shows the release year after the model names. When one configuration shipped in models from different years (e.g. M3 in the Air and the 14" Pro), the year is shown per model.

## Coverage

32 configurations, laptops only:

| Generation | Configurations |
|---|---|
| M1 | M1 8/7, 8/8 · M1 Pro 8/14, 10/14, 10/16 · M1 Max 10/24, 10/32 |
| M2 | M2 8/8, 8/10 · M2 Pro 10/16, 12/19 · M2 Max 12/30, 12/38 |
| M3 | M3 8/8, 8/10 · M3 Pro 11/14, 12/18 · M3 Max 14/30, 16/40 |
| M4 | M4 10/8, 10/10 · M4 Pro 12/16, 14/20 · M4 Max 14/32, 16/40 |
| M5 | M5 10/8, 10/10 · M5 Pro 15/16, 18/20 · M5 Max 18/32, 18/40 |
| M6 | M6 12/12 |

(Format: CPU cores / GPU cores)

## Data sources and notes

- **CPU single / multi-core**: Geekbench 6 averages for laptop models, mainly from [EveryMac](https://everymac.com/mac-benchmarks/index-mac-benchmarks.html). Where a configuration ships in several chassis, a representative value is used.
- **GPU**: Geekbench 6 Metal scores from public tests by Notebookcheck, MacRumors, gpu-monkey and others. Configurations with too few samples are estimated from same-generation ratios (roughly ±5%).
- **M6**: the 14" M6 MacBook Pro ships on 2026-11-06, so the M6 Mac mini's Geekbench 6 median is used for now. There is no M6 Pro / Max yet; the OLED touchscreen MacBook Pro still uses M5 Pro / Max.
- **Max GPU tiers**: within a generation, both Max GPU tiers have the same CPU core count, so their CPU scores are identical.
- **Air vs Pro**: the Air has no fan. Geekbench is a short test, so Air scores are close to the Pro's, but the Air throttles under sustained load.
- **Do not compare with Geekbench 7**: Geekbench 7 was released in July 2026 and its CPU scores are lower overall, so the two versions are not comparable.

Data as of October 2026.

## Usage

No build step and no dependencies:

```bash
git clone https://github.com/muinocriz/apple-silicon-ladder.git
open apple-silicon-ladder/index.html
```

You can also enable GitHub Pages (Settings → Pages → Deploy from branch → `main` / root) to view it online.

## Updating the data

The data lives in the `D` array in `index.html`. Each row has this format:

```js
["chip name", generation, "base|Pro|Max", CPU cores, GPU cores, "models · release year", single-core, multi-core, Metal, "estimate flags"]
// estimate flags: s = single-core estimated, m = multi-core estimated, g = GPU estimated; combinable, e.g. "smg"
```

## License

MIT

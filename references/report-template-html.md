# 审核报告输出规范：单文件 HTML 五色报告（红/橙/绿/黄/紫 + 新生绿）

> 适用于**报价单审核**与**合同审核**。默认交付 `.html` 单文件（自包含，不依赖外链，双击即开）。
> 用户要求纯文本 / 聊天里看时，用同一套结构改写成 Markdown，但**颜色分级必须保留**（用 🔴🟠🟢 前置标记）。

---

## 一、颜色分级（唯一语义，不得混用）

| 颜色 | 语义 | 使用场景 |
|---|---|---|
| 🔴 高危 `#F53F3F` / 浅色 `#FFECE8` | 高危 · **不改不签** | 付款条款缺失、无限增项授权、解释权条款、0 元悬空的高价项、结构红线、定金超限 |
| 🟠 次要橙 `#FF7D00` / 浅色 `#FFF7E8` | 要谈 · 谈完再签 | 备注加价条款、重复计价、口径不清、单价偏低但靠加价补回 |
| 🟢 合理绿 `#00B42A` / 浅色 `#E8FFEA` | 合理 / **你要争取的目标** | 勾稽全对、单价在行情内、写得规范的条目；以及"你应该谈到的付款表、质保、退款条件" |
| 🟡 提醒黄 `#FFFBEB` / 边框 `#F2D57E` / 标题 `#8A6100` | 提醒 · 注意 · 待办 | "这单有水分""三处口径打架""三件事记住了再谈"、谈判话术等一切**非高危的提醒类文字** |
| 🟣 标注紫 `#814EFF` / 浅色 `#F4EEFF` | 唯一推荐做法 | **只给"唯一推荐的付款方式：验一付一"这类强制推荐**，一份报告里出现 ≤2 处 |
| 🔵 主蓝 `#165DFF` | 中性强调 | 章节序号块、话术引用条等结构性装饰，不承担判定语义 |
| 🟩 新生绿 `#9FDB1D` / 浅色 `#F5FFE0` | 已处理 / 已修复 | "已修 / 已删 / 已抵扣"这类**已经改掉**的历史问题，与"合理绿"区分开 |
| 背景 `#f2f3f5` | 画布 | 页面底色；卡片与章节保持纯白 |

**五条铁律**
1. 同一事项只能有一个颜色，不允许"既橙又红"。不确定时按金额敞口 × 不可逆程度定级（见 `quote-review-playbook.md` 定级模型）。
2. 绿色除了"合理"，也承担"目标"语义——**给用户的争取标准（付款表、退款条款、质保年限）一律标绿**，让报告读起来有落点，而不只是一堆问题。
3. **提醒类不占用红色**：凡是"要你知道一下、但不至于不签"的内容，一律走黄色提醒框；红色只留给真正的高危与 pass 红线。
4. **紫色只做"唯一推荐"**：`#814EFF` 是强指令色，一份报告里只能出现在"唯一推荐的付款方式"这类结论性组件上，不可用来做普通装饰或链接。
5. 同一份报告内不要引入色板以外的颜色；需要弱化时调浅色或降透明度，不要换色相。

---

## 二、版式与组件

- 画布：`body` 背景 `#f2f3f5`，`.wrap` `max-width:980px`，`padding:28px 20px 70px`。
- 头部横幅 `.header`：`linear-gradient(135deg,#41295A,#2F0743)`，白字，`position:relative; overflow:hidden`；`.meta` 一行元信息（用 `·` 分隔）；`.verdict` 一句话结论（浅橙底 `#FFF7E8` + 左侧 4px `#FF7D00` 竖条 + 深棕字 `#3A2410`，`strong` 用 `#8A4B00`；放在深紫横幅上以浅底反白，是整页第一眼）。**文字放在 `.hbox` 容器里并 `padding-right:150px`，右侧留给印章。**
- **结论印章 `.seal`（页头右侧，必备）**：直径 116px 圆形，`border:3px double`，倾斜 `rotate(-12deg)`，内层 `box-shadow:inset 0 0 0 5px rgba(...,.18)` 做出双环手感；三行文字：`.s1` 英文判定（PASS / CONDITIONAL PASS / HOLD）、`.s2` 中文四字结论、`.s3` 补充口径（如"条件通过 · 改后签"）。宽度 ≤700px 时改为 `position:static` 居中、去掉右侧留白。
  - 印章是结论的第一眼落点：先让用户看到「能签 / 要谈 / 别签」，再读正文；三行文字固定为 `英文判定 / 中文结论 / 补充口径`。
  - 颜色随判定走：**可以签** → `#8BE28B`（绿）；**可以谈** → `#FFC46B`（琥珀，默认）；**别签** → `#FF7B7B`（红）。
- 指标卡 `.cards`：`repeat(auto-fit,minmax(180px,1fr))`，每卡三段 `.k`（12.5px 灰）/ `.v`（22px 粗）/ `.n`（12px 灰）。卡片按结论着色：`.danger` 红字、`.warn` 橙字。
- 图例 `.legend`：圆角胶囊一行排开，说明五色含义（🔴高危 / 🟠要谈 / 🟢合理 / 🟡提醒 / 🟣唯一推荐）。
- 章节 `section`：白卡、14px 圆角、`24px 28px` 内距；`h2` 带方块序号（28×28、`background:#165DFF`）；`h3` 17px `#1f3a5f`。
- 表格：`th` 底 `#f7f9fb`、1px `#e3e7ec` 细边、`td.c` 居中；首列宽度固定（150~200px）。
- 行内标记 `mark`：`.mk-r` / `.mk-o` / `.mk-g` / `.mk-l`（新生绿·已处理），`padding:2px 6px`、圆角 4px，**浅底 + 1px 同色描边**，串排时不糊成一片。
- 提示块 `.box`：`.r`（高危）/ `.o`（待谈）/ `.y`（**提醒·默认选它**）/ `.g`（合理）四色，内含 `.t` 粗体标题；用来装"单条结论 + 为什么要紧"。橙与黄的区别：橙是"要谈的问题"，黄是"提醒你注意"。
- 话术框 `.say`：`#F5F7FF` 底 + 左侧 3px `#165DFF` 竖条，**必须是可以直接照念的完整句子**。
- **唯一推荐块 `.pay`（必备）**：`<h3 class="pay">唯一推荐的付款方式：验一付一</h3>`，紫字 `#814EFF`、4px 紫左条、浅紫底 `#F4EEFF`。它是全页唯一的紫色块，读者扫一眼就能定位"我该按什么付"。
- 脚注 `.footer`：居中 12.5px，写数据来源与口径。

---

## 三、固定骨架（10 节，可按材料删节但不能改顺序）

1. **付款条款**（含**定金/意向金专段**：比例、退款条件、抵扣方式）— 多数单据最严重问题就在这
2. **数字勾稽**（绿为主，把"零错误"明确表扬；再点出"该算没算"）
3. **0 元项 / 悬空项**（数量有、金额无 → 红）
4. **漏项**（不会因为没写而不花 → 橙）
5. **备注栏加价条款**（小字才是真价格表 → 橙）
6. **免责与解释权条款**（逐句原文 → 红）
7. **单价横向对比**（对标当地行情，绿为主，橙点为口径问题）
8. **材料与型号**（矛盾条款、缺型号 → 红/橙）
9. **落地价推演**（逐层叠加成表，最后一行给区间）
10. **谈判清单**（A 必须写进合同 / B 签字前补齐 / C 材料追问 / D 现场核验）+ **五条 pass 红线**

合同审核时，第 3~8 节替换为：主体与四要素、定金与付款、价款与增项、工期验收保修、单边条款、争议解决（见 `contract-review-playbook.md` 第五节）。

---

## 四、每节写法要求

- **结论先行**：每节第一句话就是判定，不铺垫。
- **先给数字**：能算出金额的一律算（`数量 × 单价`、`比例 × 基数`），不许只写"偏高"。
- **原文引用**：涉及条款、备注、小字，**照抄原句**再评，避免用户以为你在猜。
- **给改法**：每条问题后必须跟"改成这句话 / 要这个数"，否则视为没写完。
- **话术落地**：每节末尾一个 `.say`，一句话，含具体数字与"不接受 X"的边界。
- **标尺式章节导航 `.ruler`（必备）**：页头下方一条吸顶（`position:sticky;top:0`）的横向标尺，白底 95% + `backdrop-filter:blur(10px)`。
  - 结构：`.track`（36px 高）内放 `.axis`（1px 基线）+ `.fill`（2px 进度条）+ 每节一个刻度 `<a>`（`.tk` 交替 9/13px 长短刻度 + `.nm` 节号）。
  - 交互：`.cursor` 是浮在刻度上方的胶囊气泡（`top:-19px`），随当前章节左右滑动，显示该节名称；当前刻度加粗放大并变紫（`#814EFF`），已读刻度用浅紫 `#C0ACFF` / `#8A74C8`，`.fill` 进度条与 `.cursor` 胶囊同为 `#814EFF`，随滚动同步推进。
  - 实现：每个 `section` 加 `id="sN" data-lab="节名"`，`scroll-margin-top:66px`；一段 30 行内的 JS 在 `scroll`（passive）里取"最后一个 offsetTop ≤ scrollY+96 的 section"，用 `(i+0.5)/n` 百分比同时驱动 `.fill` 宽度与 `.cursor` `left`。
  - 为什么不是胶囊链接列表：标尺能同时表达**位置**与**进度**，读者一眼知道自己在 11 节里的哪一段，还省掉一行占空间的标签。
- **文字层级（重点放大、说明收小）**：h1 27px/800、h2 21.5px、h3 17px、`.box .t` 16.5px、卡片数值 24px、话术 15px；表格正文 14px；**明细解释、口径注释统一用 `.fine`（12.5px、`--sub` 灰）**。原则：一屏里读者先看到的是结论与数字，解释永远比结论小两号。
- **篇幅克制**：每节导语 ≤ 2 行；能用一个数字说清的不写一句形容词；同一事实不重复第二遍（正文说了，表里就别再叙述）。
- **口径注释**：估算面积、估算区间、含不含税，全部在表格下方灰色小字注明。
- **不确定归属的项做成可勾选**：漏项无法判断"该施工方做还是业主自购"时，**不要替用户定性，也不要直接排除**——全部列出，每行前置一个勾选框：`☐ 不勾 = 施工方要做、计入总价`；`☑ 勾上 = 自购 / 第三方 / 已解决、不计入`。表格下方给实时合计（计入 N 项 ¥a～¥b / 已排除 N 项 ¥c～¥d / 全部 ¥e～¥f），并联动第 9 节落地价与指标卡。
  - 实现：`<tr data-min=".." data-max="..">` + `<input type="checkbox" class="leak" [checked]>` + 末尾一段纯 JS（`change` 事件重算，`toLocaleString` 加千分位，勾选行设 `opacity:.42 + line-through`）。
  - 只对**有事实依据**的项预勾选（用户说过自己买的、法定须专营单位做的、已置换的），并在表头注明"已预勾选 N 项，可改"。

---

## 五、多份报价并行审核：一价一报告 + 横向对比

同户型拿到 2～4 家报价时，**不要合成一份大报告**（每家问题混在一起，读者分不清该跟谁谈），按下面做：

1. **一份报价一份 HTML**，文件名 `装修报价审核报告_<报价方>.html`；每份都用本规范的完整骨架（8～11 节）。
2. 每份的**第 7 节（落地价）末尾**，放同一张「三家横向对比」表（列：报价方 / 面价 / 水电 / 落地价 / 一句话定性），并标注"（本单）"。
3. 横向对比只放**可比的四个数**：面价、折后价（若有）、水电是否计价、落地价区间。**不要横向比"单价"**——各家包含项不同，比如"158 元/㎡ 含砖"和"90 元/㎡ 不含砖"直接比会误导。
4. 统一口径：同一套房的地址、面积、客户名必须一致；发现不一致（如 A 家写 14-1-1102、B 家写 13-1-402），**先向用户确认是不是同一套**，确认后在报告里注明"表内误写"。
5. 结论口径：三家落地价通常相差不到 1～1.5 万，**差异不在总价，在"谁把话说清"**——指明"最值得谈的一家"与"退路一家"，不要让用户自己猜。
6. 每份的 `FACE`（面价）常量各自取本单面价，`BASE_MIN/BASE_MAX` 取本单"必付底价"，保证勾选联动只在本单内生效。

---

## 六、最小可用模板

```html
<!DOCTYPE html><html lang="zh-CN"><head><meta charset="UTF-8">
<meta name="viewport" content="width=device-width,initial-scale=1.0">
<title>报告标题</title>
<style>
:root{--red:#FFECE8;--red-b:#F53F3F;--red-bg:#FFECE8;
--orange:#FFF7E8;--orange-b:#FF7D00;--orange-bg:#FFF7E8;
--green:#E8FFEA;--green-b:#00B42A;--green-bg:#E8FFEA;
--blue:#165DFF;--purple:#814EFF;--lime:#9FDB1D;
--ink:#1f2328;--sub:#5b6470;--line:#e3e7ec;--soft:#f7f9fb}
*{box-sizing:border-box}
body{margin:0;background:#f2f3f5;color:var(--ink);line-height:1.75;font-size:15px;
font-family:-apple-system,BlinkMacSystemFont,"PingFang SC","Microsoft YaHei",sans-serif}
.wrap{max-width:980px;margin:0 auto;padding:28px 20px 70px}
.header{position:relative;overflow:hidden;background:linear-gradient(135deg,#41295A,#2F0743);color:#fff;border-radius:14px;padding:28px 30px;margin-bottom:22px}
.header .hbox{padding-right:150px}
.header .meta{font-size:13.5px;opacity:.9;margin-top:8px}
.header .verdict{margin-top:16px;background:#FFF7E8;color:#3A2410;border-left:4px solid #FF7D00;padding:12px 16px;border-radius:6px}
.header .verdict strong{color:#8A4B00}
.seal{position:absolute;right:28px;top:26px;width:116px;height:116px;border-radius:50%;
border:3px double rgba(255,196,107,.95);color:#FFC46B;display:flex;flex-direction:column;
align-items:center;justify-content:center;transform:rotate(-12deg);
box-shadow:inset 0 0 0 5px rgba(255,196,107,.18),0 4px 14px rgba(0,0,0,.18);text-align:center}
.seal .s1{font-size:11px;letter-spacing:3px;font-weight:600}
.seal .s2{font-size:23px;font-weight:800;line-height:1.1;letter-spacing:2px;margin-top:2px}
.seal .s3{font-size:9.5px;letter-spacing:1px;opacity:.8;margin-top:3px}
@media(max-width:700px){.header .hbox{padding-right:0}.seal{position:static;margin:14px auto 0;transform:rotate(-6deg)}}
.cards{display:grid;grid-template-columns:repeat(auto-fit,minmax(180px,1fr));gap:12px;margin-bottom:22px}
.card{background:#fff;border:1px solid var(--line);border-radius:12px;padding:16px 18px}
.card .k{font-size:12.5px;color:var(--sub)}.card .v{font-size:22px;font-weight:700}
.card .n{font-size:12px;color:var(--sub)}
.card.danger .v{color:var(--red-b)}.card.warn .v{color:var(--orange-b)}
section{background:#fff;border:1px solid var(--line);border-radius:14px;padding:24px 28px;margin-bottom:18px}
h2{font-size:19px;margin:0 0 6px;padding-bottom:10px;border-bottom:2px solid var(--line)}
h2 .num{display:inline-block;background:var(--blue);color:#fff;width:26px;height:26px;line-height:26px;text-align:center;border-radius:6px;font-size:14px;margin-right:8px}
h3{font-size:16px;margin:22px 0 8px;color:#1f3a5f}
table{width:100%;border-collapse:collapse;margin:12px 0;font-size:14px}
th{background:var(--soft);text-align:left;padding:9px 11px;border:1px solid var(--line);font-weight:600}
td{padding:9px 11px;border:1px solid var(--line);vertical-align:top}td.c{text-align:center}
mark{padding:2px 6px;border-radius:4px;display:inline-block;font-size:13.5px}
.mk-r{background:var(--red);color:#7f1d1d;border:1px solid #F53F3F}
.mk-o{background:var(--orange);color:#7c3a00;border:1px solid #FF7D00}
.mk-g{background:var(--green);color:#14532d;border:1px solid #00B42A}
.mk-l{background:#F5FFE0;color:#5A8A00;border:1px solid #9FDB1D}
.box{border-radius:10px;padding:14px 18px;margin:14px 0;border:1px solid}
.box.r{background:var(--red-bg);border-color:#F53F3F}
.box.o{background:var(--orange-bg);border-color:#FF7D00}
.box.y{background:#FFFBEB;border-color:#F2D57E}
.box.y .t{color:#8A6100}
.box.g{background:var(--green-bg);border-color:#00B42A}
.box .t{font-weight:700;margin-bottom:6px}
.say{background:#F5F7FF;border-left:3px solid var(--blue);padding:12px 16px;margin:10px 0;border-radius:0 8px 8px 0;font-size:14px}
.pay{color:var(--purple);font-weight:800;border-left:4px solid var(--purple);background:#F4EEFF;padding:7px 12px;border-radius:6px;margin:18px 0 8px}
.footer{text-align:center;color:var(--sub);font-size:12.5px;padding:20px 0}
</style></head><body><div class="wrap">

<div class="header">
  <div class="seal"><span class="s1">PASS</span><span class="s2">可以谈</span><span class="s3">条件通过 · 改后签</span></div>
  <div class="hbox">
    <h1>报告标题</h1>
    <div class="meta">单据 · 地址 · 客户 · 面积 · 城市</div>
    <div class="verdict"><strong>一句话结论：面价 X，落地 Y，现在能不能签。</strong></div>
  </div>
</div>

<div class="cards">
  <div class="card"><div class="k">面价</div><div class="v">¥X</div><div class="n">构成</div></div>
  <div class="card danger"><div class="k">付款条款</div><div class="v">无</div><div class="n">红线</div></div>
</div>

<section><h2><span class="num">1</span>标题</h2>
  <div class="box r"><div class="t">🔴 结论</div>理由 + 处置</div>
  <div class="say">"可以直接照念的一句话。"</div>
</section>

<div class="footer">数据来源 · 口径说明</div>
</div></body></html>
```

---

## 七、交付与自检

1. 文件名：`<单据名>审核报告.html`，放在用户项目目录，不放进临时目录。
2. 写完自检：标签闭合（可用解析器跑一遍）、无残留占位符、表格行数与数据一致、每个 🔴 项都有"改法"。
3. 交付方式：以文件形式呈现并给出绝对路径；用户要在聊天里直接看，则同步输出 Markdown 摘要（保留五色标记 🔴🟠🟢🟡🟣）。
4. 报告不等于合同：页脚必须写明"本报告不构成法律意见 / 价格为参考区间"。

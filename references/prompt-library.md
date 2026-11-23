# 效果图提示词库（通用版）

> **本库与户型、风格无关。** 全部模板均为变量化结构，按「五部分公式 + 五层摄影架构」拼装，任何城市/面积/风格通用。
> 配色取自 `references/style-palettes.md`，工具参数取自 `references/tool-workflow.md`。

---

## 一、五部分提示词公式（核心）

```
[空间 Subject] + [风格 Style] + [材质 Materials] + [灯光 Lighting] + [相机 Camera] + [负面 Negative] + [参数 Params]
```

每一部分写什么、怎么写：

| 部分 | 必写要素 | 写法要点 | 反例（别这么写） |
|------|----------|----------|------------------|
| ① 空间 | 空间类型 + 面积㎡ + 长×宽 + 层高 + 家具布局 + 用途 | **数字必须保留**，这是比例的锚 | "一个客厅"（AI 会编尺寸） |
| ② 风格 | 风格名 + 关键造型特征（线条/顶面/柜门形式） | 一个风格 + 2-3 个造型特征即可，堆砌词会互相打架 | "现代简约北欧侘寂新中式"（四不像） |
| ③ 材质 | 按 70-20-10 落到**具体材料**：墙/地/柜/台面/五金/软装 | 写材料名不写形容词（写 `oak veneer` 不写 `high-end wood`） | "高端材料""有质感"（AI 听不懂） |
| ④ 灯光 | 自然光（朝向+时段）+ 人工光（色温+层次：主/辅/氛围） | 只留一个主光向；色温统一 | "明亮温馨有氛围"（无信息量） |
| ⑤ 相机 | 镜头焦段 + 光圈 + 视角 + 构图 + 画质 | 用摄影参数，不用渲染词 | `octane render, 3D, CG, unreal engine` |

### 五层摄影架构（提升写实度、消除塑料感）

```
L1 媒介声明：photorealistic interior photography, shot on Canon EOS R5, architectural digest feature
L2 空间本体：a {面积} {空间类型}, {长}×{宽}m, {层高}m ceiling, {布局与动线}
L3 材质色彩：{基底色材质} walls, {地面材质} flooring, {柜体材质} cabinetry, {五金}, {软装点缀色 ≤10%}
L4 光学系统：{朝向} {时段} daylight through {窗型}, layered {色温} artificial lighting, soft shadows
L5 相机后处理：{焦段} lens, f/8, deep depth of field, eye-level view, 8K, natural color grading
```

**关键：** L1 声明"实拍"、L5 用真实镜头参数，是让模型输出照片质感而非 CG 质感的核心。

---

## 二、通用可变模板（复制后填 `{}`）

### 中文版（即梦 / 通义万相 / 文心一格 / 混元 / 内置工具）

```
{风格名}风格住宅室内实景摄影，{空间类型}，面积约 {X} 平方米（{长}米 × {宽}米），层高 {层高} 米。
墙面为{基底色+材质}，地面{地面材质}，定制柜体{柜体材质+门板形式}，五金与灯具为{五金色}哑光。
软装点缀色{点缀色}占比不超过 10%，仅用于抱枕/挂画/花器。
家具布局：{主家具与位置}，过道留出 {0.9} 米通行宽度，人体尺度真实。
采光：{朝向}向{时段}自然光从{窗型}射入，人工光为 {色温} 分层照明（主灯+射灯+灯带），柔和阴影。
空间用途：{用途}，有适度生活痕迹（书籍、绿植、织物）。
镜头：{焦段} 广角，人眼高度平视，f/8 大景深，构图完整不裁切家具，8K 超高清，室内设计杂志质感，真实材料反射与光影。
负面：无欧式雕花，无{跑偏风格}元素，无杂乱堆物，无跳色墙面，无扭曲家具比例，无文字，无水印，无logo，无人物。
```

### 英文版（Midjourney / SD / Flux / DALL·E）

```
photorealistic interior photography of a {style} {room type}, {X} sqm ({L}m × {W}m), {H}m ceiling;
{base color+material} walls, {flooring} floor, {cabinet material+door style} cabinetry, {hardware finish} hardware;
{accent color} accents in soft furnishings only (<10%);
layout: {key furniture and positions}, human-scale furniture, {0.9}m walkway;
{s orientation} {time of day} daylight through {window type}, layered {color temp} artificial lighting, soft natural shadows;
{lived-in detail: books, plants, textiles};
shot on {focal length} lens, eye-level, f/8, deep depth of field, full composition, 8K, architectural digest, realistic material reflections
--no ornate moulding, {wrong style}, clutter, colorful walls, distorted proportions, text, watermark, logo, people --ar {ratio} --style raw --s 75
```

---

## 三、词汇表（按需取用，不要全堆）

### 风格 Style

| 中文 | 英文 |
|------|------|
| 现代极简 | modern minimalist, clean straight lines, handleless flat panels |
| 奶油风 | cream style, soft rounded forms, warm off-white |
| 原木日式 | Japanese wabi-sabi, natural oak, low furniture |
| 轻奢 | modern luxe, brushed brass, marble veining |
| 法式 | French classic, herringbone parquet, wall moulding |
| 新中式 | modern Chinese, ink-wash accent, dark walnut |
| 侘寂 | wabi-sabi, limewash plaster, earthy texture |
| 中古复古 | mid-century modern, teak wood, tapered legs |
| 工业风 | industrial loft, exposed concrete, black steel |
| 南洋复古 | tropical colonial, rattan, tropical prints |
| 意式极简 | Italian minimalism, large-format stone, hidden handles |

### 材质 Materials

| 类别 | 中文 | 英文 |
|------|------|------|
| 墙面 | 乳胶漆/艺术漆/微水泥/木饰面/护墙板 | matte emulsion / limewash paint / microcement / wood veneer / wall paneling |
| 地面 | 哑光大板砖/实木地板/复合地板/水磨石 | matte large-format porcelain tile / solid oak flooring / laminate / terrazzo |
| 柜体 | 双饰面板/ PET 肤感/ 烤漆/ 实木贴皮 | melamine board / PET matte finish / lacquered / wood veneer |
| 台面 | 石英石/岩板/不锈钢/实木 | quartz / sintered stone / stainless steel / solid wood |
| 五金 | 哑光黑/拉丝金/枪灰/铬色 | matte black / brushed brass / gunmetal grey / chrome |
| 软装 | 棉麻/羊毛/丝绒/藤编/真皮 | linen / wool / velvet / rattan / full-grain leather |

### 灯光 Lighting

| 中文 | 英文 |
|------|------|
| 南向午后自然光 | south-facing afternoon daylight |
| 清晨柔光 / 黄昏暖光 / 阴天漫射光 | soft morning light / warm dusk light / overcast diffused light |
| 3000K 暖光 / 4000K 中性光 | warm 3000K / neutral 4000K |
| 分层照明（主灯+射灯+灯带） | layered lighting: ambient + recessed spots + LED cove strip |
| 窗帘盒隐藏灯带 / 柜体感应灯 | hidden cove lighting in curtain box / under-cabinet sensor light |
| 柔和阴影，无过曝 | soft natural shadows, no blown highlights |

### 相机 Camera

| 中文 | 英文 |
|------|------|
| 24mm 广角，人眼高度平视 | 24mm wide-angle, eye-level view |
| 16mm 超广（小空间）/ 35mm（减少畸变） | 16mm ultra-wide (small rooms) / 35mm (minimal distortion) |
| f/8 大景深，前后都清晰 | f/8, deep depth of field |
| 移轴镜头（修正竖线） | tilt-shift lens, vertical lines corrected |
| 一点透视 / 两点透视（角落视角） | one-point perspective / two-point corner view |
| 8K，真实色彩，无滤镜感 | 8K, true-to-life color grading, no HDR oversaturation |

---

## 四、分空间模板（风格中立，填入风格色板即可）

> 用法：`[通用模板] + [本节空间段]`。每个模板只描述**布局与陈设逻辑**，不绑定任何配色。

### 客餐厅（含一体化横厅）

```
{X}㎡ 客餐厅一体化横厅（{长}×{宽}m），无隔断，{沙发区→餐桌区→过道} 动线；
沙发区：{主沙发} 靠 {长边/短边} 墙，配 {茶几} 与 {地毯}，电视墙 {电视柜/收纳柜} 形式，{灯位}；
餐厅区：{餐桌尺寸与材质} 配 {椅数} 把椅，上方 {吊灯形式}，侧边 {餐边柜/冰箱}；
过道预留 ≥0.9m 通行宽度；顶面 {吊顶形式+灯位}；{阳台/窗} 提供主采光。
```

### 卧室（主卧 / 次卧 / 儿童房）

```
{X}㎡ {主卧/次卧/儿童房}（{长}×{宽}m），{床宽} 米床 {居中/靠墙}，床头背景墙 {处理方式}；
收纳：{通顶衣柜/斗柜} 位于 {墙位}，{开放格+灯带}；窗侧 {窗帘形式+窗帘盒}；
{书桌/梳妆台/阅读角} 位于 {位置}；夜间氛围：{床头灯+灯带+色温}。
```

### 厨房

```
{X}㎡ {一字/L型/U型} 厨房，操作动线 取→洗→切→炒 连贯；
吊柜 {颜色材质}，地柜 {颜色材质}，台面 {材质}，{台下盆/大单槽} + {龙头形式}；
烟机灶具 {形式}，{冰箱位}，吊柜底 {感应灯带}；墙地砖 {规格+美缝}；{玻璃移门/开放式}。
```

### 卫生间

```
{X}㎡ 卫生间，干湿分离：{淋浴房形式与尺寸} + {浴室柜+智能镜} + {马桶形式}；
墙地砖 {颜色+规格+防滑}，顶面 {集成吊顶+浴霸}；五金 {花洒/龙头/置物架 统一色}；
收纳：{壁龛/镜柜/置物架}；镜前灯 {色温与形式}。
```

### 玄关 / 鞋柜区

```
{X}m 长玄关，鞋柜沿 {长墙/短墙} 布置，{通顶/半高} 柜，{底部悬空 20cm+感应灯带}，
{中部置物台 + 插座}，{换鞋凳/挂衣区}，{强弱电箱隐藏处理方式}，地面 {材质}，进深 {35-40cm}。
```

### 书房 / 多功能房

```
{X}㎡ {书房/电竞房/客房}，{书桌+椅} 靠 {窗/墙}，{书架/收纳柜} 形式，{灯带+射灯}；
{沙发床/折叠床} 兼顾客房功能；{显示器/设备} 理线整洁，无外露明线。
```

### 阳台

```
{X}㎡ {生活阳台/休闲阳台}，{洗衣柜+烘干机/洗衣机} 或 {休闲椅+绿植}；
{断桥铝窗+纱窗}，地面 {防滑砖/木地板}，顶面 {晾衣机/吊顶}，{收纳柜}。
```

---

## 五、负面提示词库

### 通用基线（每张图都带）

中文：`无欧式雕花，无浮夸装饰，无杂乱堆物，无比例失真，无扭曲几何，无多余门窗，无文字，无水印，无 logo，无人物，无过曝，无 HDR 过度饱和`

英文：`--no ornate moulding, excessive decoration, clutter, distorted proportions, warped geometry, extra doors or windows, text, watermark, logo, people, blown highlights, HDR oversaturation`

### 按症状追加

| 症状 | 追加负面词（英文） | 追加负面词（中文） |
|------|--------------------|--------------------|
| 风格跑偏成欧式/美式 | `--no classic European, baroque, rustic farmhouse` | 无欧式古典、无巴洛克、无美式乡村 |
| 点缀色上墙上柜 | `--no {accent} walls, no {accent} cabinets` | 无{点缀色}墙面、无{点缀色}柜体 |
| 家具比例失真 | `--no oversized furniture, no tiny furniture` | 无过大/过小家具，家具人体尺度真实 |
| 出现文字水印 | `--no text, no watermark, no signature` | 无文字、无水印、无签名 |
| 空间压抑 | `--no low ceiling, no heavy dark ceiling` | 无低矮压抑感，层高 {H} 米 |
| 塑料/CG 感 | `--no 3D render look, no plastic surfaces, no CGI` | 无 3D 渲染感、无塑料材质、无 CG 质感 |
| 空荡如样板间 | `--no empty sterile showroom`（正面加 `lived-in`） | 无空荡样板间感（正面加"有生活痕迹"） |

---

## 六、参数速查

| 平台 | 画幅建议 | 关键参数 | 备注 |
|------|----------|----------|------|
| Midjourney | 客餐厅 `--ar 16:9`；卧室/厨卫 `--ar 4:3`；竖版 `--ar 3:4` | `--style raw --s 50-150 --v 7` | `--s` 越高越艺术化、离题风险越大；写实取 50-100 |
| 即梦 / 通义万相 / 文心 | 横图 16:9，竖图 3:4 | 选"写实/摄影"模型，精绘开高 | 中文提示词直读，免费额度够批量对比 |
| Stable Diffusion / Flux | 按参考图定尺寸（768-1024 起步，再放大） | ControlNet（见 references/tool-workflow.md） | 唯一能保证户型结构一致的路线 |
| 内置生图工具 | 1024×1536 / 1536×1024 | 图生图传参考图 | 先小图抽卡，选中再精修 |

---

## 七、避坑清单

1. **删掉㎡/米数 → 比例必崩。** 数字是 AI 判断空间尺度的唯一依据。
2. **多风格词堆砌 → 四不像。** 一个风格 + 2-3 个造型特征。
3. **写"高端/奢华/有质感" → 无效果。** 必须写具体材料名。
4. **用渲染引擎词 → 塑料感。** 用相机参数替代。
5. **多空间合一 → 全变形。** 一次一个空间。
6. **点缀色不给占比 → 跳色上墙。** 写死 `≤10%，仅软装`。
7. **光源方向自相矛盾 → 假。** 只留一个主光向。
8. **不写生活痕迹 → 样板间。** 加书籍、绿植、织物、杯具。
9. **参考图质量差 → 图生图贴不住。** CAD 用 4x 渲染，照片选光线充足、正对墙角拍。
10. **一次改多个变量 → 无法定位有效词。** 一轮只调一类问题。

---

## 附录：实战参考案例（仅供参照，禁止套用）

> 以下为单个真实项目的落地成果，**仅用于说明"通用方法填入具体参数后的样子"**，不代表推荐配色/风格。

**项目**：郑州高新区 10#楼，建面 89㎡ 三室两厅，客餐厅 28.8㎡ 南北贯通，西边户有西晒。

**选定色板（现代极简 · 黑白灰深蓝）**

| 角色 | 色值 | 占比 | 落位 |
|------|------|------|------|
| 基底白 | 珍珠白 / 纯白 | ≈60% | 墙、顶 |
| 中性灰 | 深灰 `#3A3D42` / 中灰 `#8A8D91` | ≈25% | 柜体、室内门、窗帘 |
| 重黑 | 哑光黑 `#1A1C1E` | ≈10% | 家电、五金、灯环 |
| 点缀深蓝 | 藏青 `#1F2A44` | ≤5% | 软装、单面卧室背景墙 |

**成套提示词（英文锚点）**

```
photorealistic interior photography of a modern minimalist Chinese apartment, 28.8 sqm open-plan living and dining (7.1m × 3.9m), 2.75m ceiling;
white walls, matte dark-grey (#3A3D42) flat-panel handleless cabinetry and doors, matte black hardware and black-trim recessed spotlights, light-grey matte large-format porcelain floor tiles;
navy blue (#1F2A44) accents in soft furnishings only (<5%);
human-scale furniture, 0.9m walkway, double-layer edge ceiling;
south-facing afternoon daylight through balcony sliding door, layered 3500K lighting;
shot on 24mm tilt-shift, eye-level, f/8, deep depth of field, 8K, architectural digest
--no ornate decoration, European style, wood-heavy rustic, clutter, navy walls except bedroom accent, navy cabinets, text, watermark --ar 16:9 --style raw --s 75
```

**该案例沉淀的经验**（已提炼进正文硬规则）：保留㎡数 / 一次一空间 / 点缀色给占比 / 中英双版 / 负面词必带 / 阴暗面补层高词。

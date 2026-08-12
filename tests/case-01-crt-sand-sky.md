# Case 01 ｜ 老式 CRT 电视 + 沙地草丛 + 蓝天

> 测试图：`assets/case-01-input.jpg`（Picsum 固定 seed `wbimgtest`，尺寸 1000×1250）
> 图源授权：Unsplash License，作者 Pablo GarciaSaldaña —— 详见 `NOTICE-assets.md`
> 测试路径：按 `SKILL.md` Step 0–7 手动走查（模拟一次真实触发）
> 假设 Step 2 最小追问结果：平台 = Midjourney，惊艳方向 = 胶片复古味，用途 = 社媒/个人

---

## Step 0 ｜任务判别
用户给了一张图，要反推提示词 → 走**反推图**主路径。

## Step 1 ｜看图拆维（按 references/reverse-dimensions.md 通用图 7 要素）

```
=== 图像分析块 ===
场景分类：通用图（静物+风景元素）

主体：一台老式 CRT 电视机，棕色/米色木质外壳，屏幕关闭呈深绿色反光
风格：写实摄影，复古/怀旧
色彩：暖米色沙地、浅绿草叶、天蓝、白云、棕/米电视外壳；整体低饱和、偏暖
光影：自然日光、柔和散射光、无明显硬影、阴天感
构图：低角度仰拍，前景草叶虚化，主体偏右下，天空占大部分（负空间大）
质感：CRT 塑料/木质纹理、细长草叶、细腻沙粒、屏幕微弱反光
氛围：孤独、怀旧、超现实、静谧
分辨率：8k, ultra-detailed

镜头焦段：约 35mm
景深：前景草虚化，电视主体清晰，背景天空轻微虚化
色调：暖调、轻微褪色
后期：胶片模拟、轻微颗粒、低对比、柔光

惊艳方向预设：胶片复古味
目标平台：Midjourney
用途：社媒 / 个人

原创性边界检查：
- 是否含真实 logo / 水印？ → 无
- 是否含具名创作者风格冒用？ → 无
- 是否含受保护角色？ → 无
- 是否含真实可识别人物 / 未成年角色？ → 无
```

## Step 3 ｜还原版 Prompt（中英双语）

```
一台老式 CRT 电视机立在沙地与草丛中，低角度拍摄，屏幕关闭呈深绿色反光，棕色木壳，背景是蓝天白云；自然柔和日光，浅景深，前景草叶虚化；暖色调、低饱和、轻微胶片颗粒；怀旧、孤独、静谧氛围；35mm 镜头，f/2.8，8k ultra-detailed。

A vintage CRT television standing in sand and grass, low angle shot, screen off with deep green reflection, brown wooden casing, blue sky with white clouds in background; soft natural daylight, shallow depth of field, blurred grass in foreground; warm tone, low saturation, subtle film grain; nostalgic, lonely, serene mood; 35mm lens, f/2.8, 8k ultra-detailed.
```

## Step 4 ｜惊艳增强版 Prompt（胶片复古味）

```
A vintage CRT television half-buried in golden sand and wispy grass, low angle hero shot, screen off with deep green glass reflection, worn wood-grain casing, vast blue sky with soft cumulus clouds, Kodak Portra 400 film emulation, soft halation around highlights, fine film grain, slightly faded warm colors, 35mm analog look, nostalgic warmth, natural diffused daylight, shallow depth of field with creamy foreground bokeh, dreamy serene mood, 8k, ultra-detailed --ar 4:5 --style raw
```

> 叠加层说明：胶片复古味（Kodak Portra 400 模拟、柔光晕、细颗粒、褪色暖色）叠加在还原版核心身份（老式电视/沙地草丛/蓝天/低角度）之上，未改变原图本质。

## Step 5 ｜3 变体

- **V1 构图 shift**：tight close-up on CRT screen reflecting the blue sky, extreme foreground grass blur, cinematic macro framing
- **V2 光影 shift**：golden hour side light casting long shadows on sand, warm rim light on television casing, late afternoon glow
- **V3 风格 shift**：dreamy ethereal pastel tones, soft glow and atmospheric haze, delicate bokeh light spots, gentle vignette

## Step 6 ｜平台适配版（Midjourney）

```
A vintage CRT television half-buried in golden sand and wispy grass, low angle hero shot, screen off with deep green glass reflection, worn wood-grain casing, vast blue sky with soft cumulus clouds, Kodak Portra 400 film emulation, soft halation around highlights, fine film grain, slightly faded warm colors, 35mm analog look, nostalgic warmth, natural diffused daylight, shallow depth of field with creamy foreground bokeh, dreamy serene mood, 8k, ultra-detailed::1.1 --ar 4:5 --style raw --no people, watermark, text, modern electronics, harsh flash
```

## 负向约束

- 通用：no deformed hands, no extra fingers, no blurry, no watermark, no text overlay, no low quality, no oversaturated, no plastic skin, no distorted anatomy, no jpeg artifacts, no duplicate subject
- 本图专用：no people, no modern electronics, no harsh flash, no oversaturated sky, no visible power cords, no urban clutter

## 原创边界说明

- 图中无真实可识别人物，无需替换。
- 无真实 logo / 水印 / 具名创作者 / 受保护角色。
- CRT 电视机为通用老式电器，不构成抄袭特定品牌。
- 不生成未成年角色；不在图中自动添加水印或文字。

---

## 走查结论

- **流程可跑通**：Step 1 维度表 → Step 3 还原 → Step 4 惊艳 → Step 5 变体 → Step 6 平台版，无断点。
- **参考资料可用**：reverse-dimensions.md 通用图 7 要素覆盖完整；enhancement-vocab.md 的「胶片复古味」词块可直接嵌入；platform-guides.md 的 MJ `--ar`/`--style raw`/`--no` 语法能套入；templates.md 的 A/B/D 模板结构匹配。
- **完整展示**：每段 prompt 均完整呈现，未截断。
- **限制声明**：本走查为按 Skill 规则手动执行，非 WorkBuddy 自动触发调用；真实触发命中率需在运行态再验。

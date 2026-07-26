# 反推 + 增强模板 (Templates)

可复制模板。把 `[括号]` 换成 Step 1 分析块的实际内容。

---

## A. 通用反推模板（还原版）
```
[主体描述], [风格], [色彩], [光影], [构图], [质感], [氛围],
[镜头/分辨率], professional photography --ar [比例]
```

## B. 惊艳增强套用模板（以电影感为例，方向可换）
```
[还原版主体与构图],
shot on 85mm f/1.4 with creamy bokeh,
[惊艳方向词块，见 enhancement-vocab.md],
[负向约束],
[平台参数]
```

---

## C. 10 场景速填模板

### 通用图
- 还原：`[主体], [风格], [色彩], [光影], [构图], [质感], [氛围], 8k`
- 惊艳：+ `[方向词块]` + negative

### 字体 / Logo
- 还原：`[字形] logotype, [质感], [排版], [配色], clean vector, white background`
- 惊艳：+ `premium embossed, studio light, [方向]`

### 风景 / 场景
- 还原：`[前景], [中景], [远景], [时间光线], [氛围], wide angle, deep focus, 8k`
- 惊艳：+ `[方向词块，如 epic fantasy god rays]`

### 摄影 / 人像
- 还原：`portrait of [主体], [光线], [镜头焦段], [景深], [色调], [构图], [后期]`
- 惊艳：+ `[方向词块]` + negative

### 插画 / 二次元
- 还原：`[画风] illustration, [笔触], [色彩], [叙事], key visual`
- 惊艳：+ `[方向词块，如 anime vibrant]`

### 产品 / 电商（强推）
- 还原：`[产品] product shot, [材质反光], [棚拍光], [hero角度], [背景], [比例], 8k`
- 惊艳：+ `hyper-real product, macro, studio sweep`

### 美食（强推）
- 还原：`[食物], [蒸汽光泽], [视角], [暖光], [质感], [摆盘], 8k food photography`
- 惊艳：+ `appetizing glow, cinematic food`

### 建筑 / 室内（强推）
- 还原：`[空间], [线条几何], [光层次], [材质], [纵深], architectural photography`
- 惊艳：+ `[方向词块，如 low-key luxury]`

### 时尚 / 服装（强推）
- 还原：`fashion shot, [穿搭], [面料垂感], [姿势], [棚外景], [造型], studio light`
- 惊艳：+ `editorial commercial, [方向]`

### 汽车（强推）
- 还原：`[车型], [车漆反光], [轮毂], [低角度], [环境], [动感], automotive photography`
- 惊艳：+ `cinematic, reflective highlight, low angle hero`

---

## D. 3 变体模板（基于惊艳版，每次只改一项）
- **V1 构图 shift**：`[改景别/机位，如 wide environmental → tight close-up]`
- **V2 光影 shift**：`[改光，如 backlit → Rembrandt side light]`
- **V3 风格 shift**：`[改方向，如 cinematic → dreamy]`

## E. 变量填空器（可选输出）
把惊艳版写成可换词模板，用户改 `{...}` 即可复用：
```
{SUBJECT}, shot on {LENS}, {LIGHT}, {GRADE}, {MOOD}, {PLATFORM_PARAMS}
```

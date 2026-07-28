# 惊艳增强词库 (Enhancement Vocabulary)

本文件是 Step 4「惊艳增强版」的核心资产。每个方向给一段可直接嵌入提示词的专业词块
（英文为主，便于图像模型识别）。用法：根据 Step 2 选的方向，取对应词块叠加到还原版；
可组合（如"电影感 + 胶片味"）。

---

## 通用增强基底（任何方向都可加）
- 镜头：`shot on 85mm f/1.4, creamy bokeh, shallow depth of field`
- 画质：`8k resolution, ultra-detailed, professional photography`
- 后期：`subtle film grain, fine detail, color graded`

## 1. 电影大片感 (Cinematic)
anamorphic widescreen lens, teal-and-orange color grade, dramatic chiaroscuro lighting,
volumetric haze, shallow depth of field, cinematic composition, blockbuster mood,
subtle lens flare, Rembrandt lighting

## 2. 低调奢华 (Low-key Luxury)
low-key lighting, deep shadows, black background with gold rim light, mysterious mood,
single hard light source, high contrast, luxurious texture, editorial elegance

## 3. 古典油画 (Old Masters)
Caravaggio-style tenebrism, warm earthy palette, canvas texture, soft chiaroscuro,
painterly brushwork feel, classical composition, museum quality

## 4. 胶片复古味 (Film Vintage)
Kodak Portra 400 film emulation, soft halation around highlights, fine film grain,
slightly faded colors, 35mm analog look, nostalgic warmth, Cinestill 800T for night scenes

## 5. 纪实纪录片 (Documentary)
35mm documentary photography, available light, candid moment, desaturated realistic
tones, unretouched authenticity, photojournalism style

## 6. 日系自然光 (Japanese Natural)
soft daylight, airy and light, fuji pro 400h pastel tones, lifestyle candid, clean
minimal, gentle shadow, film-like

## 7. 杂志商业高级 (Editorial Commercial)
clean studio backdrop, soft even light, low saturation, premium material texture,
generous negative space, fashion magazine cover mood, refined retouching

## 8. 梦幻氛围 (Dreamy)
soft glow, bokeh light spots, thin atmospheric haze, pastel tones, ethereal and
airy, dreamlike luminosity, gentle vignette

## 9. 赛博朋克 (Cyberpunk)
neon signs, rain reflections, magenta-cyan contrast, volumetric fog, wet street,
high contrast, futuristic city, glowing rim light

## 10. 国风东方 (Oriental / GuoFeng)
ink wash aesthetic, traditional low-saturation palette, poetic composition, classical
Chinese elements, misty mountains, elegant restraint, rice paper texture

## 11. 动漫二次元 (Anime)
vibrant saturation, cel shading, key visual style, clean lineart, dynamic pose,
anime studio look, glowing eyes

## 12. 蒸汽波 (Vaporwave)
pink-purple gradient, retro 80s grid, glitch elements, neon sunset, nostalgic synthwave,
chrome text

## 13. 超写实产品级 (Hyper-real Product)
macro photography, razor-sharp focus, studio sweep light, reflective highlight,
commercial product shot, 8k detail, clean background, no shadow cast

## 14. 史诗奇幻 (Epic Fantasy)
large scale, god rays, misty atmosphere, UE5 render quality, dramatic sky, heroic
lighting, fantastical environment, volumetric light

---

## 配色控制卡 (Color Control Card)

借鉴分层镜头叙事规范，把"色彩"从一句形容词升级为**可约束的色板**。反推时从原图提取
6–10 个实际核心色，按角色排列，作为还原版与惊艳版的**色彩约束**（尤其服务色彩分级与保真）。

**推荐色角色（按顺序）**
1. 最深阴影 deepest shadow
2. 基础暗部 base shadow
3. 环境主色 environment main color
4. 空气/天气色 air / weather color
5. 主光或轮廓光 key / rim light
6. 地面/材质反射 ground / reflection
7. 主体肤色或主材质色 subject skin / main material
8. 暖色点缀 warm accent
9. 最亮高光 brightest highlight

**用法**
- 在还原版/惊艳版末尾追加：`color palette: #xxxxxx deepest shadow, #xxxxxx environment main, #xxxxxx warm accent, ...`（色值可用近似十六进制或文字描述）。
- 惊艳版的色彩分级（青橙/低饱和/胶片色等）应**在控制卡范围内做偏移**，而非凭空造色，保证与原图同源。

**铁律（负向）**
- 配色条/控制卡**仅用于色彩分级参考**；提示词中必须禁止把色块、条纹、图案或文字色值表加入画面：
  `no color swatches, no palette bars, no color stripes, no text labels in image`

---

## 负向提示词库 (Negative Prompts)

**通用 Universal**
no deformed hands, no extra fingers, no blurry, no watermark, no text overlay,
no low quality, no oversaturated, no plastic skin, no distorted anatomy,
no jpeg artifacts, no duplicate subject

**人像 Portrait**
no bad eyes, no asymmetric face, no double chin, no harsh flash, no acne

**产品 Product**
no reflections of photographer, no dust, no scratches, no fingerprint, no visible seam

**文字类 Text (LOGO/海报)**
no garbled text, no wrong spelling
> 注意：AI 生成文字常错，敏感/准确文案建议后期用设计软件加，提示词只控字形质感。

**风景 Landscape**
no overexposed sky, no blown highlights, no cluttered foreground, no flat light

---

## 组合示例 (Combinations)
- 电影感 + 胶片味：`anamorphic widescreen, teal-orange grade, Kodak Portra 400 emulation, soft halation, fine grain`
- 商业高级 + 低调奢华：`clean studio, low-key, black background gold rim, premium texture, generous negative space`
- 梦幻 + 日系：`soft glow, bokeh spots, airy daylight, fuji pastel, gentle vignette`

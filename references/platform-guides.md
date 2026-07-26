# 平台适配指南 (Platform Guides)

本文件对应 Step 6。把 Step 4 的「惊艳增强版 Prompt」转成目标图像引擎语法。
结构借鉴 `prompt-model-adaptation` 的五步法：**诊断 → 检查表 → 适配 → 回归验证 → 自优化**。

## 五步法在平台适配中的映射
1. **诊断 Diagnose**：识别目标平台语法特征（参数旗标 / 权重符号 / 自然语言偏好）
2. **检查表 Checklist**：逐项核对该平台必含要素
3. **适配 Adapt**：把通用英文提示词改写成平台语法
4. **回归验证 Regression**：在同一平台出图，核对是否还原惊艳方向
5. **自优化 Self-optimize**：根据出图偏差微调词块

---

## 1. Midjourney (MJ)
- **参数旗标**：`--ar 4:5`（比例）`--style raw`（更写实）`--v 6.1`（版本）`--chaos 20`（变异）`--stylize 250`
- **多概念权重**：用 `::` 分隔并加权重，如 `portrait::1.2 backlight::0.8`
- **偏好**：简练、有画面感的短句，避免冗长复合句
- **负向**：`--no` 后接，如 `--no blurry, watermark`
- **适配示例（惊艳方向=电影感人像）**：
  ```
  cinematic portrait of a woman, 85mm f/1.4, backlit window light,
  teal-orange grade, anamorphic lens, film grain::1.1
  --ar 4:5 --style raw --no deformed hands, watermark
  ```

## 2. DALL·E (DALL-E 3)
- **纯自然语言**，无参数旗标；靠描述做风格混合
- **负向**：写在正文 "Avoid ..."；DALL-E 3 对负向支持弱，尽量正面描述
- **适配示例**：
  ```
  A cinematic portrait photograph of a woman shot on 85mm f/1.4 with creamy bokeh,
  backlit by window light, teal-and-orange color grade, subtle film grain,
  professional photography, highly detailed. Avoid distorted hands and watermarks.
  ```

## 3. Stable Diffusion (SD / SDXL)
- **逗号分词**，权重 `(word:1.2)`，强权重 `((word))`
- **LoRA / embeddings**：`<lora:name:0.8>`、`<embedding:name>`
- **负向字段独立**（Negative prompt）
- **适配示例**：
  ```
  Positive:
  (cinematic portrait:1.2), woman, 85mm, backlit window light, (teal-orange grade:1.1),
  anamorphic, film grain, 8k, ultra-detailed

  Negative:
  (deformed hands:1.3), watermark, blurry, low quality, extra fingers
  ```

## 4. Flux (FLUX.1)
- **详尽自然语言 + 写实强调**；无独立负向字段，用 "avoid" 写在正文
- 对长描述理解好，适合把分析块全展开
- **适配示例**：
  ```
  Cinematic portrait photograph of a woman, shot on an 85mm f/1.4 lens with creamy
  bokeh, backlit by soft window light creating a warm rim light, teal-and-orange
  color graded, subtle film grain, highly detailed skin texture, professional
  photography. Avoid deformed hands, watermarks, oversaturated colors.
  ```

---

## 平台选择建议 (Model Matching)
- 写实人像 / 产品 → **Flux / MJ**
- 艺术插画 / 二次元 → **MJ / SD**（配特定 LoRA）
- 精确文字 / Logo → 暂不推荐纯生成，建议后期加字
- 快速探索多版 → **MJ**（`--chaos` 出变异）

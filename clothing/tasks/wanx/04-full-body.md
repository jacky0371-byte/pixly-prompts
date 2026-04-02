# 04 全身展示

**版本：** v2.1-wanx
**最后更新：** 2026-04-02
**状态：** 万相调优版
**适用模型：** wan2.6-image（图像编辑模式，enable_interleave: false）

---

## 接口参数说明

```
model: wan2.6-image
enable_interleave: false
prompt_extend: false
n: 1
size: 2K
watermark: false
```

---

## 正向提示词（text 字段）

```
参考图说明：图1为全身穿着实物照，图2为模特脸部参考。生成图中的服装搭配必须严格还原图1的外观。

电商服装全身展示图，专业棚拍，全身正面视角。

模特全身入镜，从头顶到鞋底完整展示，上下留适当白边。脸型五官与图2一致。自然自信站姿，一腿为重心腿，站姿生动。鞋子完整可见，款式与图1一致。

{garment_type_composition}

背景：纯色浅米色或米白色，与整套图风格一致。
光照：全身均匀打光，头到脚亮度一致，下半身无暗区。自然轻微落地阴影。

【服装核心特征 — 必须精确还原图1】
{sku_constraints_slot}

【全身视角特别注意】
服装长度、合身度与图1的比例感一致。
上衣下装的搭配方案（颜色、款式）严格参照图1。
下装颜色必须与图1一致，禁止自行替换颜色。

【通用保真规则】
服装颜色、面料质感严格还原图1，禁止偏色。
所有可见结构元素与图1一致。
禁止简化或替换搭配方案。

画质：超高清，商业摄影级锐度。无水印无文字。

{supplement_slot}
```

---

## 反向提示词（negative_prompt 字段）

```
模糊，噪点，低画质，变形，肢体扭曲，腿部变形，下半身过暗，服装比例失调，服装结构错误，颜色偏差，色调偏绿，色调偏灰，下装颜色错误，材质错误，皮革变布料，拼接位置错误，细节丢失，AI感，蜡像感，过度磨皮，背景杂乱，文字水印
```

---

## 变量插槽说明

- `{reference_slot_6}` → content 数组第 1 个 image 字段（全身图）
- `{reference_slot_5}` → content 数组第 2 个 image 字段（模特人脸图）
- `{garment_type_composition}` — 服装类型修饰器
- `{sku_constraints_slot}` — ⚠️ **SKU 差异约束（v2.1起为必填核心段）**
- `{supplement_slot}` — ✅ 接收用户补充说明

## 接口 content 数组顺序

```json
"content": [
  { "image": "{reference_slot_6}" },
  { "image": "{reference_slot_5}" },
  { "text": "（完整 prompt 文本）" }
]
```

---

## CHANGELOG

- v1.0 (2026-03-28): 初版创建（Gemini）
- v1.1 (2026-03-28): 删除比例描述；素材引用改为变量占位符
- v2.0 (2026-03-31): 迁移至通义万相；Prompt 改为中文；剥离 negative_prompt
- v2.1 (2026-04-02): 深度调优：精简prompt、保真段重构、SKU约束升级为必填、negative_prompt针对性扩展、content数组图片前置、全身图增加下装颜色约束

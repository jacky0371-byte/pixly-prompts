# 04 全身展示

**版本：** v2.0-wanx
**最后更新：** 2026-03-31
**状态：** 万相迁移版
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
图1是全身穿着参考图，图2是模特脸型参考图。

请生成一张电商全身展示图：模特全身入镜，完整展示图1中的服装搭配效果，脸型与图2保持一致。

【构图】
{garment_type_composition}
全身入镜：从头顶到鞋底完整展示，上下各留适当留白。
服装为画面视觉焦点，整体比例自然。

【场景与光照】
干净简洁背景，与整套图风格一致。
全身均匀打光：从头到脚光照一致，下半身不产生暗区。
自然轻微落地阴影增加真实感。

【模特要求】
脸型、五官与图2严格一致。
整体身形比例与穿搭造型参照图1。
自然自信的全身站姿，一腿略为重心腿，另一腿轻松放松，站姿生动自然。
可呈现轻微走动感或放松站立感。
鞋子完整可见，款式与图1搭配风格一致。

【服装保真 — 严格执行】
图1中的主体服装所有细节必须完整还原。
整体搭配方案（上衣、下装、鞋子）参照图1呈现。
服装在全身视角下的长度、合身度与比例感必须与图1一致。

{sku_constraints_slot}

【画质要求】
超高清，商业摄影锐度。
干净专业的全身电商摄影。
无水印，无文字叠加。

{supplement_slot}
```

---

## 反向提示词（negative_prompt 字段）

```
模糊，噪点，低画质，变形，肢体扭曲，腿部变形，下半身过暗，服装比例失调，颜色偏差，背景杂乱，文字水印
```

---

## 变量插槽说明

- `{reference_slot_6}` → content 数组第 1 个 image 字段（全身图）
- `{reference_slot_5}` → content 数组第 2 个 image 字段（模特人脸图）
- `{garment_type_composition}` — 服装类型修饰器
- `{sku_constraints_slot}` — SKU 差异约束
- `{supplement_slot}` — ✅ 接收用户补充说明

## 接口 content 数组顺序

```json
"content": [
  { "text": "（完整 prompt 文本）" },
  { "image": "{reference_slot_6}" },
  { "image": "{reference_slot_5}" }
]
```

---

## CHANGELOG

- v1.0 (2026-03-28): 初版创建（Gemini）
- v1.1 (2026-03-28): 删除比例描述；素材引用改为变量占位符
- v2.0 (2026-03-31): 迁移至通义万相；Prompt 改为中文；剥离 negative_prompt；图片声明前置

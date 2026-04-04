# 10 吊牌展示图

**版本：** v1.0-seedream
**最后更新：** 2026-04-04
**状态：** Seedream 首版
**适用模型：** doubao-seedream-4.5

> ℹ️ **Seedream 优势**：Seedream 的文本渲染能力是核心强项，吊牌文字的清晰度预期优于万相。

---

## 接口参数说明

```python
extra_body={
    "image": ["{reference_slot_7}", "{reference_slot_8}"],
    "watermark": False,
    "sequential_image_generation": "disabled",
}
```

---

## Prompt 文本

```
图1是吊牌正面参考图，图2是吊牌反面（洗标/成分标）参考图。

请生成一张清晰干净的吊牌展示图：上方展示吊牌正面，下方展示吊牌反面，所有文字、标志、符号必须清晰可读。

构图：上半区图1吊牌正面特写，展示品牌名、logo及主要信息。下半区图2吊牌反面特写，展示面料成分、尺码、洗涤说明。吊牌可略有角度，可置于轻微织物背景上增加质感。两区之间干净分隔。

光照：均匀明亮正面光，文字区域无阴影遮挡，无高光反射。

文字保真：吊牌上所有文字、数字、字母的内容与排版必须与参考图严格一致。品牌标志形状细节一致。洗涤符号形态正确。吊牌底色、印刷色、logo颜色与参考图一致。不得生成虚构品牌名或虚构洗涤信息。

{sku_constraints_slot}

画质：文字区域超高清锐度，标准阅读尺寸下完全可读。无水印无额外文字。
```

---

## 变量插槽说明

- `{reference_slot_7}` → extra_body.image[0]
- `{reference_slot_8}` → extra_body.image[1]
- `{sku_constraints_slot}` — SKU 差异约束
- ❌ 不接收补充说明

---

## CHANGELOG

- v1.0 (2026-04-04): 基于万相 v2.1 迁移至 Seedream

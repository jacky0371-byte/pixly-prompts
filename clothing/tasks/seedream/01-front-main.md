# 01 正面主展示

**版本：** v1.2-seedream
**最后更新：** 2026-04-05
**状态：** Seedream 按官方指南优化版
**适用模型：** doubao-seedream-4.5 / doubao-seedream-5-0-260128

---

## 接口参数

```python
extra_body={
    "image": ["{reference_slot_1}", "{reference_slot_5}"],
    "watermark": False,
    "sequential_image_generation": "disabled",
}
```

---

## Prompt

```
参考图1中服装的所有细节（款式、面料、颜色、拼接、口袋、拉链、缝线等），让图2中的模特正面站立穿上这件服装，生成一张专业电商棚拍主图。

{garment_type_composition}

背景为纯色浅米色，专业柔光棚拍，服装面料的真实纹理清晰可见。模特脸型五官与图2保持一致，表情自然自信，双臂自然下垂，发型不遮挡领口。内搭与图1中完全相同，不要更换颜色或款式。不要给模特添加图1中没有的任何配饰。

{sku_constraints_slot}

{supplement_slot}
```

---

## 变量插槽

- `{reference_slot_1}` → extra_body.image[0]（服装正面实物照）
- `{reference_slot_5}` → extra_body.image[1]（模特人脸参考）
- `{garment_type_composition}` — 服装类型修饰器
- `{sku_constraints_slot}` — ⚠️ SKU 核心特征（必填）
- `{supplement_slot}` — ✅ 用户补充说明

---

## CHANGELOG

- v1.0 (2026-04-04): Seedream 首版
- v1.1 (2026-04-05): 增加面料纹理约束、明线颜色约束、配饰限制
- v1.2 (2026-04-05): 按 Seedream 官方提示词指南重写——从结构化条目列表改为简洁自然语言叙述；大幅精简 prompt 长度；核心操作指令前置（"参考图1...让图2模特穿上"）；移除重复堆叠的约束条目

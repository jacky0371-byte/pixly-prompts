# 06 矩阵氛围图（上半身）

**版本：** v1.0-seedream
**最后更新：** 2026-04-04
**状态：** Seedream 首版
**适用模型：** doubao-seedream-4.5

> ℹ️ **Seedream 优势**：多图组合生成是 Seedream 的核心强项（跨图一致性模块），矩阵图布局的稳定性预期优于万相。

---

## 接口参数说明

```python
extra_body={
    "image": ["{reference_slot_1}", "{reference_slot_5}"],
    "watermark": False,
    "sequential_image_generation": "disabled",
}
```

---

## Prompt 文本

```
图1是服装正面参考图，图2是模特脸型参考图。

请生成一张电商矩阵氛围图：同一模特穿着同一件服装，以2列网格布局排列3个上半身视角在同一画面中。

布局：
左列占画面左半部分，一张大号上半身主图，正面或轻微侧角，占满左列高度。
右列占画面右半部分，两张等高上半身图上下排列：右上为四分之三侧面上半身，右下为略低头或望向一侧的氛围感上半身。
各子图之间有干净间距，每个子图有独立背景，不互相重叠。
{garment_type_composition}

场景：比标准棚拍略有氛围感的暖调柔光。所有子图光照色调一致。背景为略深于纯白的暖灰色调。

模特：所有子图中的脸型五官必须与图2完全一致，同一张脸贯穿全部子图。各子图姿态自然变化。

服装保真：所有子图中服装颜色、结构细节、合身度必须与图1完全一致。颜色为最高优先级，所有子图不得出现色偏。

{sku_constraints_slot}

画质：高清，时尚编辑摄影质感。整体色调统一。无水印无文字。

{supplement_slot}
```

---

## 变量插槽说明

- `{reference_slot_1}` → extra_body.image[0]
- `{reference_slot_5}` → extra_body.image[1]
- `{garment_type_composition}` — 服装类型修饰器
- `{sku_constraints_slot}` — SKU 差异约束
- `{supplement_slot}` — ✅ 接收用户补充说明

---

## CHANGELOG

- v1.0 (2026-04-04): 基于万相 v2.1 迁移至 Seedream

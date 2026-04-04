# 07 矩阵氛围图（全身）

**版本：** v1.0-seedream
**最后更新：** 2026-04-04
**状态：** Seedream 首版
**适用模型：** doubao-seedream-4.5

---

## 接口参数说明

```python
extra_body={
    "image": ["{reference_slot_6}", "{reference_slot_5}"],
    "watermark": False,
    "sequential_image_generation": "disabled",
}
```

---

## Prompt 文本

```
图1是全身穿着参考图，图2是模特脸型参考图。

请生成一张电商全身矩阵氛围图：同一模特穿着同一套服装，以2列网格布局排列3个全身姿态在同一画面中。

布局：
左列一张大号全身主图，正面站立，头顶到鞋底完整入镜。
右列两张等高全身图上下排列：右上为行走动态姿态，右下为四分之三全身侧面角度。均全身入镜。
各子图之间有干净间距，不互相重叠。
{garment_type_composition}

场景：略有电影感的氛围，温暖光照，背景柔化处理。所有子图色调统一。

模特：所有子图中脸型五官与图2完全一致。身形比例与穿搭参照图1。姿态多样自然。

服装保真：所有子图中服装颜色、结构细节、整体造型必须与图1完全一致。颜色为最高优先级。

{sku_constraints_slot}

画质：高清，时尚编辑摄影质感。无水印无文字。

{supplement_slot}
```

---

## 变量插槽说明

- `{reference_slot_6}` → extra_body.image[0]
- `{reference_slot_5}` → extra_body.image[1]
- `{sku_constraints_slot}` — SKU 差异约束
- `{supplement_slot}` — ✅ 接收用户补充说明

---

## CHANGELOG

- v1.0 (2026-04-04): 基于万相 v2.1 迁移至 Seedream

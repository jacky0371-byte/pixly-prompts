# 06 矩阵氛围图（上半身）

**版本：** v1.2-seedream

## 接口参数

```python
extra_body={"image": ["{reference_slot_1}", "{reference_slot_5}"], "watermark": False, "sequential_image_generation": "disabled"}
```

## Prompt

```
参考图1中服装的所有细节和图2中的模特形象，生成一张电商矩阵氛围图：同一模特穿着同一件服装，以2列网格排列3个上半身视角。

{garment_type_composition}

左列为一张大号正面上半身主图，右列上下各一张等高上半身图（分别为侧面和氛围感角度）。各子图之间有干净间距，不互相重叠。所有子图中模特脸型与图2一致，服装颜色和细节与图1完全一致。背景为暖灰色调，光照统一。内搭与图1相同，不要更换颜色或款式。不要给模特添加图1中没有的配饰（如工牌、证件等）。

{sku_constraints_slot}

{supplement_slot}
```

---

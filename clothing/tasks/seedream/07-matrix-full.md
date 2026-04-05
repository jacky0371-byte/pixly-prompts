# 07 矩阵氛围图（全身）

**版本：** v1.2-seedream

## 接口参数

```python
extra_body={"image": ["{reference_slot_6}", "{reference_slot_5}"], "watermark": False, "sequential_image_generation": "disabled"}
```

## Prompt

```
参考图1中的完整穿搭和图2中的模特形象，生成一张电商全身矩阵氛围图：同一模特穿着同一套服装，以2列网格排列3个全身姿态。

{garment_type_composition}

左列一张大号正面全身主图，右列上下各一张等高全身图（行走动态和侧面角度），均从头顶到鞋底完整入镜。所有子图中模特脸型与图2一致，服装和搭配与图1完全一致。背景温暖柔和，光照色调统一。内搭和下装颜色款式与图1相同，不要更换。不要添加图1中没有的配饰。

{sku_constraints_slot}

{supplement_slot}
```

---

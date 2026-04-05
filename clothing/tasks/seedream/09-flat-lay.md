# 09 平铺正反面

**版本：** v1.2-seedream

## 接口参数

```python
extra_body={"image": ["{reference_slot_1}", "{reference_slot_3}"], "watermark": False, "sequential_image_generation": "disabled"}
```

## Prompt

```
参考图1的服装正面和图2的服装背面，生成一张无模特纯商品平铺图：上方为正面平铺俯拍，下方为背面平铺俯拍，正反对齐排列。

白色台面，完全均匀的正上方平行光，无方向性阴影。服装摆放整洁无褶皱，袖子对称。正面所有细节（口袋、拉链、缝线颜色）与图1一致，背面所有细节与图2一致，明确为同一件服装。

{sku_constraints_slot}
```

---

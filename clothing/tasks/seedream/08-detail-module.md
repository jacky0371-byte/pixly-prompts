# 08 细节模块（上1下2）

**版本：** v1.2-seedream

## 接口参数

```python
extra_body={"image": ["{reference_slot_1}", "{reference_slot_4}"], "watermark": False, "sequential_image_generation": "disabled"}
```

## Prompt

```
参考图1的服装整体和图2的工艺细节，生成一张电商细节展示模块图，采用上1下2三格布局。

上半区（约55%高度）展示模特穿着图1服装的正面上半身棚拍。下半区左右各一张工艺细节极致特写，分别选取图2中最具代表性的两处细节（如领口、口袋、拉链、袖口等）。三个区域之间有细线分隔，每个区域内留15-20%空白边距。颜色在三个区域中保持一致，细节特写中的缝线颜色必须与图2一致。

{sku_constraints_slot}
```

---

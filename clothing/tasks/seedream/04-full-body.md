# 04 全身展示

**版本：** v1.2-seedream

## 接口参数

```python
extra_body={"image": ["{reference_slot_6}", "{reference_slot_5}"], "watermark": False, "sequential_image_generation": "disabled"}
```

## Prompt

```
参考图1中的完整穿搭（服装、内搭、下装、鞋子的款式和颜色），让图2中的模特全身入镜穿上这套服装，生成一张专业电商棚拍全身展示图。

{garment_type_composition}

从头顶到鞋底完整展示，上下留适当白边。背景纯色浅米色，全身均匀打光。模特脸型五官与图2一致，站姿自然自信。内搭和下装的颜色、款式必须与图1完全相同，不要更换。不要给模特添加图1中没有的配饰。

{sku_constraints_slot}

{supplement_slot}
```

---

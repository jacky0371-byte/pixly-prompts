# 02 背面展示

**版本：** v1.2-seedream

## 接口参数

```python
extra_body={"image": ["{reference_slot_2}", "{reference_slot_5}"], "watermark": False, "sequential_image_generation": "disabled"}
```

## Prompt

```
参考图1中服装背面的所有细节（面料、颜色、拼接块位置和形状、缝线、口袋、下摆等），让图2中的模特背对镜头穿上这件服装，生成一张专业电商棚拍背面展示图。

{garment_type_composition}

模特背对镜头居中站立，头部向一侧轻转约15度露出侧脸轮廓，侧脸与图2一致。背景为纯色浅米色，柔和均匀光照让背面所有结构细节清晰可见。发型拨向一侧，后领口完整露出。不要给模特添加图1中没有的配饰。

{sku_constraints_slot}
```

---

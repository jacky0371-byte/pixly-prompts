# 03 4/5轻侧展示

**版本：** v1.2-seedream

## 接口参数

```python
extra_body={"image": ["{reference_slot_1}", "{reference_slot_5}"], "watermark": False, "sequential_image_generation": "disabled"}
```

## Prompt

```
参考图1中服装的所有细节，让图2中的模特以四分之三侧面角度（身体转约30-45度）穿上这件服装，生成一张专业电商棚拍侧面展示图。

{garment_type_composition}

模特面部略向镜头方向转，脸型五官与图2一致。背景为纯色浅米色，柔和方向性光照展现服装的立体轮廓和面料纹理。内搭与图1完全相同，不要更换。不要给模特添加图1中没有的配饰。

{sku_constraints_slot}

{supplement_slot}
```

---

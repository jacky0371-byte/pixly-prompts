# 10 吊牌展示图

**版本：** v1.2-seedream

## 接口参数

```python
extra_body={"image": ["{reference_slot_7}", "{reference_slot_8}"], "watermark": False, "sequential_image_generation": "disabled"}
```

## Prompt

```
参考图1的吊牌正面和图2的吊牌反面，生成一张清晰干净的吊牌展示图：上方为吊牌正面特写，下方为吊牌反面特写。

均匀明亮光照，文字区域无阴影遮挡。吊牌上所有文字、数字、品牌标志、洗涤符号的内容和排版必须与参考图严格一致，不要生成虚构的品牌名或洗涤信息。

{sku_constraints_slot}
```

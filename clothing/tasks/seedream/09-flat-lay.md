# 09 平铺正反面

**版本：** v1.0-seedream
**最后更新：** 2026-04-04
**状态：** Seedream 首版
**适用模型：** doubao-seedream-4.5

---

## 接口参数说明

```python
extra_body={
    "image": ["{reference_slot_1}", "{reference_slot_3}"],
    "watermark": False,
    "sequential_image_generation": "disabled",
}
```

---

## Prompt 文本

```
图1是服装正面参考图，图2是服装平铺背面参考图。

请生成一张无模特纯商品平铺图：上方展示服装正面平铺，下方展示服装背面平铺，正反面对齐排列。

构图：上半区服装正面平铺俯拍视角，下半区服装背面平铺俯拍视角，保持相同比例和对齐。两件服装宽度比例完全一致，垂直居中。摆放整洁无褶皱，袖子/裤腿对称。两区之间留适当间距。

光照：纯色白色或米白色台面。完全均匀的正上方平行光，无方向性阴影，无渐变，无景深。保持服装真实颜色。

服装保真：正面平铺与图1完全一致（口袋、纽扣、拉链位置，缝线、印花、颜色）。背面平铺与图2完全一致（背部结构、开衩、口袋、织标）。正反面明确为同一件服装。颜色为最高优先级。

{sku_constraints_slot}

画质：超高清，曝光均匀，服装摆放完美。无水印无文字。
```

---

## 变量插槽说明

- `{reference_slot_1}` → extra_body.image[0]
- `{reference_slot_3}` → extra_body.image[1]
- `{sku_constraints_slot}` — SKU 差异约束
- ❌ 不接收补充说明，无需人脸参考图

---

## CHANGELOG

- v1.0 (2026-04-04): 基于万相 v2.1 迁移至 Seedream

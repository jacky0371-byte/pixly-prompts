# 09 平铺正反面

**版本：** v1.3-seedream
**最后更新：** 2026-04-05
**状态：** Seedream 面料前置优化版
**适用模型：** doubao-seedream-4.5 / doubao-seedream-5-0-260128

---

## 接口参数说明

```python
client.images.generate(
    model="doubao-seedream-4.5",
    prompt="（完整 prompt 文本）",
    size="2K",
    response_format="url",
    extra_body={
        "image": [
            "{reference_slot_1}",   # 图1：服装正面图
            "{reference_slot_3}",   # 图2：平铺背面图
        ],
        "watermark": False,
        "sequential_image_generation": "disabled",
    }
)
```

---

## Prompt（prompt 字段）

```
图1和图2展示的是同一件{garment_summary}的正面和背面。生成一张无模特平铺图：上方正面平铺俯拍，下方背面平铺俯拍，对齐排列。

白色台面，均匀正上方平行光，无方向性阴影。摆放整洁无褶皱。正面细节与图1一致，背面细节与图2一致。面料必须呈现牛仔斜纹纹理。

{sku_constraints_slot}
```

---

## 变量插槽说明

- `{reference_slot_1}` → extra_body.image[0]（正面图）
- `{reference_slot_3}` → extra_body.image[1]（平铺背面图）
- `{garment_summary}` — ⚠️ **v1.3 新增**，从 SKU 分析结果【总体】段自动提取注入
- `{sku_constraints_slot}` — ⚠️ SKU 核心特征（必填）
- ❌ 不接收补充说明

---

## CHANGELOG

- v1.0 (2026-04-04): Seedream 首版
- v1.1 (2026-04-05): 增加面料纹理约束、明线约束、配饰限制
- v1.2 (2026-04-05): 按官方指南重写为简洁自然语言
- v1.3 (2026-04-05): 新增 {garment_summary}，面料描述前置到 prompt 第一句

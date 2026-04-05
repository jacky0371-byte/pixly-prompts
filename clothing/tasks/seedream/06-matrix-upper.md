# 06 矩阵氛围图（上半身）

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
            "{reference_slot_1}",   # 图1：服装正面实物照
            "{reference_slot_5}",   # 图2：模特人脸参考
        ],
        "watermark": False,
        "sequential_image_generation": "disabled",
    }
)
```

---

## Prompt（prompt 字段）

```
图1中的服装是{garment_summary}。参考图1的服装细节和图2的模特形象，生成一张电商矩阵氛围图：同一模特穿同一件服装，2列网格排列3个上半身视角。

{garment_type_composition}

左列大号正面主图，右列上下各一张（侧面和氛围角度）。各子图间距干净，模特脸型与图2一致。所有子图中服装面料必须呈现牛仔斜纹纹理，颜色与图1一致。内搭与图1相同，不要给模特添加图1中没有的配饰。

{sku_constraints_slot}

{supplement_slot}
```

---

## 变量插槽说明

- `{reference_slot_1}` → extra_body.image[0]（服装正面图）
- `{reference_slot_5}` → extra_body.image[1]（模特人脸参考）
- `{garment_summary}` — ⚠️ **v1.3 新增**，从 SKU 分析结果【总体】段自动提取注入
- `{garment_type_composition}` — 服装类型修饰器
- `{sku_constraints_slot}` — ⚠️ SKU 核心特征（必填）
- `{supplement_slot}` — ✅ 接收用户补充说明

---

## CHANGELOG

- v1.0 (2026-04-04): Seedream 首版
- v1.1 (2026-04-05): 增加面料纹理约束、明线约束、配饰限制
- v1.2 (2026-04-05): 按官方指南重写为简洁自然语言
- v1.3 (2026-04-05): 新增 {garment_summary}，面料描述前置到 prompt 第一句

# 01 正面主展示

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
图1中的服装是{garment_summary}。参考图1中这件服装的所有细节，让图2中的模特正面站立穿上它，生成一张专业电商棚拍主图。

{garment_type_composition}

背景纯色浅米色，专业柔光棚拍。服装面料必须呈现真实的牛仔斜纹编织纹理，不要渲染成光滑或有光泽的质感。模特脸型五官与图2一致，内搭与图1相同，不要更换。

{sku_constraints_slot}

{supplement_slot}
```

---

## 变量插槽说明

- `{reference_slot_1}` → extra_body.image[0]（服装正面实物照）
- `{reference_slot_5}` → extra_body.image[1]（模特人脸参考）
- `{garment_summary}` — ⚠️ **v1.3 新增**，从 SKU 分析结果【总体】段自动提取注入
- `{garment_type_composition}` — 服装类型修饰器注入位置
- `{sku_constraints_slot}` — ⚠️ SKU 核心特征（必填）
- `{supplement_slot}` — ✅ 接收用户补充说明

---

## CHANGELOG

- v1.0 (2026-04-04): Seedream 首版
- v1.1 (2026-04-05): 增加面料纹理约束、明线约束、配饰限制
- v1.2 (2026-04-05): 按官方指南重写为简洁自然语言
- v1.3 (2026-04-05): 新增 {garment_summary} 变量，面料类型+颜色前置到 prompt 第一句；增加"面料必须呈现XX纹理"直接描述；解决面料偏光滑偏黑问题

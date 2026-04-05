# 04 全身展示

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
            "{reference_slot_6}",   # 图1：全身穿着实物照
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
图1中的上衣是{garment_summary}。参考图1中的完整穿搭效果，让图2中的模特全身入镜穿上这套服装，生成一张专业电商棚拍全身展示图。

{garment_type_composition}

从头顶到鞋底完整展示，背景纯色浅米色，全身均匀打光。模特脸型与图2一致。上衣面料必须呈现粗糙哑光的牛仔纹理。内搭必须是图1中的白色圆领T恤，不要替换为其他颜色或款式。下装颜色款式也与图1一致。

{sku_constraints_slot}

{supplement_slot}
```

---

## 变量插槽说明

- `{reference_slot_6}` → extra_body.image[0]（全身穿着图）
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

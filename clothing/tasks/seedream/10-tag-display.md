# 10 吊牌展示图

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
            "{reference_slot_7}",   # 图1：吊牌正面
            "{reference_slot_8}",   # 图2：吊牌反面
        ],
        "watermark": False,
        "sequential_image_generation": "disabled",
    }
)
```

---

## Prompt（prompt 字段）

```
参考图1的吊牌正面和图2的吊牌反面，生成一张清晰干净的吊牌展示图：上方吊牌正面特写，下方吊牌反面特写。

均匀明亮光照，文字无阴影遮挡。所有文字、品牌标志、洗涤符号的内容排版与参考图严格一致，不要生成虚构信息。

{sku_constraints_slot}
```

---

## 变量插槽说明

- `{reference_slot_7}` → extra_body.image[0]（吊牌正面）
- `{reference_slot_8}` → extra_body.image[1]（吊牌反面）
- `{sku_constraints_slot}` — ⚠️ SKU 核心特征（必填）
- ❌ 不接收补充说明

---

## CHANGELOG

- v1.0 (2026-04-04): Seedream 首版
- v1.1 (2026-04-05): 增加面料纹理约束、明线约束、配饰限制
- v1.2 (2026-04-05): 按官方指南重写为简洁自然语言
- v1.3 (2026-04-05): 新增 {garment_summary}，面料描述前置到 prompt 第一句

# 05 肌理细节图

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
            "{reference_slot_4}",   # 图1：细节/肌理参考图
        ],
        "watermark": False,
        "sequential_image_generation": "disabled",
    }
)
```

---

## Prompt（prompt 字段）

```
图1展示的是{garment_summary}的面料细节。参考图1的真实质感，生成一张极致微距特写的面料肌理展示图。

超近距离拍摄，面料占画面80%以上，只聚焦局部。45度侧向掠射光展现编织纹理的立体感。面料的织法、纤维质感、颜色、缝线颜色都必须与图1一致。

{sku_constraints_slot}
```

---

## 变量插槽说明

- `{reference_slot_4}` → extra_body.image[0]（细节图，可传多张）
- `{garment_summary}` — ⚠️ **v1.3 新增**，从 SKU 分析结果【总体】段自动提取注入
- `{sku_constraints_slot}` — ⚠️ SKU 核心特征（必填）
- ❌ 不接收补充说明

---

## CHANGELOG

- v1.0 (2026-04-04): Seedream 首版
- v1.1 (2026-04-05): 增加面料纹理约束、明线约束、配饰限制
- v1.2 (2026-04-05): 按官方指南重写为简洁自然语言
- v1.3 (2026-04-05): 新增 {garment_summary}，面料描述前置到 prompt 第一句

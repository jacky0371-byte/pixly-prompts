# 03 4/5轻侧展示

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
图1中的服装是{garment_summary}。参考图1中这件服装的所有细节，让图2中的模特以四分之三侧面角度穿上它，生成一张专业电商棚拍侧面展示图。

{garment_type_composition}

背景纯色浅米色，柔和方向性光照展现服装立体轮廓。模特身体转约30-45度，面部略朝镜头，脸型与图2一致。面料必须呈现粗糙哑光的牛仔纹理，不要渲染成光滑质感。内搭与图1相同。

{sku_constraints_slot}

{supplement_slot}
```

---

## 变量插槽说明

- `{reference_slot_1}` → extra_body.image[0]（服装正面图）
- `{reference_slot_5}` → extra_body.image[1]（模特人脸参考）
- `{garment_summary}` — ⚠️ v1.3 新增
- `{garment_type_composition}` — 服装类型修饰器
- `{sku_constraints_slot}` — ⚠️ SKU 核心特征（必填）
- `{supplement_slot}` — ✅ 接收用户补充说明

---

## CHANGELOG

- v1.0 ~ v1.2: 同系列迭代
- v1.3 (2026-04-05): 新增 {garment_summary}，面料描述前置


---

# 04 全身展示

**版本：** v1.0-seedream
**最后更新：** 2026-04-04
**状态：** Seedream 首版
**适用模型：** doubao-seedream-4.5（或 doubao-seedream-5-0-260128）

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

## Prompt 文本（prompt 字段）

```
图1是全身穿着实物照，图2是模特脸部参考。

请生成一张电商服装全身展示图：模特全身入镜，完整展示图1中的服装搭配效果，脸型与图2一致。

要求如下：

构图：全身入镜，从头顶到鞋底完整展示，上下留适当白边。服装为画面视觉焦点。
{garment_type_composition}

背景：纯色浅米色或米白色，与整套图风格一致。
光照：全身均匀打光，头到脚亮度一致，下半身无暗区。自然轻微落地阴影。

模特：脸型五官与图2严格一致。自然自信站姿，一腿为重心腿，站姿生动。鞋子完整可见，款式与图1一致。

【本商品核心特征 — 以下每一条必须精确还原】
{sku_constraints_slot}

全身视角特别注意：服装长度、合身度与图1的比例感一致。上衣下装的搭配方案（颜色、款式）严格参照图1。下装颜色必须与图1一致，不得自行替换颜色。

服装保真规则：
服装颜色、面料质感严格还原图1，不得偏色。所有可见结构元素与图1一致。不得简化或替换搭配方案。

画质：超高清，商业摄影级锐度。无水印无文字。

{supplement_slot}
```

---

## 变量插槽说明

- `{reference_slot_6}` → extra_body.image[0]（全身图）
- `{reference_slot_5}` → extra_body.image[1]（模特人脸图）
- `{garment_type_composition}` — 服装类型修饰器
- `{sku_constraints_slot}` — ⚠️ **SKU 差异约束（必填核心段）**
- `{supplement_slot}` — ✅ 接收用户补充说明

---

## CHANGELOG

- v1.0 (2026-04-04): 基于万相 v2.1 迁移至 Seedream

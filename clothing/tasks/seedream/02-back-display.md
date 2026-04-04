# 02 背面展示

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
            "{reference_slot_2}",   # 图1：服装背面穿着实物照
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
图1是服装背面穿着实物照，图2是模特脸部参考。

请生成一张电商服装背面展示图：模特背对镜头穿着图1中的服装，展示服装背面全貌。

要求如下：

构图：模特背对镜头居中站立，头部向一侧轻微转动约15度，隐约可见侧脸轮廓。
{garment_type_composition}

背景：纯色浅米色或米白色，与正面主图一致。
光照：柔和均匀棚拍光，背部所有缝线、口袋、拉链、拼接结构清晰可见，无遮挡阴影。

模特：侧脸轮廓与图2一致。站姿挺拔，肩膀打开，双臂自然下垂不遮挡背部。发型拨向一侧，后领口完整可见。

【本商品核心特征 — 以下每一条必须精确还原】
{sku_constraints_slot}

服装保真规则：
服装背面的颜色、面料质感必须严格还原图1，不得偏色。
背面所有结构元素（后片拼接、缝线、省道、口袋、拉链、开衩、装饰条、织标）的位置、形状、材质必须与图1完全一致。
不得遗漏、简化或添加背面设计元素。

画质：超高清，商业摄影级锐度，与正面主图光照风格一致。无水印无文字。
```

---

## 变量插槽说明

- `{reference_slot_2}` → extra_body.image[0]（服装背面穿着图）
- `{reference_slot_5}` → extra_body.image[1]（模特人脸图）
- `{garment_type_composition}` — 服装类型修饰器
- `{sku_constraints_slot}` — ⚠️ **SKU 差异约束（必填核心段）**
- ❌ 不接收补充说明

---

## CHANGELOG

- v1.0 (2026-04-04): 基于万相 v2.1 迁移至 Seedream

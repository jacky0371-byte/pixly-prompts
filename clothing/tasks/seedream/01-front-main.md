# 01 正面主展示

**版本：** v1.0-seedream
**最后更新：** 2026-04-04
**状态：** Seedream 首版
**适用模型：** doubao-seedream-4.5（或 doubao-seedream-5-0-260128）

---

## 接口参数说明

```python
client.images.generate(
    model="doubao-seedream-4.5",    # 或 doubao-seedream-5-0-260128
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

## Prompt 文本（prompt 字段）

```
图1是服装正面实物照，图2是模特脸部参考。

请生成一张电商服装主图：一位模特正面站立穿着图1中的服装，脸型五官与图2一致。

要求如下：

构图：模特居中，直面镜头，服装为画面视觉焦点。
{garment_type_composition}

背景：纯色浅米色或米白色，干净无杂物。
光照：专业柔光棚拍，正面左侧主光，右侧补光，服装无硬阴影，面料质感清晰可见。脚下自然落地阴影。

模特：脸型五官与图2严格一致。表情自然自信，眼神看向镜头。站姿放松，双臂自然下垂。发型整洁不遮挡领口肩部。

【本商品核心特征 — 以下每一条必须精确还原】
{sku_constraints_slot}

服装保真规则：
服装的颜色、面料质感、光泽度必须严格还原图1，不得偏色、提亮或美化。
所有结构元素（领型、袖口、口袋、拉链、纽扣、拼接区域、缝线、印花）的位置、形状、材质、颜色必须与图1完全一致。
不得遗漏、简化、添加或移动任何设计元素。
不得用"常见款式"替代图1的实际设计。

画质：超高清，商业摄影级锐度，无水印无文字无边框。

{supplement_slot}
```

---

## 变量插槽说明

- `{reference_slot_1}` → extra_body.image[0]（服装正面图 URL/Base64）
- `{reference_slot_5}` → extra_body.image[1]（模特人脸图 URL/Base64）
- `{garment_type_composition}` — 服装类型修饰器注入位置
- `{sku_constraints_slot}` — ⚠️ **SKU 差异约束（必填核心段）**
- `{supplement_slot}` — ✅ 接收用户补充说明

---

## 与万相版的关键差异

| 维度 | 万相 wan2.6-image | Seedream 4.5/5.0 |
|------|------------------|-----------------|
| API 格式 | DashScope content 数组 | OpenAI 兼容 images.generate |
| 参考图传入 | content[].image 字段 | extra_body.image 数组 |
| negative_prompt | ✅ 有独立字段 | ❌ 不支持，需在 prompt 中用正面描述替代 |
| prompt 语言 | 中文 | 中文（Seedream 中文指令遵循度优于万相） |
| 材质还原 | 弱（皮革/拼接易出错） | 强（材质理解为核心强项） |

---

## CHANGELOG

- v1.0 (2026-04-04): 基于万相 v2.1 迁移至 Seedream；适配 OpenAI 兼容 API 格式；移除 negative_prompt（Seedream 不支持）；保真约束改用正面描述方式；精简 prompt 结构

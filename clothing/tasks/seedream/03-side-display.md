# 03 4/5轻侧展示

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

请生成一张电商服装四分之三侧面展示图：模特身体向侧面转动约30-45度，面部略向镜头方向转，展示服装的立体轮廓与侧面构造。

要求如下：

构图：模特身体转动30-45度，形成自然的四分之三角度。面部相对身体再向镜头方向多转约20度，实现"身侧面、脸四分之三"的站姿。前脚略前迈，重心自然转移。
{garment_type_composition}

背景：纯色浅米色或米白色，与整套图风格一致。
光照：柔和方向性光，面向镜头侧略强，制造轻微立体层次。服装三维形态与垂感清晰展现。

模特：脸型五官与图2严格一致。表情自然，眼神朝向镜头。手臂不遮挡侧面口袋与侧缝。

【本商品核心特征 — 以下每一条必须精确还原】
{sku_constraints_slot}

侧面角度特别注意：侧缝线位置与结构清晰还原。侧袋（如有）在此角度的可见度与位置准确。袖型侧面垂落形态自然。

服装保真规则：
服装颜色、面料质感、光泽度严格还原图1，不得偏色。所有可见结构元素的位置、形状、材质、颜色与图1一致。不得简化侧面结构细节。

画质：超高清，商业摄影级锐度，与正面背面风格统一。无水印无文字。

{supplement_slot}
```

---

## 变量插槽说明

- `{reference_slot_1}` → extra_body.image[0]（服装正面图）
- `{reference_slot_5}` → extra_body.image[1]（模特人脸图）
- `{garment_type_composition}` — 服装类型修饰器
- `{sku_constraints_slot}` — ⚠️ **SKU 差异约束（必填核心段）**
- `{supplement_slot}` — ✅ 接收用户补充说明

---

## CHANGELOG

- v1.0 (2026-04-04): 基于万相 v2.1 迁移至 Seedream

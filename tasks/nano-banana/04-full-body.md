# 04 全身展示

**版本：** v1.2
**最后更新：** 2026-03-28
**状态：** 测试中

## 当前模板

```
You are a professional e-commerce fashion photographer creating a full-body styling shot.

REFERENCE IMAGES:
The full-body outfit reference:
{reference_slot_6}

The model face reference:
{reference_slot_5}

OBJECTIVE:
Generate a full-body image showing the complete outfit styling. This shot should convey how the garment looks as part of a complete, wearable look.

COMPOSITION:
- Full body in frame — from top of head to shoes, with a small margin at top and bottom
- {garment_type_composition}
- The hero garment remains the visual focus even in the full-body context

SCENE & LIGHTING:
- Clean studio background, consistent with other images
- Full-body lighting: even illumination from head to toe, no dark zones on the lower body
- Soft shadows for grounding

MODEL DIRECTION:
- The model's face MUST match {reference_slot_5} EXACTLY — identical facial features, face shape, skin tone, hairstyle, AND all accessories (glasses, earrings, etc.). If the reference model wears glasses, the generated model MUST wear the same glasses. Non-negotiable.
- The model's body proportions and outfit styling MUST match {reference_slot_6}
- Natural, confident full-body pose — slight weight shift to one leg for a natural stance
- Can show a gentle walking motion or a relaxed standing pose
- Shoes should be visible and appropriate for the outfit style

PRODUCT FIDELITY — CRITICAL:
- COLOR ACCURACY IS THE HIGHEST PRIORITY — the garment color MUST exactly match {reference_slot_6}. Do NOT lighten, darken, shift hue, or adjust saturation in any direction. Treat color as a locked parameter.
- The hero garment MUST exactly match the garment shown in {reference_slot_6} in ALL structural details:
  - CUFF DETAIL: Exact cuff design, material, and construction — ribbed, button, folded, or other style MUST match exactly
  - ZIPPER DETAIL: All zippers must match in position, pull-tab style, material (metal/plastic), and color
  - All pockets, seams, collars, hems exactly as shown
- The overall outfit coordination should match {reference_slot_6}
- Preserve garment length, fit, and proportional appearance on the body
- FINAL CHECK: Verify garment color matches reference before outputting. If any color drift detected, regenerate.
{sku_constraints_slot}

QUALITY:
- Ultra-high resolution
- Clean, professional, full-body e-commerce photography

{supplement_slot}
```

## 变量插槽说明

- `{reference_slot_6}` — 全身图
- `{reference_slot_5}` — 模特人脸图
- `{garment_type_composition}` — 服装类型修饰器
- `{sku_constraints_slot}` — SKU 差异约束
- `{supplement_slot}` — ✅ 接收用户补充说明

## CHANGELOG

- v1.0 (2026-03-28): 初版创建
- v1.1 (2026-03-28): 删除比例描述；素材引用改为 {reference_slot_X} 变量
- v1.2 (2026-03-28): 强化颜色锁定为最高优先级；人脸匹配扩展含眼镜等配饰；增加袖口/拉链细节精确还原指令；增加最终颜色检查步骤

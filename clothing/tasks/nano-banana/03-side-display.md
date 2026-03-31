# 03 4/5轻侧展示

**版本：** v1.2
**最后更新：** 2026-03-28
**状态：** 测试中

## 当前模板

```
You are a professional e-commerce fashion photographer creating a three-quarter angle product image.

REFERENCE IMAGES:
The garment front reference:
{reference_slot_1}

The model face reference:
{reference_slot_5}

OBJECTIVE:
Generate a natural three-quarter view (roughly 30-45 degrees from front) that shows the garment's dimensional silhouette and side construction.

COMPOSITION:
- The model is turned approximately 30-45 degrees from the camera (a "4/5 view")
- {garment_type_composition}
- This angle should reveal the garment's side profile, sleeve drape, and dimensional fit

SCENE & LIGHTING:
- Clean, minimal studio background — matching other images in the set
- Soft directional lighting that creates gentle depth — slightly stronger from the camera-facing side
- The lighting should accentuate the garment's three-dimensional form and fabric drape

MODEL DIRECTION:
- The model's face MUST match {reference_slot_5} EXACTLY — identical facial features, face shape, skin tone, hairstyle, AND all accessories visible in the reference (glasses, earrings, etc.). If the reference model wears glasses, the generated model MUST wear the same glasses in every image. This is non-negotiable.
- Natural, relaxed three-quarter pose — one foot slightly forward for a natural stance
- Body turned but face angled slightly more toward camera (about 20 degrees from the body angle)
- Natural expression, eyes toward camera or slightly past it
- Arms in a natural position that does NOT hide garment details (side pockets, seams, etc.)

PRODUCT FIDELITY — CRITICAL:
- The garment MUST match {reference_slot_1} in all structural details
- From this side angle, pay special attention to:
  - Side seam construction and placement
  - Side pocket visibility and position (if applicable)
  - Sleeve shape and drape from the side
  - CUFF DETAIL: Reproduce the exact cuff design, material, and construction — ribbed elastic, button cuff, folded cuff, or any other style MUST match the reference exactly. Do NOT substitute with a generic cuff.
  - ZIPPER DETAIL: All zippers must match the reference in position, pull-tab style, material (metal/plastic), and color. Do NOT simplify or replace zipper hardware.
  - How the garment falls and fits around the torso from this angle
  - Any asymmetric design elements visible from this angle
  - COLOR ACCURACY IS THE HIGHEST PRIORITY — the garment color MUST exactly match {reference_slot_1}. Do NOT lighten, darken, shift the hue, or adjust the saturation in any way. Treat the color as a locked, non-negotiable parameter.
- Do NOT simplify side construction details
- FINAL CHECK: Verify garment color matches the reference before outputting. If any color drift is detected, regenerate.
{sku_constraints_slot}

QUALITY:
- Ultra-high resolution, commercially sharp
- Consistent style with front and back views

{supplement_slot}
```

## 变量插槽说明

- `{reference_slot_1}` — 正面图
- `{reference_slot_5}` — 模特人脸图
- `{garment_type_composition}` — 服装类型修饰器
- `{sku_constraints_slot}` — SKU 差异约束
- `{supplement_slot}` — ✅ 接收用户补充说明

## CHANGELOG

- v1.0 (2026-03-28): 初版创建
- v1.1 (2026-03-28): 删除比例描述；素材引用改为 {reference_slot_X} 变量
- v1.2 (2026-03-28): 强化颜色锁定约束；人脸匹配扩展至包含眼镜等全部配饰；增加袖口和拉链细节精确还原指令

# 02 背面展示

**版本：** v1.3
**最后更新：** 2026-03-28
**状态：** 测试中

## 当前模板

```
You are a professional e-commerce fashion photographer creating a back-view product image.

REFERENCE IMAGES:
The garment back reference (worn on model):
{reference_slot_2}

The model face reference:
{reference_slot_5}

OBJECTIVE:
Generate a clean back-view photo showing the garment's rear construction and design details.

COMPOSITION:
- The model stands with their back to the camera, centered in frame
- {garment_type_composition}
- Slight turn of the head (about 15-20 degrees) so the profile/jawline is barely visible — this adds life without distracting from the garment

SCENE & LIGHTING:
- Clean, minimal background — matching the front-view style (solid light beige or off-white)
- Soft, even studio lighting that reveals back construction details
- Ensure stitching lines, back pockets, zippers, and structural elements are clearly visible

MODEL DIRECTION:
- The model's face profile MUST match {reference_slot_5} EXACTLY — maintain identical facial features, face shape, skin tone, hairstyle, AND all accessories (glasses, earrings, etc.) even in the slight profile view. If the reference model wears glasses, the generated model MUST wear the same glasses. Non-negotiable.
- Straight, confident standing posture — shoulders back, spine aligned
- Arms naturally at sides, not hiding any garment details
- Hair pulled to one side or neatly arranged so the back neckline and collar are fully visible

PRODUCT FIDELITY — CRITICAL:
- The garment back MUST exactly match {reference_slot_2}
- Preserve ALL of the following:
  - Back panel construction, seam lines, darts
  - Back pockets, zippers, vents, slits
  - Collar and neckline shape from the back
  - Hem shape and length
  - Any back prints, labels, embroidery, or decorative elements
  - CUFF DETAIL: Reproduce the exact cuff design and material visible from the back — ribbed elastic, button cuff, or folded cuff must match exactly
  - ZIPPER DETAIL: Any zippers visible from the back must match in pull-tab style, material, and color
  - COLOR ACCURACY IS THE HIGHEST PRIORITY — the garment color MUST exactly match {reference_slot_2}. Do NOT lighten, darken, saturate, desaturate, or shift the hue. Treat color as a locked parameter.
- Do NOT add or alter any structural element not present in {reference_slot_2}
- FINAL CHECK: Verify garment color matches the reference before outputting. If any color shift detected, regenerate.
{sku_constraints_slot}

QUALITY:
- Ultra-high resolution, commercially sharp
- Consistent lighting style with the front-view image
```

## 变量插槽说明

- `{reference_slot_2}` — 背面图（系统自动替换为实际图片）
- `{reference_slot_5}` — 模特人脸图
- `{garment_type_composition}` — 服装类型修饰器
- `{sku_constraints_slot}` — SKU 差异约束
- ❌ 不接收补充说明

## CHANGELOG

- v1.0 (2026-03-28): 初版创建
- v1.1 (2026-03-28): 删除比例描述；素材引用改为 {reference_slot_X} 变量
- v1.2 (2026-03-28): 强化颜色保真约束 — 颜色升级为最高优先级，锁定色调漂移，增加最终检查步骤
- v1.3 (2026-03-28): 人脸匹配扩展含眼镜等全部配饰；增加袖口/拉链细节精确还原指令（批量更新）

# 09 平铺正反面

**版本：** v1.2
**最后更新：** 2026-03-28
**状态：** 测试中

## 当前模板

```
You are a product photographer creating a flat-lay front-and-back comparison image for an e-commerce listing.

REFERENCE IMAGES:
The garment front reference:
{reference_slot_1}

The garment flat-lay back reference:
{reference_slot_3}

OBJECTIVE:
Generate a clean flat-lay image showing the garment from both the front and back, arranged for easy comparison. This is a NO-MODEL, product-only image.

COMPOSITION:
- TOP HALF: Front view of the garment laid flat (bird's eye / overhead view)
- BOTTOM HALF: Back view of the garment laid flat (bird's eye / overhead view)
- Both views should be the same scale and aligned vertically for easy comparison
- The garment should be neatly arranged — no wrinkles, sleeves/legs symmetrically positioned
- Small margin between front and back sections

SCENE & LIGHTING:
- Clean, solid-color surface — white, off-white, or very light gray
- Perfectly even overhead lighting — no directional shadows
- Flat lighting that reveals construction details without creating depth illusion

PRODUCT FIDELITY — CRITICAL:
- COLOR ACCURACY IS THE HIGHEST PRIORITY — both the front and back views MUST reproduce the exact garment color from the references. Do NOT shift, lighten, darken, or alter the color. The flat-lay lighting must NOT cause color distortion — if overhead lighting would wash out a dark navy, adjust the lighting intensity to preserve true color. Treat color as a locked parameter.
- FRONT VIEW must exactly match {reference_slot_1}:
  - All pockets, buttons, zippers in exact positions
  - All seam lines, topstitching, prints/patterns
  - Exact color and fabric texture
- BACK VIEW must exactly match {reference_slot_3}:
  - Back panel construction, vents, pockets, labels
  - All structural details preserved
- Both views must clearly be the SAME garment
- FINAL CHECK: Verify color accuracy in both views before outputting. If any color drift detected, regenerate.
{sku_constraints_slot}

QUALITY:
- Ultra-sharp, even exposure
- Professional flat-lay product photography
- No wrinkles, no creases, garment perfectly arranged
```

## 变量插槽说明

- `{reference_slot_1}` — 正面图
- `{reference_slot_3}` — 平铺背面图
- `{sku_constraints_slot}` — SKU 差异约束
- ❌ 不接收补充说明
- 无需人脸参考图

## CHANGELOG

- v1.0 (2026-03-28): 初版创建
- v1.1 (2026-03-28): 删除比例描述；素材引用改为 {reference_slot_X} 变量
- v1.2 (2026-03-28): 颜色锁定为最高优先级；增加平铺打光不得导致色偏的约束；增加最终颜色检查（批量更新）

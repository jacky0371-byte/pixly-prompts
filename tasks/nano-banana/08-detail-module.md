# 08 细节模块(上1下2)

**版本：** v1.2
**最后更新：** 2026-03-28
**状态：** 测试中

## 当前模板

```
You are creating a composite product detail module image for an e-commerce listing page.

REFERENCE IMAGES:
The garment front reference:
{reference_slot_1}

The garment detail/texture reference:
{reference_slot_4}

OBJECTIVE:
Generate a single image with a specific layout:
- TOP HALF: A styled upper-body or half-body shot of the model wearing the garment (occupying roughly 55% of the image height)
- BOTTOM HALF: Two side-by-side close-up detail shots of the garment (each occupying roughly half the width, together filling the remaining 45% of the image height)

This is a COMPOSITE LAYOUT — one image containing three distinct photographic zones.

LAYOUT SPECIFICATION:
- Top section (55% height): Model wearing the garment from {reference_slot_1}, front-facing, styled studio shot with clean background
- Bottom-left section (45% height, 50% width): Close-up detail of a notable design feature from {reference_slot_4} (e.g., collar construction, pocket detail, button/zipper, sleeve cuff)
- Bottom-right section (45% height, 50% width): Close-up detail of another notable feature OR fabric texture close-up from {reference_slot_4}
- Thin clean dividing lines or subtle spacing between sections
- Leave 15-20% blank margin space in each section for potential text overlay (the merchant will add text later)

SCENE & LIGHTING:
- Top section: Standard studio lighting, clean background
- Bottom sections: Macro-style raking light to reveal texture and construction details
- Consistent color temperature across all three zones

PRODUCT FIDELITY — CRITICAL:
- COLOR ACCURACY IS THE HIGHEST PRIORITY across all three zones — the garment color MUST exactly match the references in every section. Do NOT shift, enhance, or alter the color in the full shot or the close-up details. Treat color as a locked parameter.
- The garment in the top section MUST match {reference_slot_1} in all structural details
- The detail close-ups in the bottom sections MUST show actual details from {reference_slot_4} with full precision:
  - CUFF DETAIL: If showing sleeve cuff, reproduce exact cuff shape, ribbing, buttons, or elastic exactly
  - ZIPPER DETAIL: If showing zipper, reproduce exact pull-tab style, material (metal/plastic), teeth width, and color
  - Thread and stitching color must match the reference
- Details should be selected to highlight the garment's most distinctive features
- FINAL CHECK: Verify garment color is consistent across all three zones before outputting. If any zone shows color drift, regenerate.
{sku_constraints_slot}

QUALITY:
- High resolution across all three zones
- Professional e-commerce composite layout
- Clean, balanced visual weight between zones
```

## 变量插槽说明

- `{reference_slot_1}` — 正面图
- `{reference_slot_4}` — 细节图
- `{sku_constraints_slot}` — SKU 差异约束
- ❌ 不接收补充说明

## CHANGELOG

- v1.0 (2026-03-28): 初版创建
- v1.1 (2026-03-28): 删除比例描述；素材引用改为 {reference_slot_X} 变量
- v1.2 (2026-03-28): 颜色锁定为最高优先级并覆盖全部三个区域；增加袖口/拉链/线迹颜色精确还原指令；增加最终颜色检查（批量更新）

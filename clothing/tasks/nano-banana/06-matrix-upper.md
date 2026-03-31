# 06 矩阵氛围图(上半身)

**版本：** v1.3
**最后更新：** 2026-03-28
**状态：** 测试中

## 当前模板

```
You are a fashion editorial photographer creating an atmospheric mood board / matrix image for an e-commerce detail page.

REFERENCE IMAGES:
The garment front reference:
{reference_slot_1}

The model face reference:
{reference_slot_5}

OBJECTIVE:
Generate a multi-angle upper-body matrix image that combines 3-4 different angles/poses of the same model wearing the same garment. This creates an editorial "mood" feel that elevates the product presentation beyond standard e-commerce.

COMPOSITION — FIXED GRID LAYOUT (CRITICAL):
- The image MUST be composed as a structured grid — NOT a random collage, NOT overlapping images, NOT free-floating cutouts
- Use a FIXED 2-column layout:
  - LEFT column: one large upper-body shot occupying the full left half (front-facing or slight angle, the hero view)
  - RIGHT column: two stacked upper-body shots of equal height, each occupying half of the right column (one slightly turned pose on top, one more editorial/candid below)
- All cells must have clean, consistent spacing/gutters between them — same gutter width throughout
- Each sub-image has its own contained background — no bleed or overlap between cells
- {garment_type_composition}
- All views show the UPPER BODY primarily

SCENE & LIGHTING:
- Slightly more atmospheric than standard studio shots
- Warm, soft, lifestyle-feeling lighting — as if in a high-end showroom or soft natural light
- Consistent lighting across all sub-views
- Background can be a soft warm tone, slightly darker than standard white

MODEL DIRECTION:
- The SAME face from {reference_slot_5} must appear in ALL sub-views — identical facial features, skin tone, hairstyle, AND all accessories (glasses, earrings, etc.) throughout. If the reference model wears glasses, ALL sub-views MUST show glasses. Non-negotiable.
- Vary the poses naturally: one confident, one relaxed, one slightly turned
- Expressions should feel natural and editorial — not stiff catalog poses

PRODUCT FIDELITY — CRITICAL:
- COLOR ACCURACY IS THE HIGHEST PRIORITY — the garment color MUST be absolutely consistent and exactly match {reference_slot_1} across ALL sub-views. Do NOT shift, lighten, darken, or alter the color in any sub-view. Treat color as a locked parameter.
- The garment MUST be structurally identical across all sub-views — same color, same details, same fit
- CUFF DETAIL: Exact cuff design and material must be reproduced consistently in every sub-view
- ZIPPER DETAIL: Zipper hardware style and color must match the reference in every sub-view
- All structural details must match {reference_slot_1} in every sub-view
- FINAL CHECK: Verify all sub-views show identical garment color before outputting. If any color drift between sub-views or from reference, regenerate.
{sku_constraints_slot}

QUALITY:
- High resolution, editorial fashion photography quality
- Cohesive color grading across all sub-views
- The overall image should feel like a page from a fashion magazine

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
- v1.2 (2026-03-28): 重构拼接布局 — 从随机拼贴改为固定2列网格
- v1.3 (2026-03-28): 颜色锁定为最高优先级；人脸匹配扩展含眼镜等全部配饰；增加袖口/拉链细节指令；增加最终颜色检查（批量更新）

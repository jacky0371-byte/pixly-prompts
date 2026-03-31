# 07 矩阵氛围图(全身)

**版本：** v1.3
**最后更新：** 2026-03-28
**状态：** 测试中

## 当前模板

```
You are a fashion editorial photographer creating a full-body atmospheric matrix image.

REFERENCE IMAGES:
The full-body outfit reference:
{reference_slot_6}

The model face reference:
{reference_slot_5}

OBJECTIVE:
Generate a multi-angle full-body matrix image showing 3-4 different full-body poses of the same model in the same outfit. This creates a dynamic, editorial presentation.

COMPOSITION — FIXED GRID LAYOUT (CRITICAL):
- The image MUST use a structured, fixed grid — NOT a random collage, NOT overlapping photos, NOT free-floating cutouts
- Use a FIXED 2-column layout:
  - LEFT column: one large full-body shot occupying the full left half (front-facing, the hero view — head to shoes fully visible)
  - RIGHT column: two stacked full-body shots of equal height, each occupying half of the right column (one dynamic/walking pose on top, one three-quarter angle below)
- All cells must have clean, consistent gutters — same spacing throughout
- Each sub-image has its own self-contained background — no bleed or overlap between cells
- {garment_type_composition}
- All views are FULL BODY — head to shoes visible in each sub-image

SCENE & LIGHTING:
- Slightly cinematic atmosphere — outdoor urban feel OR high-end indoor setting
- Consistent warm lighting across all sub-views
- Soft architectural or lifestyle background (blurred, not distracting)

MODEL DIRECTION:
- The SAME face from {reference_slot_5} must appear in ALL views — identical facial features, skin tone, hairstyle, AND all accessories (glasses, earrings, etc.) throughout. If the reference model wears glasses, ALL sub-views MUST show glasses. Non-negotiable.
- Body proportions and outfit styling should match {reference_slot_6}
- Vary poses: standing, walking, slight turn, looking away
- Natural, confident body language throughout

PRODUCT FIDELITY — CRITICAL:
- COLOR ACCURACY IS THE HIGHEST PRIORITY — the garment color MUST be absolutely consistent and exactly match {reference_slot_6} across ALL sub-views. Do NOT shift, lighten, darken, or alter the color in any sub-view. Treat color as a locked parameter.
- The outfit MUST be structurally identical in all sub-views — matching {reference_slot_6} exactly
- CUFF DETAIL: Exact cuff design and material reproduced consistently in every sub-view
- ZIPPER DETAIL: Zipper hardware style and color must match the reference in every sub-view
- All garment structural details preserved in every angle
- FINAL CHECK: Verify all sub-views show identical garment color before outputting. If any color drift detected, regenerate.
{sku_constraints_slot}

QUALITY:
- High resolution, editorial fashion photography
- Cohesive color grading and atmosphere

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
- v1.2 (2026-03-28): 重构拼接布局 — 从创意随机拼贴改为固定2列网格
- v1.3 (2026-03-28): 颜色锁定为最高优先级；人脸匹配扩展含眼镜等全部配饰；增加袖口/拉链细节指令；增加最终颜色检查（批量更新）

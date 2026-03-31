# 01 正面主展示

**版本：** v1.3
**最后更新：** 2026-03-28
**状态：** 测试中

## 当前模板

```
You are a professional e-commerce fashion photographer creating a hero product image for an online store's detail page.

REFERENCE IMAGES:
The garment front reference:
{reference_slot_1}

The model face reference:
{reference_slot_5}

OBJECTIVE:
Generate a high-quality front-facing product photo. This is the PRIMARY display image — it must look premium, clean, and commercially appealing.

COMPOSITION:
- The model stands facing the camera directly, centered in frame
- {garment_type_composition}
- The garment should be the clear visual focus — no distracting elements

SCENE & LIGHTING:
- Clean, minimal background — solid light beige, off-white, or very soft warm gray
- Professional studio lighting: soft diffused main light from front-left, gentle fill from right
- No harsh shadows on the garment — lighting should reveal fabric texture and construction details
- Subtle ground shadow for natural grounding

MODEL DIRECTION:
- The model's face MUST match {reference_slot_5} EXACTLY — maintain identical facial features, face shape, skin tone, hairstyle, AND all accessories visible in the reference (glasses, earrings, etc.). If the reference model wears glasses, the generated model MUST wear the same glasses. This is non-negotiable and must be consistent across every generated image.
- Natural, confident expression — slight smile or neutral
- Relaxed standing pose, arms naturally at sides or one hand slightly touching the garment
- Eyes looking at the camera or slightly off-camera
- Hair neatly styled, not covering the garment

PRODUCT FIDELITY — CRITICAL:
- The garment MUST exactly match {reference_slot_1} in every structural detail
- Preserve ALL of the following exactly as shown in the reference:
  - Neckline shape and depth
  - Sleeve length, width, and cuff design
  - All pockets: exact position, size, shape, flap design
  - All buttons, zippers, snaps: exact position and style
  - Seam lines, stitching patterns, decorative topstitching
  - Fabric texture, sheen, drape, weight appearance
  - COLOR ACCURACY IS THE HIGHEST PRIORITY — match the exact shade, do NOT shift or enhance the color. If the garment is dark navy, it MUST remain dark navy. Treat color as a locked, non-negotiable parameter.
  - CUFF DETAIL: Reproduce the exact cuff design, material, and construction — ribbed elastic, button cuff, folded cuff, or any other style MUST match the reference exactly. Do NOT substitute with a generic cuff.
  - ZIPPER DETAIL: All zippers must match in position, pull-tab style, material (metal/plastic), and color. Do NOT simplify or replace zipper hardware.
  - Any prints, patterns, logos, or embroidery: exact position and scale
- Do NOT simplify, add, remove, or relocate ANY structural element
- Do NOT default to a "typical" version of this garment type — follow the reference exactly
- FINAL CHECK: Before outputting, verify the garment color in your generation matches the reference. If there is ANY color shift, regenerate.
{sku_constraints_slot}

QUALITY:
- Ultra-high resolution, commercially sharp
- Professional e-commerce photography standard
- No watermarks, no text overlays, no borders

{supplement_slot}
```

## 变量插槽说明

- `{reference_slot_1}` — 正面图（系统自动替换为实际图片）
- `{reference_slot_5}` — 模特人脸图（系统自动替换为实际图片）
- `{garment_type_composition}` — 服装类型修饰器
- `{sku_constraints_slot}` — SKU 差异约束
- `{supplement_slot}` — ✅ 接收用户补充说明

## CHANGELOG

- v1.0 (2026-03-28): 初版创建
- v1.1 (2026-03-28): 删除比例描述（由接口配置项传入）；素材引用改为 {reference_slot_X} 变量占位符
- v1.2 (2026-03-28): 强化颜色保真约束 — 将颜色升级为最高优先级，增加明确的色调锁定指令和最终检查步骤
- v1.3 (2026-03-28): 人脸匹配扩展含眼镜等全部配饰；增加袖口/拉链细节精确还原指令（批量更新）

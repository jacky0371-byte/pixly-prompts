# 10 吊牌展示图

**版本：** v1.2
**最后更新：** 2026-03-28
**状态：** 测试中

## 当前模板

```
You are a product detail photographer creating a brand tag / care label display image.

REFERENCE IMAGES:
The brand tag front reference:
{reference_slot_7}

The care label / back tag reference:
{reference_slot_8}

OBJECTIVE:
Generate a clean, elegant display of the garment's brand tags and care labels. The text on the tags must be clearly legible.

COMPOSITION:
- Two-part layout:
  - Upper section: Brand tag / front label from {reference_slot_7} — showing brand name, logo, and key information
  - Lower section: Care label / back tag from {reference_slot_8} — showing material composition, washing instructions, size
- Both tags should be photographed as close-ups, filling their respective sections
- Tags can be shown slightly angled or on a subtle fabric background for context
- Clean margins between sections

SCENE & LIGHTING:
- Tags laid on a clean surface or shown with a hint of the garment fabric behind them
- Even, bright lighting — text must be razor-sharp and fully legible
- No shadows falling across text areas
- Soft, neutral background

PRODUCT FIDELITY — CRITICAL:
- The tag content MUST exactly match {reference_slot_7} and {reference_slot_8}
- ALL text, logos, symbols, and markings must be accurately reproduced
- Washing instruction symbols must be correct and legible
- COLOR ACCURACY: Tag background color, print color, logo color, and any fabric backing visible must exactly match the references. Do NOT whiten, brighten, or alter any color on the tags.
- Do NOT generate fake or generic tag content — replicate the exact tags shown in the references
- FINAL CHECK: Verify all colors and text match before outputting.
{sku_constraints_slot}

QUALITY:
- Text must be perfectly sharp and readable at standard viewing size
- Professional product detail photography
- Clean, trustworthy presentation
```

## 变量插槽说明

- `{reference_slot_7}` — 吊牌正面
- `{reference_slot_8}` — 吊牌反面
- `{sku_constraints_slot}` — SKU 差异约束
- ❌ 不接收补充说明

## CHANGELOG

- v1.0 (2026-03-28): 初版创建
- v1.1 (2026-03-28): 删除比例描述；素材引用改为 {reference_slot_X} 变量
- v1.2 (2026-03-28): 增加吊牌颜色精确还原约束；增加最终颜色检查（批量更新）

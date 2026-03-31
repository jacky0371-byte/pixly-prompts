# SKU 差异识别 — 通用框架

**版本：** v1.0
**最后更新：** 2026-03-28

## 说明

这是 SKU 识别的通用框架。各品类应继承此框架并扩展品类专属的检查项。

## 通用输出格式

```
For each identified feature, output ONE line in this format:
[AREA]: [precise description of the non-standard feature, including exact position]

If the product is entirely standard with no unusual features, output:
STANDARD — no high-risk structural deviations detected
```

## SKU 约束注入格式

分析结果注入到任务模板 `{sku_constraints_slot}` 时使用以下包装：

```
⚠️ SKU-SPECIFIC STRUCTURAL CONSTRAINTS — MUST FOLLOW EXACTLY:
The following features are CRITICAL and MUST appear exactly as described:

{sku_analysis_output}

FAILURE TO REPRODUCE THESE EXACT DETAILS WILL MAKE THE IMAGE UNUSABLE.
```

## CHANGELOG

- v1.0 (2026-03-28): 初版创建

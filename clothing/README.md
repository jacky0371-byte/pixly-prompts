# 服饰品类

## 素材槽位配置

| 槽位序号 | 素材名称 | 变量名 | 说明 |
|---------|---------|--------|------|
| 1 | 正面 | `{reference_slot_1}` | 服装正面整体图 |
| 2 | 背面 | `{reference_slot_2}` | 穿着状态背面图 |
| 3 | 平铺背面 | `{reference_slot_3}` | 平铺状态背面图 |
| 4 | 细节图 | `{reference_slot_4}` | 面料/工艺细节特写（wanx 支持最多4张）|
| 5 | 模特人脸图 | `{reference_slot_5}` | 模特/主播脸部参考 |
| 6 | 全身图 | `{reference_slot_6}` | 全身穿着参考 |
| 7 | 吊牌正面 | `{reference_slot_7}` | 吊牌第一面 |
| 8 | 吊牌反面 | `{reference_slot_8}` | 吊牌第二面 |

## 子类型列表

| 类型 | 修饰器目录 | 说明 |
|------|----------|------|
| 上装 | `modifiers/{model}/upper.md` | 衬衫、T恤、外套、针织等 |
| 下装 | `modifiers/{model}/lower.md` | 裤装、半裙等 |
| 套装/连衣裙 | `modifiers/{model}/suit.md` | 成套服装、连身裙等 |

## 任务清单

| 编号 | 任务名 | 引用槽位 | 接收补充 | 文件名 |
|------|--------|---------|---------|---------| 
| 01 | 正面主展示 | slot_1 + slot_5 | ✅ | `tasks/{model}/01-front-main.md` |
| 02 | 背面展示 | slot_2 + slot_5 | ❌ | `tasks/{model}/02-back-display.md` |
| 03 | 4/5轻侧展示 | slot_1 + slot_5 | ✅ | `tasks/{model}/03-side-display.md` |
| 04 | 全身展示 | slot_6 + slot_5 | ✅ | `tasks/{model}/04-full-body.md` |
| 05 | 肌理细节图 | slot_4（wanx最多4张）| ❌ | `tasks/{model}/05-texture-detail.md` |
| 06 | 矩阵氛围图(上半身) | slot_1 + slot_5 | ✅ | `tasks/{model}/06-matrix-upper.md` |
| 07 | 矩阵氛围图(全身) | slot_6 + slot_5 | ✅ | `tasks/{model}/07-matrix-full.md` |
| 08 | 细节模块(上1下2) | slot_1 + slot_4 | ❌ | `tasks/{model}/08-detail-module.md` |
| 09 | 平铺正反面 | slot_1 + slot_3 | ❌ | `tasks/{model}/09-flat-lay.md` |
| 10 | 吊牌展示图 | slot_7 + slot_8 | ❌ | `tasks/{model}/10-tag-display.md` |

`{model}` 替换为 `nano-banana` 或 `wanx`。

## SKU 分析器

| 模型 | 文件 | 调用方式 |
|------|------|---------|
| nano-banana | `sku-analyzer/nano-banana.md` | Gemini 图像理解 |
| wanx | `sku-analyzer/wanx.md` | 通义千问 VL |

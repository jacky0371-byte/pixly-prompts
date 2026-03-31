# 素材槽位映射表（全局参考）

不同品类的槽位配置可能不同，以下是通用框架。各品类的具体配置见其 README.md。

## 通用规范

- 变量格式：`{reference_slot_X}`，X 为槽位序号（从 1 开始）
- 系统拼装时将变量替换为用户上传的实际图片数据
- Gemini 收到的是文字 + 图片穿插排列的多模态输入
- 每个品类最多 8 个槽位

## 服饰品类槽位

| 序号 | 素材名称 | 变量 |
|------|---------|------|
| 1 | 正面 | `{reference_slot_1}` |
| 2 | 背面 | `{reference_slot_2}` |
| 3 | 平铺背面 | `{reference_slot_3}` |
| 4 | 细节图 | `{reference_slot_4}` |
| 5 | 模特人脸图 | `{reference_slot_5}` |
| 6 | 全身图 | `{reference_slot_6}` |
| 7 | 吊牌正面 | `{reference_slot_7}` |
| 8 | 吊牌反面 | `{reference_slot_8}` |

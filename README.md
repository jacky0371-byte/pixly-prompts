# Pixly Prompts

电商产品图 AI 批量生成工具 — Prompt 模板仓库

## 产品背景

Pixly 是一个面向中国电商卖家的 AI 产品图批量生成工具（Web 版）。用户上传商品素材照片，系统按预设的任务模板批量调用生图 API 生成一整套电商展示图。

本仓库存储所有品类的 Prompt 模板，用于与 Claude 协作进行持续调优。

## 已接入生图模型

| 模型标识 | 全称 | Prompt 语言 | 状态 |
|---------|------|------------|------|
| `nano-banana` | Google Gemini — Nano Banana 2（Imagen） | 英文 | 生产中 |
| `wanx` | 阿里通义万相 wan2.6-image | 中文 | 迁移中 |

新增模型时：在此表格添加一行，并在各品类目录下的 `tasks/`、`modifiers/`、`sku-analyzer/` 中新建对应的模型子目录或文件。

## 品类清单

| 品类 | 目录 | 状态 | 任务数 |
|------|------|------|--------|
| 服饰 | `clothing/` | ✅ 已完成 | 10 |
| 鞋靴箱包 | `footwear-bags/` | 🔲 待开发 | — |
| 3C电子产品 | `electronics/` | 🔲 待开发 | — |

## Prompt 架构

每个任务的最终 Prompt 由四层拼装：

```
Layer 1: 基础 Prompt 模板（本仓库管理）
    ↓
Layer 2: 子类型修饰器（如服饰的上装/下装/套装）
    ↓
Layer 3: SKU 差异约束（AI 识别商品结构差异，可选）
    ↓
Layer 4: 用户补充说明（追加到末尾，部分任务接收）
```

## 目录结构

```
pixly-prompts/
├── _shared/                        # 跨品类共享框架
│   ├── slot-mapping.md
│   └── sku-analyzer.md
├── clothing/                       # 服饰
│   ├── tasks/
│   │   ├── nano-banana/            # Gemini 版任务模板（英文）
│   │   │   ├── 01-front-main.md
│   │   │   └── ...
│   │   └── wanx/                   # 通义万相版任务模板（中文）
│   │       ├── 01-front-main.md
│   │       └── ...
│   ├── modifiers/
│   │   ├── nano-banana/            # Gemini 版修饰器（英文）
│   │   │   ├── upper.md
│   │   │   ├── lower.md
│   │   │   └── suit.md
│   │   └── wanx/                   # 通义万相版修饰器（中文）
│   │       ├── upper.md
│   │       ├── lower.md
│   │       └── suit.md
│   ├── sku-analyzer/
│   │   ├── nano-banana.md          # Gemini 版 SKU 分析（英文）
│   │   └── wanx.md                 # 通义千问 VL 版 SKU 分析（中文）
│   └── README.md
├── footwear-bags/                  # 鞋靴箱包（待开发）
├── electronics/                    # 3C电子（待开发）
└── README.md
```

## 变量规范

### 素材槽位变量

Prompt 中使用 `{reference_slot_X}` 引用用户上传的素材图片。系统拼装时会将变量替换为实际图片数据。各品类的具体槽位配置见各品类目录下的 `README.md`。

### 其他变量

| 变量 | 说明 |
|------|------|
| `{garment_type_composition}` | 子类型修饰器注入位置 |
| `{sku_constraints_slot}` | SKU 差异约束注入位置 |
| `{supplement_slot}` | 用户补充说明注入位置（仅部分任务有） |
| `{user_sku_note}` | 用户手动输入的 SKU 结构差异描述 |

### 注意事项

- 图片比例**不写在 Prompt 中**，由调用生图接口时的配置项传入
- nano-banana 模板使用**英文**；wanx 模板使用**中文**
- wanx 模板的 `negative_prompt` 单独存放在模板文件的"反向提示词"区块，代码侧独立传参
- wanx 调用时须设置 `prompt_extend: false`

## 仓库 Raw 基础地址

```
https://raw.githubusercontent.com/jacky0371-byte/pixly-prompts/main/
```

示例（获取 wanx 版正面主展示模板）：
```
https://raw.githubusercontent.com/jacky0371-byte/pixly-prompts/main/clothing/tasks/wanx/01-front-main.md
```

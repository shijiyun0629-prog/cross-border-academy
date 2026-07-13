# 📥 CSV 模板使用说明

## 一、为什么用 CSV 而不是 xlsx

- CSV 文件 Excel / Numbers / Google Sheets **都能直接打开**，兼容性最好
- Excel 里保存时选"CSV UTF-8"格式即可
- 网站的"批量导入"直接接受 CSV 粘贴，无需转换

---

## 二、字段说明

| 列名 | 必填 | 可选值 | 说明 |
|---|---|---|---|
| `category_id` | ✅ | `rules` / `research` / `content` / `ads` / `ops` | 内容归属分类，见下表 |
| `kind` | ✅ | `link` / `note` / `tool` | 内容类型 |
| `title` | ✅ | 任意文本 | 卡片标题 |
| `desc` | ✅ | 任意文本 | 一句话简介 |
| `tags` | ⬜ | 用英文逗号分隔 | 如 `冷启动,SOP,必读` |
| `channel` | ✅ | `TT` / `Amazon` / `独立站` / `通用` | 多渠道用逗号：`TT,Amazon` |
| `market` | ✅ | `跨境` / `本土` / `通用` | 品牌出海 / 本土店 / 都适用 |
| `url` | ⬜ | 完整 URL / 相对路径 / `#` | `#` 表示暂无链接（占位） |

### 分类 ID 速查表

| id | 名称 |
|---|---|
| `rules` | ① 平台规则 & 合规政策 |
| `research` | ② 市场调研 & 选品 |
| `content` | ③ 内容创作 & 达人合作 |
| `ads` | ④ 广告投放 (GMV Max / Spark Ads) |
| `ops` | ⑤ 运营 SOP & 冷启动 Playbook |

想新增分类？直接在 `index.html` 的 `DATA` 数组里加一个新 category 块（复制粘贴现有的，改 id + name + desc 即可）。

---

## 三、工作流

### 每天/每周新增 3–5 条：直接用网站表单
1. 双击 `index.html` 打开网站
2. 点右下角"➕ 添加内容"
3. 填完 → 生成 JSON → 一键复制 → 粘贴到 index.html 的对应位置

### 批量整理（一次加 10 条以上）：走 CSV
1. 打开 `content_template.csv`（Excel 会自动识别为表格）
2. 删掉示例行，或直接在下面继续加行
3. 保存为 CSV UTF-8
4. 打开 `index.html`，点右下角"➕"→ 切到"📥 CSV 批量导入"标签
5. 用 Excel 打开你的 CSV → 全选 → 复制 → 粘贴到网站的文本框
6. 点"生成 JSON" → 一键复制 → 粘贴到 index.html 的 DATA 数组

---

## 四、Excel 里的小技巧

**给 channel / market / kind 列加下拉验证：**
1. 选中 `channel` 列 → Data → Data Validation
2. Allow: List → Source: `TT,Amazon,独立站,通用`
3. `market` 列同理，Source: `跨境,本土,通用`
4. `kind` 列同理，Source: `link,note,tool`

这样以后填内容时不会拼错枚举值。

**颜色分类：** Home → Conditional Formatting → 按 `channel` 或 `market` 值高亮，一眼看出内容结构分布。

---

## 五、以后升级到 100+ 条内容时

那时候可以考虑：
- 把 CSV 挂到 **飞书多维表格** / **Notion 数据库**
- 网站启动时通过 API 拉数据（不再需要复制粘贴）
- 支持多人协作编辑

现在不需要考虑这一步。

# 跨境电商学习站 · 使用说明

一个单文件 HTML 学习资源库。双击 `index.html` 即可本地预览。

---

## 一、当前 V1 结构

```
学习网站/
├── index.html      # 主文件（页面 + 数据全在里面）
└── README.md       # 你正在看的这个说明
```

**5 个示例分类**（在 index.html 顶部的 `DATA` 数组里可修改）：
1. 平台规则 & 合规政策
2. 市场调研 & 选品
3. 内容创作 & 达人合作
4. 广告投放（GMV Max / Spark Ads）
5. 运营 SOP & 冷启动 Playbook

每个分类下有 3 种卡片类型：
- 🔗 **外链** (`kind: 'link'`) — 官方文档、工具、政策原文
- 📝 **知识笔记** (`kind: 'note'`) — 原创方法论、复盘、SOP
- 🛠 **工具/模板** (`kind: 'tool'`) — Checklist、Excel、报表模板

---

## 二、怎么加内容？

打开 `index.html`，找到 `const DATA = [` 这一段，按格式加：

```javascript
{
  kind: 'note',                          // 'link' | 'note' | 'tool'
  title: '标题（可包含 emoji）',
  desc:  '一句话简介，会出现在卡片上',
  tags:  ['标签1', '标签2', '标签3'],     // 用于搜索匹配
  url:   'https://...' 或 './xxx.pdf'    // 相对路径 / 绝对 URL / '#' 表示占位
}
```

想新增一个分类？复制现有 category 块，改 `id`、`name`、`desc`、`items` 即可。

**技巧：** 内部知识文档（如冷启动方法论）建议放在同目录下，然后 `url: './xxx.html'` 就能一键打开。

---

## 三、怎么上线？（未来公开发布时）

三选一，都是免费的：

### A. Vercel（最推荐 · 5 分钟）
1. 注册 [vercel.com](https://vercel.com)
2. `New Project` → 上传整个"学习网站"文件夹
3. 拿到 `https://xxx.vercel.app` 公开链接
4. 可绑定自己的域名

### B. GitHub Pages（0 元）
1. 把文件夹推到 GitHub 仓库
2. Settings → Pages → Deploy from branch → main
3. 拿到 `https://username.github.io/xxx`

### C. Netlify（拖拽即可）
1. 打开 [netlify.com](https://www.netlify.com/) drop 页
2. 直接把文件夹拖上去
3. 立刻拿到公开链接

---

## 四、后续升级方向（按需，别一次做全）

| 需求 | 现在的做法 | 未来升级 |
|---|---|---|
| 搜索 | 已内建（关键词过滤） | 加 Algolia 全文检索 |
| 更新内容 | 手改 HTML 里的 JSON | 迁移到 Notion / Airtable 作为后端 |
| 多人协作编辑 | 无 | 迁移到 Notion 公开页 or Docusaurus |
| 阅读统计 | 无 | 加 Google Analytics / Plausible |
| 用户登录 | 无 | 换 Next.js + Supabase |

**建议节奏：** 先把内容填满，再考虑升级技术。80% 的价值来自内容本身，不是花哨的框架。

---

## 五、内容填充优先级建议

阶段 1（这周）：把现有 5 个分类的示例卡片改成真实资源
阶段 2（本月）：把 `品牌案例/papatui/00_知识库_TTS冷启动方法论.md` 转 HTML 挂进来
阶段 3（Q3）：加"案例复盘"新板块，接入 papatui / Henkel 真实项目沉淀
阶段 4（Q4）：内容量到 50+ 条时，考虑上线公开域名

---
name: decode-book
description: 把 resource/ 下的 PDF 书转成 base.md 并拆分为知识点，供 learn 使用。用户要解码、转换、拆解一本书时触发。
---

# decode-book

把 `resource/` 下的一本 PDF 书转成 `knowledge/books/<书名>/base.md`，并将内容拆分为一个个知识点。

## 步骤

1. **定位原书**：在 `resource/` 下按 `<书名>` 匹配 PDF（支持片段匹配）。命中多个时列出让用户选；一个都找不到就停下，请用户先把 PDF 放进 `resource/`。
2. **抽取文本**：用 Python（`pdfplumber` 或 `pypdf`）抽取全书文本；扫描版 PDF 需 OCR 时改用 `pdf2image` + `pytesseract`。
3. **写 base.md**：建目录 `knowledge/books/<书名>/`，把整理后的全文写入 `base.md`。
4. **拆分知识点**：把内容拆成若干自包含的知识点，每节以 `## <序号>. <标题>` 开头：
   - 一个知识点 = 一个可独立学习的核心概念或论点。
   - 标题是一句陈述该点结论的话（不是「第一章」这类位置标题）。
   - 正文保留原文关键内容；可提炼，但不引入书中没有的观点。

## 完成标准

`base.md` 存在，含 N≥1 个 `##` 分节；每节标题是一句可判断对错的陈述，正文自包含；序号从 1 连续。

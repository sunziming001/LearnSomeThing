# AGENTS.md

这是一个基于 **ICAP** 学习框架的自学工作区：把 `resource/` 下的 PDF 书转成结构化知识点，再逐个按 ICAP（Passive → Active → Constructive）学习并沉淀笔记。

## 目录约定

- `resource/` — 存放 PDF 原书。
- `knowledge/books/<书名>/` — 一本书的全部学习数据：
  - `base.md` — 全书结构化文本，按知识点分节。
  - `note.md` — 学习笔记，`learn` 累加写入。
  - `progress.md` — 学习进度，`learn` 据此续学。

## 技能

- `/decode-book <书名>` — 把 PDF 转成 `base.md` 并拆分为知识点。用户要「解码 / 转换 / 拆解」一本书时用。
- `/learn <书名>` — 按 ICAP 逐个知识点学习并记录笔记。用户要「学习 / 继续学 / 复习」一本书时用。

流程：先 `decode-book`，再 `learn`。

# ochiai-paper-summary

Claude Code / Cursor 向けの **落合フォーマット（6問）論文要約** スキル。

学術論文を A4 一枚程度の短文で、次の6問に答える形にまとめます。

1. どんなもの？
2. 先行研究と比べてどこがすごい？
3. 技術や手法のキモはどこ？
4. どうやって有効だと検証した？
5. 議論はあるか？
6. 次に読むべき論文はあるか？

> **非公式です。** フォーマットの着想は落合陽一氏の SlideShare
> [先端技術とメディア表現1 #FTMA15](https://www.slideshare.net/slideshow/1-ftma15/47697911)
> （およそ65ページ付近）にあります。本リポジトリは落合氏・所属機関とは無関係です。

## 入れ方

```bash
git clone https://github.com/uzuraDev/ochiai-paper-summary.git
cd ochiai-paper-summary
```

```bash
# Claude Code（個人）
cp -R skills/ochiai-paper-summary ~/.claude/skills/

# Claude Code（プロジェクト）
cp -R skills/ochiai-paper-summary .claude/skills/

# Cursor（プロジェクト）
cp -R skills/ochiai-paper-summary .cursor/skills/
```

リポジトリ直下の `.claude/skills/` / `.cursor/skills/` をそのまま使っても構いません。

## 使い方

論文（PDF / URL / テキスト）を渡して「落合フォーマットで要約して」と指示するか、Claude Code では `/ochiai-paper-summary` を使います。

出力テンプレ: `skills/ochiai-paper-summary/assets/template.md`

## License

MIT（`LICENSE`）— Copyright (c) 2026 uzuraDev

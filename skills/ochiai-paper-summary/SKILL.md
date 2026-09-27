---
name: ochiai-paper-summary
description: >-
  Use when summarizing an academic paper (PDF, arXiv URL/ID, DOI, or pasted
  abstract+sections) into Yoichi Ochiai’s six-question A4-style format
  (落合フォーマット). Also use for 「論文要約」「落合フォーマット」「Ochiai
  format」「6問でまとめて」 requests in Claude Code or Cursor.
license: MIT
compatibility: Claude Code, Cursor Agent Skills (agentskills.io)
metadata:
  author: muu-kuro
  language: ja
  attribution: Yoichi Ochiai #FTMA15 SlideShare (format inspiration; not affiliated)
---

# 落合フォーマット論文要約

学術論文を **A4一枚程度** の短文で、次の6問に答える形で要約する。

フォーマットの出典アイデアは、落合陽一氏のスライド
[先端技術とメディア表現1 #FTMA15](https://www.slideshare.net/slideshow/1-ftma15/47697911)
（およそ65ページ付近）で示された読み方。本スキルは非公式の再実装であり、落合氏や所属機関の公式物ではない。

## いつ使うか

- ユーザーが論文PDF・arXiv・DOI・本文抜粋を渡し、「要約して」「落合フォーマットで」と言ったとき
- サーベイ用に複数本を同じ型で並べたいとき

## 入力の扱い

1. **入手**: URL/arXiv ID/DOIなら取得またはユーザー提供PDFを読む。アクセスできない場合は止まって理由を伝える。
2. **精読の優先順**: Abstract → Introduction → Method/Approach → Experiments/Results → Discussion/Limitations → Conclusion → 重要そうな関連研究。図表キャプションも見る。
3. **根拠**: 各問の主張は論文中の根拠（節・図表番号）に紐づける。推測は「推測:」と明示する。分からないことは書かない。
4. **言語**: ユーザーの指定がなければ **日本語**。用語・手法名は必要なら英語を併記。
5. **分量**: 全体でA4一枚相当（目安 800〜1500字）。各問は2〜5文。箇条書き可。冗長な引用の羅列はしない。

## 出力フォーマット（必須）

次の見出し順を守る。`assets/template.md` と同じ構造。

```markdown
# {論文タイトル（省略禁止）}

- 著者: {First Author et al.}（著者が少ない場合は全員）
- 年 / 会場またはジャーナル: {YYYY} / {venue}
- 識別子: [{arXiv|DOI|URL}]({link})
- 一言: {この論文を一文で}

## 1. どんなもの？
（問題設定・提案の概要・誰向けか）

## 2. 先行研究と比べてどこがすごい？
（差分・新規性。比較対象を具体名で）

## 3. 技術や手法のキモはどこ？
（コアアイデア・アルゴリズム・アーキテクチャ。実装細部の羅列は避け、本質）

## 4. どうやって有効だと検証した？
（データ・ベースライン・指標・主な数値結果。過大解釈しない）

## 5. 議論はあるか？
（limitation・前提・失敗ケース・倫理・再現性など。論文が触れていなければ「論文内に明示的な議論は薄い」と書く）

## 6. 次に読むべき論文はあるか？
（本文・関連研究から **2〜5本**。可能ならタイトルと理由。リンクがあれば付ける）
```

## 品質チェック（出力前）

- [ ] タイトルが省略されていない
- [ ] 6見出しがすべて埋まっている（空欄禁止。不明なら「論文からは判断できない」）
- [ ] 数値・主張に根拠がある（または推測ラベル）
- [ ] 宣伝調・過度な賛辞になっていない
- [ ] 著作権: 長文の verbatim 引用を避け、言い換え中心。図の再配布はしない（必要なら「図N参照」のみ）

## 複数論文

1本ずつ上記フォーマットで出力し、最後に任意で「横断メモ」（共通テーマ・対立点）を短く付けてよい。

## やってはいけないこと

- 読んでもいない節について断定する
- 落合氏・大学・研究室の公式スキルだと名乗ること
- 論文本文の大幅な逐語転載

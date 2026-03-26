# Mado Open

**問いを投げたときだけ世界が動く、ミニマル実装の物語観測フレームワーク。**
*A minimal-implementation, on-demand world observation framework for LLM-based narrative.*

---

## これは何？ / What is this?

Mado Open は、LLMを使ったキャラクター小説のための軽量フレームワークです。
フルタイムのワールドシミュレータではありません。
「窓を開ける」（問いかける）たびに、LLMがその瞬間だけ世界をレンダリングします。

*Mado Open is a lightweight framework for LLM-based character fiction.
It's not a full-time world simulator — lazy narrative evaluation.
The world only renders when you "open a window."*

**特徴 / Features:**
- キャラクターの「矛盾（wants → but）」が物語を生む / Characters defined by contradiction
- テーマは観測ごとに30度回転＋感覚チャンネル循環 / Theme rotates 30° with sensory channel cycling
- DBもRAGも不要。STATEブロックに全状態を保持 / No DB, no RAG. All state in plain text
- 観測と観測の間に因果を書かない。でも世界はそこにいる / No causality written between observations. The world was always there.

---

## 2つの使い方 / Two Modes

| | テンプレート版 / Standalone | Claude Code 版 / Claude Code |
|--|--|--|
| 必要なもの | LLMだけ | Claude Code + git |
| 永続性 | コピペで継続 | ファイルに自動保存 |
| 対象 | 手軽に試したい | 長期的に世界を育てたい |

---

## クイックスタート / Quick Start

### テンプレート版 / Standalone

1. [`mado_open.md`](./mado_open.md) をダウンロード
2. 内容を丸ごと新規LLMチャットに貼り付ける
3. インタビューに答える → 物語が生成される
4. 末尾の次回テンプレートを新規チャットに貼る → 繰り返す

> 💡 英語でも使えます。[WINDOW] や回答を英語で書けばLLMは英語で出力します。
> *Works in English: write [WINDOW] and answers in English, LLM responds in English.*

### Claude Code 版 / Claude Code Mode

→ [`claude_code_setup.md`](./claude_code_setup.md) を参照

---

## 動作確認済みLLM / Compatible LLMs

Claude Sonnet/Opus, ChatGPT-4o, Gemini 1.5 Pro 以上を推奨。
*Recommended: Claude Sonnet/Opus, ChatGPT-4o, Gemini 1.5 Pro or better.*

---

## ライセンス / License

MIT License © 2026 mizukiamano099-ops

自由に使用・改変・再配布できます。商用利用も可。著作権表示を残してください。
*Free to use, modify, and redistribute, including commercially. Keep the copyright notice.*

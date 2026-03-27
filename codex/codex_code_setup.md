# Mado Open ── Codex セットアップガイド

> テンプレート1枚（`MadoOpen.md`）だけでも動きますが、
> Codex を使うと**世界が消えません**。
> 状態がファイルに保存され、git で全履歴が残ります。

---

## テンプレート版 vs Codex 版

| 観点 | テンプレート版 | Codex 版 |
|------|--------------|----------------|
| 必要なもの | LLMだけ | Codex + git |
| 永続性 | チャット間でコピペが必要 | ファイルに自動保存 |
| 監査性 | なし | git で全履歴が残る |
| 世界の安定性 | LLMの性能・文脈長に依存 | ファイルが真実の源泉 |
| 複数世界 | テンプレートを複数管理 | リポジトリで分離 |

---

## 必要なもの

- Codex 実行環境
- git

---

## セットアップ手順

### 1. リポジトリを作成する

```bash
mkdir my-mado-world
cd my-mado-world
git init
```

### 2. AGENTS.md を作成する

このリポジトリに同梱の `AGENTS.md` をそのまま利用する。
（新規作成する場合は `claude_code_setup.md` の `CLAUDE.md` 内容を `AGENTS.md` として配置する。）

---

### 3. ディレクトリを作成する

```bash
mkdir -p world characters/main_cast characters/npcs state observations
```

### 4. state/current.md を初期化する

```bash
cat > state/current.md << 'EOF_STATE'
# STATE — 現在の世界状態
> このファイルは観測のたびに更新される。手動編集は最小限。
---
OBS:0
EOF_STATE
```

### 5. 補助ファイルを作成する

```bash
cat > state/history.md << 'EOF_HISTORY'
# STATE HISTORY

EOF_HISTORY

cat > state/seeds.md << 'EOF_SEEDS'
# THEME SEEDS

EOF_SEEDS

cat > world/definition.md << 'EOF_DEF'
# WORLD DEFINITION

- 舞台:
- 世界の問い:
- 空気感:
- 制約:
EOF_DEF

cat > world/timeline.md << 'EOF_TL'
# WORLD TIMELINE

EOF_TL

cat > world/events.md << 'EOF_EVENTS'
# WORLD EVENTS

EOF_EVENTS
```

### 6. 最初のコミットをする

```bash
git add .
git commit -m "init: codex mado world setup"
```

### 7. Codex セッションを開始する

プロジェクトフォルダで Codex を起動し、以下のように話しかける：

```
世界を立ち上げよう
```

Codex がインタビューを開始し、世界定義・キャラクター・初回観測の準備に進めます。

---

## 日常の使い方

**窓を開ける（物語を生成する）：**
```
開けよう
城崎修のPOVで開けよう
土曜の朝、鳴海が来る場面で
```

**[WINDOW] で詳細指定：**
```
[WINDOW]
誰のPOVで：長谷水緒の一人称で
いつ：水曜の夜
どんな場面：閉店間際に一人残っている
```

---

## 備考

- 観測ごとに `git commit & push` を行う運用を推奨
- 世界を複数持つ場合：リポジトリを分けることを推奨
- NPC が3回登場するとメインキャスト昇格の提案を推奨
- 英語での利用：[WINDOW] や会話を英語で書けば英語で出力されます

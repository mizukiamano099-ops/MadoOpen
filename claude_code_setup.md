# Mado Open ── Claude Code セットアップガイド

> テンプレート1枚（`mado_open.md`）だけでも動きますが、
> Claude Code を使うと**世界が消えません**。
> 状態がファイルに保存され、git で全履歴が残ります。

---

## テンプレート版 vs Claude Code 版

| 観点 | テンプレート版 | Claude Code 版 |
|------|--------------|----------------|
| 必要なもの | LLMだけ | Claude Code + git |
| 永続性 | チャット間でコピペが必要 | ファイルに自動保存 |
| 監査性 | なし | git で全履歴が残る |
| 世界の安定性 | LLMの性能・文脈長に依存 | ファイルが真実の源泉 |
| 複数世界 | テンプレートを複数管理 | リポジトリで分離 |

---

## 必要なもの

- [Claude Code](https://claude.ai/code)（CLIまたはIDE拡張）
- git

---

## セットアップ手順

### 1. リポジトリを作成する

```bash
mkdir my-mado-world
cd my-mado-world
git init
```

### 2. CLAUDE.md を作成する

以下の内容をそのままコピーして `CLAUDE.md` として保存する：

---

```markdown
# Mado ── オンデマンド世界観測フレームワーク

## あなたの役割
あなたは「窓の管理人」です。
- ユーザーが「窓を開ける」（問いかける）たびに、世界の断面を物語として描写する
- 窓を閉じたら、世界の状態を静かに更新する
- 窓と窓の間に何が起きたかは書かない。でも世界はそこにいる

## セッション開始時の必須読み込み
`state/current.md` を必ず読む。`OBS:0` なら世界立ち上げから始める。

## 窓を開ける手順
1. `state/current.md` を読む
2. 関連するキャラクターファイルを読む（今回必要な人だけ）
3. `world/definition.md` を読む
4. 観測条件を決める（WHO / WHEN / WHERE / WHAT / MODE）
5. 物語を生成し `observations/obs_NNN/draft.md` に保存する
6. `observations/obs_NNN/query.md` と `context.md` も保存する

## 窓を閉じる手順
1. `state/current.md` を更新する（OBS / REL / VEC / SEED_CH / SEED / MEMO）
2. テーマ回転：本文最後の一文から約30度右回りで次のSEEDを生成し、SEED_CHも回転する
3. `world/timeline.md` を進める
4. `state/history.md` の先頭に1行追記する
5. git commit & push する

## STATE フォーマット（state/current.md）

OBS:{観測番号}
WORLD_CLOCK:{世界内日時}|{季節・天候}
WORLD_Q:{世界の問い}
WORLD_ATM:{空気感（静けさ/密度）}|{色}|{音}|{匂い}
WORLD_CON:{物理的制約}|{社会的制約}|{心理的制約}
TONE:{全体トーン}
STAGE:{舞台}
CHAR:{コード}|{名前}|{年齢・立場}|{特徴}|wants:{欲望}→but:{矛盾}|{口調}
REL:{A}>{B}|{好意0-9},{緊張0-9},{理解0-9},{距離0-9}|{方向メモ}
VEC:{コード}|{内的方向（一文）}
SEED_CH:{触覚/聴覚/視覚/嗅覚/味覚}
SEED:{テーマシード（140字）}
MEMO:{前回の引き継ぎ（2-3行）}

## ディレクトリ構成
world/           世界定義（definition.md / timeline.md / events.md）
characters/      キャラクター（main_cast/ / npcs/）
state/           世界状態（current.md / history.md / seeds.md）
observations/    観測記録（obs_NNN/）

## キャラクターの必須要素
矛盾（wants → but）が最重要。これがないと物語が生まれない。
口調定義に厳密に従う。

## 禁止事項
- 窓を開けていないときに物語を生成しない
- state/ の手動編集をユーザーに提案しない（自動更新のみ）
- engines/ や templates/ のファイルを編集しない
```

---

### 3. ディレクトリを作成する

```bash
mkdir -p world characters/main_cast characters/npcs state observations
```

### 4. state/current.md を初期化する

```bash
cat > state/current.md << 'EOF'
# STATE — 現在の世界状態
> このファイルは観測のたびに自動更新される。手動編集しない。
---
OBS:0
EOF
```

### 5. 最初のコミットをする

```bash
git add .
git commit -m "init: Mado world setup"
```

### 6. Claude Code を起動する

プロジェクトフォルダで Claude Code を起動し、以下のように話しかける：

```
世界を立ち上げよう
```

Claude Code がインタビューを開始します。回答すると世界の定義ファイルが生成され、最初の観測の準備が整います。

---

## 日常の使い方

**窓を開ける（物語を生成する）：**
```
開けよう
城崎修のPOVで開けよう
土曜の朝、鳴海が来る場面で
```

**文体を指定して開ける：**
```
米澤穂信スタイルのPOVキャラで開けよう
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

- 観測ごとに `git commit & push` が自動で行われます
- 世界を複数持つ場合：リポジトリを分けることを推奨
- NPC が3回登場するとメインキャスト昇格の提案が出ます
- 英語での利用：[WINDOW] や会話を英語で書けば英語で出力されます
```

---

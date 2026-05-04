# melsec-iqr-device-skill

三菱電機 **MELSEC iQ-R** シリーズのデバイス知識を [Claude Code](https://docs.claude.com/claude-code) の Skill として提供するリポジトリです。デバイス選定・命名規則・パラメータ設定・CPU 機種間の移植など、iQ-R デバイスに関する問い合わせに対応します。

## 提供する Skill

本リポジトリには 2 つの Skill が含まれます。両 Skill は対になっており、**概念的な質問は overview**、**定量的な仕様の質問は specifications** を参照する設計です。

| Skill | 役割 |
|------|------|
| [melsec-iqr-device-overview](skills/melsec-iqr-device-overview/SKILL.md) | デバイス分類体系・命名規則・グローバル/ローカル区分・ラッチ・インデックス修飾・間接指定・デバイス点数設定・CPU 機種ごとの差異・バックアップ/リストア／トラッキング転送対象判定など、**横断的・概念的な知識** |
| [melsec-iqr-device-specifications](skills/melsec-iqr-device-specifications/SKILL.md) | X/Y/M/D/T/C/SM/SD/Jn\X/Un\G/Z/LZ/R/ZR/RD/P/I/SA\X など各デバイスの **詳細仕様**（記号・種別・デフォルト点数・最大使用範囲・設定単位・表記基数・用途・注意事項・バックアップ／トラッキング可否） |

## ディレクトリ構成

```
iqr-device-skill/
├── skills/
│   ├── melsec-iqr-device-overview/
│   │   └── SKILL.md
│   └── melsec-iqr-device-specifications/
│       ├── SKILL.md
│       └── references/
│           ├── user-devices.md
│           ├── system-devices.md
│           ├── link-direct-devices.md
│           ├── unit-access-devices.md
│           ├── index-and-file-registers.md
│           ├── pointers-and-others.md
│           └── safety-devices.md
└── LICENSE
```

## インストール方法

### 方法 A: フォルダをコピーする（推奨）

`skills/` 配下の各スキルフォルダを、Claude Code の skills ディレクトリにコピーします。

- ユーザースコープ（全プロジェクトで使用）: `~/.claude/skills/`
- プロジェクトスコープ（特定プロジェクトのみ）: `<プロジェクトルート>/.claude/skills/`

例（macOS / Linux）:

```bash
cp -r skills/melsec-iqr-device-overview ~/.claude/skills/
cp -r skills/melsec-iqr-device-specifications ~/.claude/skills/
```

例（Windows PowerShell）:

```powershell
Copy-Item -Recurse skills\melsec-iqr-device-overview $HOME\.claude\skills\
Copy-Item -Recurse skills\melsec-iqr-device-specifications $HOME\.claude\skills\
```

### 方法 B: claude.ai にアップロードする（ブラウザ／デスクトップ／モバイル）

各スキルフォルダを ZIP 圧縮し、拡張子を `.skill` に変更することで Anthropic 公式の **skill-creator 仕様** に準拠したパッケージとして利用できます。Claude Code 以外でも、以下の環境にアップロードして Skill として利用できます。

- [claude.ai](https://claude.ai)（ブラウザ版）
- Claude デスクトップアプリ
- Claude モバイルアプリ

手順（claude.ai の場合）:

1. 設定 → **Capabilities** → **Skills** を開く
2. 「Upload skill」から `.skill` ファイルをアップロード
3. アップロード後、対象の話題が会話に出ると Claude が自動的に Skill を呼び出す

> UI の名称や配置は変更されることがあります。最新の手順は [Anthropic 公式ドキュメント](https://docs.claude.com/) を参照してください。

## 使い方

インストール後、Claude Code を起動して質問するだけです。Skill のフロントマター（`description`）に書かれたトリガに合致する話題を Claude が検出すると、自動的に Skill の本文を読み込んで回答に反映します。

質問例:

- 「iQ-R の D デバイスのデフォルト点数と最大点数を教えて」
- 「ラッチリレー L とラッチ設定した M はどう違う？」
- 「Un\G の指定方法と Jn\X との使い分けを説明して」
- 「R04CPU から R08CPU に移植するときに注意するデバイスは？」
- 「SM400 と SM402 の違いは？」

## 出典

三菱電機 MELSEC iQ-R シリーズ各種マニュアル（ユーザーズマニュアル、CPU ユニット ユーザーズマニュアル 応用編、プログラミングマニュアル）

最新かつ正確な情報は必ず公式マニュアルを確認してください。

## 注意事項

- 本リポジトリは **三菱電機株式会社 とは無関係の非公式プロジェクト** です。
- 「MELSEC」「iQ-R」「GX Works3」などは三菱電機株式会社の商標または登録商標です。
- 本 Skill が出力する情報は参考用途であり、安全関連の設計・運用判断は必ず公式マニュアルおよび有資格者による確認に基づいて行ってください。
- LLM の特性上、生成される回答に誤りが含まれる可能性があります。実機適用前にレビューしてください。

## ライセンス

[MIT License](LICENSE) — Copyright (c) 2026 mokouliszt

## コントリビューション

誤りの指摘・追記提案は Issue / Pull Request で歓迎します。

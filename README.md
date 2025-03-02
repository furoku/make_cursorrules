# Cursor Rules for Claude

Cursor IDEでの開発を効率化するためのClaude/Claude Projects用設定ファイルとガイドラインのコレクションです。

## 概要

このリポジトリには、Cursor IDEの挙動を最適化するための各種設定ファイルとガイドラインが含まれています：

- `User Rules` - グローバルなAI制御ルール
- `.cursorrules` - プロジェクト固有の設定ファイル
- `.cursor/rules/*.mdc` - プロジェクト固有のルールファイル
- スタイルガイドとプルリクエスト規約

Cursorは、Anthropic Claude-3などの高性能AIモデルと連携して開発を支援するIDEです。このリポジトリの設定とガイドラインを活用することで、CursorのAI支援機能をより効果的に利用できます。

## ディレクトリ構成

```
.
├── .cursorrules                    # プロジェクトのメイン設定ファイル
├── .gemini/                        # 開発ガイドライン
│   └── styleguide.md              # コーディングスタイルガイド
├── claude projectの設定ファイル/    # Claude Projects用設定ファイル
│   ├── 00_インストラクションに設定.md     # 基本動作の設定
│   ├── 11_ナレッジに設定_cursorrulesファイルのチートシート.md
│   ├── 12_ナレッジに設定_cursor_rules配下ファイル用のチートシート.md
│   ├── 13_ナレッジに設定_User Rules（旧 "Rules for AI"）のチートシート.md
│   └── 14_プルリクエスト規約.md
└── README.md                      # このファイル
```

## 使い方

1. このリポジトリをCloneまたはダウンロード
2. Claude Projectsの設定：
   - `00_インストラクションに設定.md`をInstructionsに設定
   - 各チートシートをKnowledgeにアップロード
3. 各ガイドラインを参照しながら、プロジェクトに適した設定を作成
4. 作成した設定をCursorに適用して、AIの効率的な支援を受ける

## 貢献方法

プルリクエストや改善提案を歓迎します。貢献する際は`14_プルリクエスト規約.md`を参照してください。

## ライセンス

MITライセンス 
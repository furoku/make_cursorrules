# Cursor Rules for Claude

Cursor IDEの挙動制御に必要なルールを作るためのClaude Projects向けの設定ファイルです。

## 概要

本リポジトリには、Cursor IDE の挙動を制御するための、`User Rules`、`.cursorrules` ファイル、さらに `.cursor/rules` フォルダ内に配置される mdc ファイルの作成および活用を支援する、Claude Projects 向けのインストラクションとナレッジファイルが収められています。

Cursor は、Anthropic Claude-3.7-sonnet などの高性能 AI モデルと連携しながら、優れた AI 機能を発揮して開発支援を行う IDE です。なお、高度な AI 制御を実現するためには、上記の `User Rules`、`.cursorrules` ファイル、及び `.cursor/rules` フォルダ内の mdc ファイルの適切な活用が不可欠となります。

本リポジトリの設定を Claude Projects に適用することで、Cursor の AI 支援機能をより効果的に引き出すルールファイルが作成できるとの期待のもと公開しています。

## 含まれるファイル

- `instructions.md` - Claude Projectsのインストラクションに設定。基本的な動作。
- `project_knowledge/` - Claude ProjectsのKnowledgeにアップロード、または「Add text contents」で設定。
  - `Cusrorの .cursor_rulesフォルダ チートシート.md` - `.cursor/rules`の配下のmdcファイルの書き方
  - `Cursorの .cursorrulesファイル チートシート.md` - `.cursorrules`ファイルの書き方
  - `User Rules（旧 "Rules for AI"）チートシート.md` - グローバルなAIルールの書き方
  - `プルリクエスト規約` - nishina555 さんのリポジトリを参照

## 使い方

1. このリポジトリをCloneまたはダウンロード
2. 各ファイルを参照しながら、プロジェクトに適したルールを作成
3. 作成したルールをClaudeに適用して、AIの効率的な支援を受ける

## 貢献方法

プルリクエストや改善提案を歓迎します。

## ライセンス

MITライセンス 
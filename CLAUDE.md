# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## プロジェクト概要

日本語出力向けに設定された Sphinx ドキュメントプロジェクト。ドキュメントは reStructuredText (RST) 形式で記述され、Mermaid 図（フローチャート・シーケンス図・クラス図）を含みます。

## ビルドコマンド

すべてのコマンドは `docs/` ディレクトリから実行します。

```bash
make html     # HTML ドキュメントをビルド → docs/build/html/
make epub     # ePub をビルド
make latex    # LaTeX をビルド
make clean    # ビルド成果物を削除
```

仮想環境は `.venv/` にあります。`make` 以外のコマンドを実行する場合は `source .venv/bin/activate` で有効化してください。

## アーキテクチャ

ドキュメントは `docs/source/` 以下の **Markdown (.md)** ファイルで構成されます。`index.md` の `toctree` がページ順序を定義しており、新規ページを追加する際は `.md` ファイル作成と `toctree` への登録の両方が必要です。

現在のページ構成: `requirements` → `basic_design` → `detailed_design`

## Sphinx 設定（conf.py）

- `language = 'ja'`（日本語出力）
- テーマ: alabaster
- 拡張機能: `myst_parser`（Markdown サポート）、`sphinxcontrib.mermaid`（Mermaid 図）、`sphinx_needs`（要件管理）

## Mermaid 図の記法

Markdown ファイル内での Mermaid 埋め込み構文（MyST-Parser のディレクティブ記法）:

````markdown
```{mermaid}
graph TD
    A[開始] --> B[終了]
```
````

対応図種: フローチャート (`graph TD`)、シーケンス図 (`sequenceDiagram`)、クラス図 (`classDiagram`)

## sphinx-needs の記法

needs（要件・仕様・テストケースなど）の定義:

````markdown
```{req} タイトル
:id: REQ_001
:status: open
:tags: 認証

本文（要件の説明）。
```
````

主なディレクティブ: `{req}`（要件）、`{spec}`（仕様）、`{test}`（テストケース）

needs 一覧テーブルの表示:

````markdown
```{needtable}
:filter: type == "req"
:columns: id, title, status, tags
```
````

needs 間リンク（例: テストケースが要件を検証する）は `:links: REQ_001` オプションで指定します。

## Pharaoh テストレポート

`pharaoh-report/` に Pharaoh プロジェクトが初期化済み。設定ファイルは `pharaoh-report/pharaoh.yaml`。

```bash
# コンポーネント（テスト結果セット）の追加
pharaoh -p pharaoh-report add -n <name> -t <template>

# アセット生成 → レポートビルド
pharaoh -p pharaoh-report generate build
```

**重要**: Pharaoh はプロジェクトルートとして空ディレクトリまたは既存の pharaoh プロジェクトのみ受け付けるため、専用の `pharaoh-report/` サブディレクトリで運用します（リポジトリルート直下では初期化不可）。

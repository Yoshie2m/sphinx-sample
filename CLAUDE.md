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

ドキュメントは `docs/source/` 以下の RST ファイルで構成されます。`index.rst` の `toctree` がページ順序を定義しており、新規ページを追加する際は `.rst` ファイル作成と `toctree` への登録の両方が必要です。

現在のページ構成: `requirements` → `basic_design` → `detailed_design`

## Sphinx 設定（conf.py）

- `language = 'ja'`（日本語出力）
- テーマ: alabaster
- **重要**: `sphinxcontrib-mermaid` は `.venv/` にインストール済みですが、`conf.py` の `extensions` リストへの登録が必要です。`.. mermaid::` ディレクティブを動作させるには以下を追加してください:

```python
extensions = ['sphinxcontrib.mermaid']
```

## Mermaid 図の記法

RST ファイル内での Mermaid 埋め込み構文:

```rst
.. mermaid::

   graph TD
       A[開始] --> B[終了]
```

対応図種: フローチャート (`graph TD`)、シーケンス図 (`sequenceDiagram`)、クラス図 (`classDiagram`)

# Strictness Mode

## モード判定

`pharaoh.toml` が存在し `require_change_analysis = true` の場合は**強制モード**、それ以外は**アドバイザリーモード**。

## 強制モード

`.pharaoh/session.json` を読み込み、影響する各 need ID の `changes.<id>.acknowledged` が `true` であることを確認する。未承認の need が存在する場合は処理をブロックする。

## アドバイザリーモード

処理を実行する。完了後、変更分析が未実施であればヒントを一度だけ表示する。

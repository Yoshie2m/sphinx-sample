# Requirements

要件定義書の内容をここに記述します。

```{mermaid}
graph TD
    A[開始] --> B{判断}
    B -->|はい| C[処理1]
    B -->|いいえ| D[処理2]
    C --> E[終了]
    D --> E
```

## 要件一覧

```{req} ユーザーログイン機能
:id: REQ_001
:status: open
:tags: 認証

ユーザーはメールアドレスとパスワードでログインできること。
```

```{req} 管理者によるユーザー管理
:id: REQ_002
:status: open
:tags: 管理

管理者はユーザーの追加・削除・権限変更を行えること。
```

## 要件テーブル

```{needtable}
:filter: type == "req"
:columns: id, title, status, tags
```

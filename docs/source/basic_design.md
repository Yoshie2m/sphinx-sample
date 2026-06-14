# Basic Design

基本設計書の内容をここに記述します。

```{mermaid}
sequenceDiagram
    participant User
    participant System
    User->>System: リクエスト送信
    System-->>User: レスポンス返却
```

## 設計一覧

```{spec} ログイン機能設計
:id: SPEC_001
:status: open
:tags: 認証
:links: REQ_001

システムはメールアドレスとパスワードを受け取り、認証処理を行ってセッショントークンを発行しなければならない。
```

```{spec} ユーザー管理機能設計
:id: SPEC_002
:status: open
:tags: 管理
:links: REQ_002

システムは管理者権限を持つユーザーのみがユーザーの追加・削除・権限変更を実行できるインターフェースを提供しなければならない。
```

```{needtable}
:filter: type == "spec"
:columns: id, title, status, tags, links
```

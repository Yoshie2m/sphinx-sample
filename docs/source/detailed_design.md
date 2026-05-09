# Detailed Design

詳細設計書の内容をここに記述します。

```{mermaid}
classDiagram
    class User {
        +String name
        +String email
        +login()
        +logout()
    }
    class Admin {
        +manageUsers()
    }
    User <|-- Admin
```

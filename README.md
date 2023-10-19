```mermaid
sequenceDiagram
    participant LocalPC as "Spring Boot (ローカルPC)"
    participant DBContainer as "コンテナのDB"

    LocalPC->>DBContainer: 接続

    activate LocalPC
    LocalPC->>+DBContainer: POST \HTTP: EC2_IP:3307
    Note over DBContainer: データベース操作を実行
    deactivate LocalPC
    Note over DBContainer: データベースで応答
    DBContainer-->>-LocalPC: 応答
```
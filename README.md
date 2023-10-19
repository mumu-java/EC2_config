
sequenceDiagram
    participant LocalPC as "Spring Boot (Local PC)"
    participant EC2Instance as "EC2 Instance (Amazon Linux 2023)"
    participant DBContainer as "DB Container"

    LocalPC->>EC2Instance: Connect
    Note over EC2Instance: Docker Container Running
    EC2Instance->>DBContainer: Connect

    activate LocalPC
    LocalPC->>+EC2Instance: POST to\nHTTP: EC2_IP:3307
    Note over EC2Instance: Handle\nPOST Request
    EC2Instance->>-DBContainer: Perform\nDatabase Operations
    deactivate LocalPC

    DBContainer-->>-EC2Instance: Respond\nwith Data
    EC2Instance-->>-LocalPC: Respond\nwith Data

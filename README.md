```mermaid
flowchart TB
    %% Frontend Section
    subgraph Frontend
        A[Public Portal] -->|Search, View Videos, Download| API
        B[Admin Dashboard] -->|Upload Videos, Edit Transcripts| API
        C[Superadmin Dashboard] -->|Manage Users, Billing Plans| API
        D[Stripe Payment Pages] -->|User Subscription| Billing
    end

    %% Backend Section
    subgraph Backend
        API[API Gateway] --> Auth[Authentication/Auth0]
        API --> DB[PostgreSQL/DynamoDB]
        API --> Queue[AWS SQS or Celery]
        API --> Billing[Stripe Integration]
        Auth --> Roles[Role-Based Access]
    end

    %% AI Processing Section
    subgraph AI_Processing
        Upload[Upload Videos to AWS S3] --> Transcription[AI Transcription Services]
        Transcription --> SpeakerTagging[Speaker Tagging]
        SpeakerTagging --> Summarization[Summarization and Topic Segmentation]
        Summarization --> Metadata[Metadata Storage]
        Metadata --> DB
    end

    %% Connections
    Frontend --> API
    Queue --> AI_Processing
    AI_Processing --> DB
    Billing --> DB

    %% Storage Section
    subgraph Storage
        S3[AWS S3 for Video Storage] --> AI_Processing
        DB --> Frontend
    end

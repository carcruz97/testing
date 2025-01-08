graph TD
    subgraph Frontend
        A[Public Portal] --> B[Search & Playback]
        A --> C[Download Content]
        D[Admin Dashboard] --> E[Upload Videos]
        D --> F[Manage Transcripts]
        G[Superadmin Dashboard] --> H[User Management]
        G --> I[System Logs]
        J[Billing Pages] --> K[Subscription Payment]
    end

    subgraph Backend
        L[API Gateway] --> M[Authentication]
        L --> N[Video Processing Workflow]
        N --> O[Queue Management]
        L --> P[Billing API Integration]
    end

    subgraph AI Processing
        Q[Video Upload] --> R[Transcription]
        R --> S[Speaker Tagging]
        S --> T[Topic Segmentation]
        T --> U[Summarization]
    end

    subgraph Database and Storage
        V[Storage] --> W[Video Files]
        V --> X[Processed Outputs]
        Y[Database] --> Z[Metadata]
        Y --> AA[Transcripts]
        Y --> AB[User Accounts]
        Y --> AC[Subscription Status]
    end

    subgraph Billing System
        AD[Subscription Management] --> AE[Enforce Access]
        AD --> AF[Invoice Generation]
        AG[Payment Processing] --> AH[Sync Billing Data]
    end

    A --> L
    D --> L
    G --> L
    J --> P
    N --> Q
    R --> Y
    S --> Y
    V --> Q
    AD --> AB
    AG --> AC

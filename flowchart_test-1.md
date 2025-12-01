# Machine Learning Workflow

```mermaid
graph TD
    subgraph A [Initial Phase]
        direction LR
        A1[Problem Statement] --> A2[Data Collection] --> A3[Data Preprocessing]
    end
    
    A3 --> B[Choose Model]
    
    subgraph C [Training & Validation Phase]
        direction LR
        C1[Parameters Tuning] --> C2[Training Model] --> C3[Cross Validation]
    end
    
    C3 --> D{Training goal meet?}
    D -->|No| C1
    D -->|Yes| E[Deployment]
```

graph TD
    subgraph A [Initial Phase]
        direction LR
        A1[Problem Statement] --> A2[Data Collection] --> A3[Data Preprocessing]
    end
    
    A3 --> B[Choose Model]
    
    subgraph C [Training & Validation Phase]
        direction LR
        C1[Parameters Tuning] --> C2[Training Model] --> C3[Cross Validation]
    end
    
    C3 --> D{Training goal meet?}
    D -->|No| C1
    D -->|Yes| E[Deployment]























```mermaid
flowchart TD

    %% Invisible helpers to force horizontal alignment for the first row
    A[Problem Statement]
    B[Data Collection]
    C[Data Preprocessing]

    A --> B
    B --> C

    %% Force B and C to stay on same row by locking them to invisible nodes
    A --- X1(( )):::invis
    B --- X2(( )):::invis
    C --- X3(( )):::invis

    %% Vertical flow begins here
    C --> D[Choose Model]
    D --> E[Training Model]
    E --> F[Cross Validation]
    F --> G{Training Goal Met?}
    G -- No --> H[Parameters Tuning]
    H --> E
    G -- Yes --> I[Deployment]

    %% Style for invisible alignment nodes
    classDef invis fill:none,stroke:none;

```









```mermaid   
flowchart TD

    %% --- Define Colors ---
    classDef start fill:#4CAF50,stroke:#1B5E20,color:#fff;
    classDef data fill:#0288D1,stroke:#01579B,color:#fff;
    classDef process fill:#7E57C2,stroke:#4A148C,color:#fff;
    classDef model fill:#FF7043,stroke:#E64A19,color:#fff;
    classDef decision fill:#FDD835,stroke:#F9A825,color:#000;
    classDef output fill:#66BB6A,stroke:#2E7D32,color:#fff;
    classDef monitor fill:#26A69A,stroke:#004D40,color:#fff;

    A[Define Objective]:::start
    B[Acquire Data<br/>RNA-seq, Clinical, Gencode]:::data
    C[Integrate Data]:::process
    D[Preprocess Data]:::process
    E[Feature Engineering]:::process
    F[Select Model<br/>Random Forest]:::model
    G[Train Model]:::model
    H[Cross Validation]:::model
    I{Performance OK?}:::decision
    J[Hyperparameter Tuning]:::model
    K[Identify Biomarkers<br/>Top 50 Genes]:::output
    L[Deployment]:::output
    M[Model Monitoring<br/>Drift Detection]:::monitor
    N[Retrain Model]:::monitor

    A --> B --> C --> D --> E --> F --> G --> H --> I
    I -- No --> J --> F
    I -- Yes --> K --> L --> M
    M -- Drift Detected --> N --> F
```




















```mermaid   
flowchart TD   
    A[Define Objective: subtype classification & biomarker discovery]   
        --> B[Acquire Data: RNA-seq, Clinical, Gencode]   

    B --> C[Integrate Data: merge RNA-seq + clinical + annotations]   

    C --> D[Preprocess Data: normalize, batch-correct, filter]   

    D --> E[Feature Engineering: PCA, variance filter, pathways]   

    E --> F[Select Model: Random Forest]   

    F --> G[Train Model]   

    G --> H[Cross Validation: stratified k-fold]   

    H --> I{Performance meets target?}  

    I -- No --> J[Hyperparameter Tuning]  
    J --> F  

    I -- Yes --> K[Identify Biomarkers: top 50 genes]  

    K --> L[Deployment: inference pipeline]  

    L --> M[Model Monitoring: drift detection]   

    M -- Drift Detected --> N[Retrain Model with updated data]  
    N --> F  
```

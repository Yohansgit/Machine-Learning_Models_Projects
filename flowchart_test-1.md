```mermaid
flowchart TD

    %% Top row forced horizontal   
    subgraph TOP[ ]   
    direction LR 
        A[Problem Statement] --> B[Data Acquisition] --> C[Data Preprocessing]     
    end     
   
    %% Vertical Flow
    C --> D[Choose Model]    
    D --> E[Training Model]
    E --> F[Cross Validation]
    F --> G{Training Goal Met?}
    G -- No --> H[Parameters Tuning]
    H --> E
    G -- Yes --> I[Deployment]
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

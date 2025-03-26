# Mermaid Diagram Examples for Developers

## 1. Flowchart: Project Workflow
```mermaid
flowchart TD
    A[Start Project] -->|Planning| B{Requirements Analysis}
    B -->|Validate| C[Design]
    B -->|Revise| A
    C -->|Development| D[Implementation]
    D -->|Testing| E{Quality Assurance}
    E -->|Pass| F[Deployment]
    E -->|Fail| D
    F --> G[Maintenance]
```

## 2. Sequence Diagram: API Interaction
```mermaid
sequenceDiagram
    participant Client
    participant APIGateway
    participant AuthService
    participant MainService
    
    Client->>APIGateway: Request
    APIGateway->>AuthService: Validate Token
    AuthService-->>APIGateway: Token Valid
    APIGateway->>MainService: Forward Request
    MainService-->>APIGateway: Process Response
    APIGateway-->>Client: Return Response
```

## 3. Git Workflow Diagram
```mermaid
gitGraph:
    commit id: "Initial Commit"
    branch dev
    checkout dev
    commit id: "Setup Project Structure"
    branch feature/user-auth
    checkout feature/user-auth
    commit id: "Implement Login"
    commit id: "Add Password Reset"
    checkout dev
    merge feature/user-auth id: "Merge User Auth"
    branch feature/dashboard
    checkout feature/dashboard
    commit id: "Create Dashboard Layout"
    checkout dev
    merge feature/dashboard id: "Merge Dashboard"
    commit id: "Prepare Release"
    branch release/v1.0
    checkout release/v1.0
    commit id: "Final Testing"
```

## 4. State Diagram: User Account Lifecycle
```mermaid
stateDiagram-v2
    [*] --> Registered
    Registered --> Verified : Email Confirmation
    Verified --> Active : Complete Profile
    Active --> Suspended : Violation
    Suspended --> Active : Appeal Approved
    Active --> Inactive : Inactivity
    Inactive --> Active : Reactivate
    Active --> [*] : Account Deletion
```

## 5. Class Diagram: E-commerce System
```mermaid
classDiagram
    class User {
        +id: int
        +email: string
        +password: string
        +register(): void
        +login(): boolean
    }
    class Product {
        +id: int
        +name: string
        +price: float
        +description: string
        +updateInventory(): void
    }
    class Order {
        +id: int
        +userId: int
        +totalPrice: float
        +status: string
        +createOrder(): void
        +updateStatus(): void
    }
    User "1" -- "0..*" Order : places
    Order "1" -- "1..*" Product : contains
```

## 6. Entity Relationship Diagram: Blog Platform
```mermaid
erDiagram
    USER ||--o{ POST : creates
    USER ||--o{ COMMENT : writes
    POST ||--o{ COMMENT : has
    POST {
        int id PK
        string title
        string content
        datetime created_at
    }
    USER {
        int id PK
        string username
        string email
    }
    COMMENT {
        int id PK
        string content
        datetime created_at
    }
```

## 7. Gantt Chart: Sprint Planning
```mermaid
gantt
    title Software Development Sprint
    dateFormat  YYYY-MM-DD
    section Backend
    Database Design       :done,  des1, 2024-02-01, 3d
    API Development       :active,  des2, after des1, 5d
    
    section Frontend
    UI Design             :done, des3, 2024-02-03, 2d
    Component Development :active, des4, after des3, 4d
    
    section Testing
    Unit Testing          :active, des5, 2024-02-10, 3d
    Integration Testing   :active, des6, after des5, 3d
    
    section Deployment
    Staging Deploy        :milestone, des7, 2024-02-15, 0d
    Production Deploy     :milestone, des8, 2024-02-20, 0d
```

## Tips for Using Mermaid
1. Install Mermaid library in your documentation tools
2. Use in markdown files, documentation platforms
3. Can be integrated with tools like GitHub, VS Code
4. Great for visualizing complex systems and workflows
```


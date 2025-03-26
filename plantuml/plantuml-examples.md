# PlantUML Diagram Examples for Developers

## 1. Flowchart: Project Workflow
```plantuml
@startuml
!theme plain
skinparam linetype ortho

start
:Start Project;
if (Requirements Analysis) then (valid)
  :Design;
  :Implementation;
  if (Quality Assurance) then (pass)
    :Deployment;
    :Maintenance;
    stop
  else (fail)
    ->back to implementation;
    :Implementation;
  endif
else (revise)
  ->back to start;
  :Start Project;
endif
@enduml
```

## 2. Sequence Diagram: API Interaction
```plantuml
@startuml
!theme plain
actor Client
participant "API Gateway" as APIGateway
participant "Auth Service" as AuthService
participant "Main Service" as MainService

Client -> APIGateway : Request
APIGateway -> AuthService : Validate Token
AuthService --> APIGateway : Token Valid
APIGateway -> MainService : Forward Request
MainService --> APIGateway : Process Response
APIGateway --> Client : Return Response
@enduml
```

## 3. Component Diagram: Git Workflow
```plantuml
@startuml
!theme plain
[Initial Commit] as IC
folder "Develop Branch" as Dev {
  [Setup Project Structure] as SPS
  
  folder "Feature: User Auth" as UA {
    [Implement Login] as IL
    [Add Password Reset] as APR
  }
  
  folder "Feature: Dashboard" as DB {
    [Create Dashboard Layout] as CDL
  }
  
  [Prepare Release] as PR
}

IC --> Dev
UA --> Dev
DB --> Dev
@enduml
```

## 4. State Diagram: User Account Lifecycle
```plantuml
@startuml
!theme plain
state "Registered" as Reg
state "Verified" as Ver
state "Active" as Act
state "Suspended" as Sus
state "Inactive" as Ina

[*] --> Reg
Reg --> Ver : Email Confirmation
Ver --> Act : Complete Profile
Act --> Sus : Violation
Sus --> Act : Appeal Approved
Act --> Ina : Inactivity
Ina --> Act : Reactivate
Act --> [*] : Account Deletion
@enduml
```

## 5. Class Diagram: E-commerce System
```plantuml
@startuml
!theme plain
class User {
  -id: int
  -email: string
  -password: string
  +register(): void
  +login(): boolean
}

class Product {
  -id: int
  -name: string
  -price: float
  -description: string
  +updateInventory(): void
}

class Order {
  -id: int
  -userId: int
  -totalPrice: float
  -status: string
  +createOrder(): void
  +updateStatus(): void
}

User "1" -- "0..*" Order
Order "1" -- "1..*" Product
@enduml
```

## 6. Entity Relationship Diagram: Blog Platform
```plantuml
@startuml
!theme plain
entity User {
  * id : int
  --
  * username : string
  * email : string
}

entity Post {
  * id : int
  --
  * title : string
  * content : string
  * created_at : datetime
}

entity Comment {
  * id : int
  --
  * content : string
  * created_at : datetime
}

User ||--o{ Post
User ||--o{ Comment
Post ||--o{ Comment
@enduml
```

## 7. Activity Diagram: Sprint Planning
```plantuml
@startuml
!theme plain
title Software Development Sprint

start
partition Backend {
  :Database Design;
  :API Development;
}

partition Frontend {
  :UI Design;
  :Component Development;
}

partition Testing {
  :Unit Testing;
  :Integration Testing;
}

partition Deployment {
  :Staging Deploy;
  :Production Deploy;
}

stop
@enduml
```

## Tips for Using PlantUML
1. Requires PlantUML processor or plugin
2. Works with many text editors and documentation tools
3. Can be integrated with Markdown, AsciiDoc
4. Supports multiple diagram types
5. Version control friendly due to text-based format
```
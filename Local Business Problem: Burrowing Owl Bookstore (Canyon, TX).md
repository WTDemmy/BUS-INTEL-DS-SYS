 Local Business Problem: Burrowing Owl Bookstore (Canyon, TX)

Problem Statement
How can a small, local bookstore like Burrowing Owl in Canyon, TX increase visibility and foot traffic in a town with limited population and digital ad fatigue using a low-cost, physical-to-digital ad solution during high-traffic local times?

Burrowing Owl Bookstore is a small independent bookstore located in Canyon, Texas — a town heavily dependent on the population of West Texas A&M University. Due to the town’s small size and a shift in consumer behavior (e.g. digital ad fatigue, online buying habits), the store struggles with visibility and customer engagement.

 Context:
- Canyon has a limited local population.
- Daily traffic jams occur between 5–6 PM as residents/students commute home to Amarillo.
- Traditional digital ads are often ignored by mobile users.

Objective

Develop a low-cost, scalable solution that increases foot traffic and engagement with the bookstore, using physical and digital touchpoints that align with the town's daily flow and behavior.

Solution: Micro-Zones Ad Network

A hybrid marketing system that blends **physical flyers** and **QR-based digital engagement**, targeting specific “micro-zones” with high commuter presence and student activity.

How It Works:
 FlowChart Diagram
```mermaid
flowchart TD
    A[Design Flyer with QR Code] --> B[Place in High Traffic Zones]
    B --> H[Coffee shops near WTAMU]
    B --> I[Bus stops]
    B --> J[Crosswalk poles on traffic-heavy routes]
    H & I & J --> K[Pedestrians Walkway]
    K --> D 
    B --> C[Commuter Notices Flyer]
    C --> D[Scans QR Code]
    D --> E[Digital Offer or Event Page]
    E --> F[Incentive to Visit Store]
    F --> G[Customer Visits Burrowing Owl Bookstore]
```
```mermaid
sequenceDiagram
    participant M as Marketing Team
    participant L as Locations (Coffee Shops, Bus Stops, Crosswalks)
    participant P as Pedestrian/Commuter
    participant F as Flyer with QR Code
    participant QR as QR Landing Page
    participant S as Burrowing Owl Bookstore

    M->>L: Places flyers in high-traffic zones
    L->>P: Flyers are visible in daily commute
    P->>F: Notices flyer at walkway
    P->>F: Scans QR code
    F->>QR: Redirects to digital offer or event
    QR-->>P: Displays content (promo, event, book)
    P->>S: Visits Burrowing Owl Bookstore with incentive
```
Class Diagram 
```mermaid

classDiagram
    class Flyer {
        +String flyerId
        +String qrCodeURL
        +Date datePlaced
        +String campaignName
    }

    class Location {
        +String locationId
        +String name
        +String type  // Coffee Shop, Bus Stop, etc.
        +String address
    }

    class User {
        +String userId
        +String deviceType
        +String timeOfScan
        +String locationScanned
    }

    class QRScan {
        +String scanId
        +String flyerId
        +String userId
        +Date timestamp
    }

    class LandingPage {
        +String pageId
        +String contentType  // Offer, Event, Book Highlight
        +String link
    }

    class Bookstore {
        +String storeId
        +String name
        +String location
        +String offerAvailable
    }

    Flyer "1" --> "1" LandingPage : links to >
    Flyer "1" --> "1" Location : placed at >
    User "1" --> "many" QRScan : performs >
    Flyer "1" --> "many" QRScan : generates >
    QRScan "1" --> "1" LandingPage : leads to >
    LandingPage "1" --> "1" Bookstore : promotes >
```
Entity Relationship Diagram 
```mermaid
erDiagram
    FLYER {
        string flyerId PK
        string qrCodeURL
        date datePlaced
        string campaignName
        string locationId FK
        string pageId FK
    }

    LOCATION {
        string locationId PK
        string name
        string type
        string address
    }

    USER {
        string userId PK
        string deviceType
        string timeOfScan
        string locationScanned
    }

    QRSCAN {
        string scanId PK
        string flyerId FK
        string userId FK
        string pageId FK
        date timestamp
    }

    LANDINGPAGE {
        string pageId PK
        string contentType
        string link
        string storeId FK
    }

    BOOKSTORE {
        string storeId PK
        string name
        string location
        string offerAvailable
    }

    FLYER }o--|| LOCATION : "placed at"
    FLYER ||--|| LANDINGPAGE : "links to"
    FLYER ||--o{ QRSCAN : "generates"
    USER ||--o{ QRSCAN : "performs"
    QRSCAN ||--|| LANDINGPAGE : "leads to"
    LANDINGPAGE }o--|| BOOKSTORE : "promotes"
```


# Army-ERD
Army Data Wearhouse ERD
```mermaid
---
title: Army Structure
---
erDiagram
  Persoana ||--o{ Divizie : apartine
  Divizie ||--|{ Brigada : apartine
  Brigada }|..|{ Companie : apartine
```

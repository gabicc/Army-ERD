# Army-ERD
## Army Data Wearhouse ERD
 
Editor used: mermaid live editor
https://mermaid.live/edit
 
ERD documentatie
https://mermaid.js.org/syntax/entityRelationshipDiagram.html
 
 
```mermaid
---
title: Army Structure
---
erDiagram
  
  Persoana{
        int id
        string nume
        string prenume
        int id_grad
        int id_divizie
        int id_brigada
        int id_companie
        int id_pluton
        int experienta
        int id_rol
  }
  Grad{
    int id
    string nume
    string ce_comanda

  }
  Promovari{
    int id
    date data
    int id_rang
    int id_persoana
  }
  Armament{
    string model
    int id_persoana
    int nr_gloante
    string calibru
  }
  Rol{
    int id_rol
    string denumire_rol
    int risc
  }
  Locatie{
    int id_locatie
    int latitudine
    int longitudine
    string nume
    string directie_latitudine
    string directie_longitudine
  }
  Antrenament{
    int id
    int id_persoana
    int nr_ore_durata
    int id_locatie
    date data
  }
  Divizie{
    int id
    sting nume
    int id_general
  }
  Brigada{
    int id
    sting nume
    int id_comandant
    int id_divizie
  }
  Companie{
    int id
    sting nume
    int id_capitan
    int id_brigada
  }
  Pluton{
    int id
    sting nume
    int id_locotenent
    int id_companie
  }
  Persoana ||--|| Divizie : apartine
  Persoana ||--o| Brigada : apartine
  Persoana ||--o| Companie : apartine
  Persoana ||--o| Pluton : apartine
  Persoana ||--|| Rol : are
  Persoana ||--|{ Antrenament : "a participat"
  Antrenament ||--|| Locatie : " desfasurat in"
  Rol ||--|| Antrenament : conform
  Rol ||--|| Armament : "are caracteristic"
  Persoana ||--|| Grad : are
  Persoana ||--|{ Armament : are
  Persoana ||--|| Locatie : "se afla in"
  Persoana ||--o{ Promovari : obtine
  Promovari ||--|| Grad : ""
  Divizie ||--|{ Brigada : "compusa din"
  Brigada ||..|{ Companie : "compusa din"
  Companie ||--|{ Pluton : "compusa din"
    
```

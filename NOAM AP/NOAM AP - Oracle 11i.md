---
Title: NOAM AP Solaution Architecture
Description : 11i Integration to Oracle Cloud
---

Here are a Source 11i Details

  ```mermaid
        graph TD 
        OnPrem/Cloud --> OnPrem
        Standalone/Containerized --> Standalone 
        Scalability --> No-Changes
        Platform --> D[Linux]
        style OnPrem/Cloud fill:green
        style Standalone/Containerized fill:grey
        style Scalability fill:violet 
        style Platform fill:orange
  ```
  Here are Digital Integration Layer Details
  ```mermaid
          graph TD 
           Vendor --> OIC
           Technology --> id1[Oracle Cloud Native Orchestration Layer]
           Technology --> id2[Oracle Cloud Native Data Layer]
           Staging -->id2[Stage the data to ATP Database]
           Configuration --> id3[ DB connect to Oracle 11i]
           style Vendor fill:green
          style Technology fill:grey
          style Staging fill:violet 
          style Configuration fill:orange
  ```

  Here are Target Oracle SAAS
  ```mermaid
            graph TD 
            Vendor --> Oracle
            Technology --> id1[Oracle SAAS ERP cloud]
            Configuration --> id2[ AP invoice Okay to pay via FBDI]
            Staging -->id3[Convert the data to Oracle SAAS format using OIC]
            style Vendor fill:green
            style Technology fill:grey
            style Staging fill:violet 
            style Configuration fill:orange
  ```
    Here are Bridge details
 ```mermaid
            graph TD 
            Communication --> Asynchronous
            Protocal --> id1[Https]
            Security --> id2[ DB via Secured account]
            Security --> id3[ ATP via Wallet account]
            Security --> id4[ Oracle SAAS via Secured account]
            Volume --> 100
             style Communication fill:green
            style Protocal fill:grey
            style Security fill:violet 
            style Volume fill:orange
  ```
  Here is a Sequence diagram:
  ```mermaid
          sequenceDiagram
          Oracle 11i ->> OIC: Pull Okay to pay invoice
          OIC->>ATP DB: Save it in DB for enrichment and validation
          ATP DB->> OIC: FBDI format & validation
          OIC ->> Oracle SAAS: Create Okay to Pay invoice in Cloud       
  ```



# UnB Campus Navigation App - Architecture

## 1. System Architecture Diagram
```mermaid
flowchart TD
    A[Frontend: React + Mapbox GL JS] -->|Hardcoded Data| B[UnB Building Coordinates]
    A -->|Optional API Calls| C[Mapbox Directions API]
    A -->|If Saving Data| D[Firebase Firestore]
    D --> E[Anonymous Route History]
```
unb-campus-waze/

├── public/

│   └── index.html

├── src/

│   ├── components/

│   │   ├── Map.js          # Main Mapbox GL component

│   │   └── Controls.js     # Start/end selection UI

│   ├── data/

│   │   └── buildings.js    # Hardcoded UnB coordinates

│   ├── App.js

│   └── index.js

├── package.json

└── README.md

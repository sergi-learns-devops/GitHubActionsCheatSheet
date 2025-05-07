# GitHubActionsCheatSheet
Cheat sheet for GitHub Actions

Toda GitHub Action debe contener unos parámetros básicos:
1. name --> Corresponde al nombre del _workflow_.
2. on --> Corresponde cuando se ejecutará la GitHub Action.
⋅⋅* Admite diferentes tipos de _triggers_. Más información con todos los tipos [aquí](https://docs.github.com/en/actions/writing-workflows/choosing-when-your-workflow-runs/events-that-trigger-workflows).
3. jobs --> Cada _workflow_ contiene uno o más 'jobs'. Estos trabajos irán identados dentro de 'jobs'. 

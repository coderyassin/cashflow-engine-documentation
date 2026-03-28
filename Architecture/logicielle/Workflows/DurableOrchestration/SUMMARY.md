🔹 1. L’idée simple

C’est un moteur qui exécute un workflow (suite d’étapes) en gardant son état de manière persistante.

👉 Contrairement à un code classique :

    . Si ton app crash → tout est perdu ❌
    . Avec un workflow durable → il reprend là où il s’est arrêté ✅

___

🔹 2. Exemple concret

Imagine un processus e-commerce :
1. Créer commande
2. Débiter le paiement
3. Réserver le stock
4. Expédier le produit

👉 Si ton service crash à l’étape 3 :

    . Sans orchestration durable → tu dois tout recommencer 😓
    . Avec orchestration durable → il reprend directement à l’étape 3 ✅

___

🔹 3. Pourquoi “durable” ?

Parce que :

    . L’état du workflow est sauvegardé (DB, event store…)
    . Chaque étape est traçable
    . Les retries sont automatiques
    . Tu peux gérer des workflows qui durent minutes, heures, voire jours

___

🔹 4. Orchestration vs Chorégraphie

👉 Orchestration :

    . Un orchestrateur central contrôle tout    
    . Il décide : “appelle ce service, puis celui-ci…”
    . Plus simple à comprendre et monitorer

👉 Chorégraphie :

    . Chaque service réagit aux événements
    . Pas de chef d’orchestre
    . Plus flexible mais plus complexe à debugger

___

🔹 5. À quoi ça sert vraiment (cas réels)

    . Processus métier long (banque, assurance, RH)
    . Pipelines data / batch
    . CI/CD
    . Traitement asynchrone complexe
    . Intégration entre systèmes (APIs externes)

___

🔹 6. Résumé rapide

👉 Orchestration durable = Exécuter des workflows complexes de manière fiable, persistante et résiliente, même en cas de crash.

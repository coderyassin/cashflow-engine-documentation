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

🔹 3. Le problème sans "durabilité"

Dans un système classique, si une étape échoue (coupure réseau, serveur planté, timeout), tout le workflow peut :

    . S'interrompre sans reprendre
    . Perdre son état (on ne sait plus où on en était)
    . Exécuter deux fois la même action (double facturation, par exemple)

___

🔹 4. Ce que la "durabilité" apporte

Un workflow durable garantit que :

    . **La persistance de l'état** — même si le système redémarre, le workflow reprend exactement là où il s'est arrêté
    . **L'exécution garantie** — chaque étape sera exécutée au moins une fois, et les étapes critiques exactement une fois
    . **La gestion des pannes** — les erreurs sont gérées automatiquement avec des retries, des timeouts et des compensations
    . **La longévité** — un workflow peut durer des secondes... ou des mois (ex : un processus d'approbation humaine)

___

🔹 5. Orchestration vs Chorégraphie

👉 Orchestration :

    . Un orchestrateur central contrôle tout    
    . Il décide : “appelle ce service, puis celui-ci…”
    . Plus simple à comprendre et monitorer

👉 Chorégraphie :

    . Chaque service réagit aux événements
    . Pas de chef d’orchestre
    . Plus flexible mais plus complexe à debugger

___

🔹 6. À quoi ça sert vraiment (cas réels)

    . Processus métier long (banque, assurance, RH)
    . Pipelines data / batch
    . CI/CD
    . Traitement asynchrone complexe
    . Intégration entre systèmes (APIs externes)

___

🔹 6. Résumé rapide

👉 Orchestration durable = Coordonner des processus complexes de façon fiable, même face aux pannes, avec un état persistant et une exécution garantie.

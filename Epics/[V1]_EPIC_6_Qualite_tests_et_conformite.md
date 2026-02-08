# EPIC 6 – Qualité, tests et conformité

## Objectif
Garantir un MVP stable, testable et conforme aux bonnes pratiques de développement et de documentation.

---

## Périmètre
Cet Epic couvre :
- les tests unitaires du domaine
- les tests d’intégration des adapters (REST, persistence)
- la documentation technique et fonctionnelle
- la conformité aux standards de développement et d’architecture

---

## User Stories

### US-6.1 – Tests unitaires du domaine

**Description**  
La logique métier du domaine doit être testée de manière isolée  
afin de garantir son exactitude et sa robustesse.

**Critères d’acceptation**
- Chaque classe du domaine possède des tests unitaires couvrant les cas critiques
- Les tests peuvent être exécutés automatiquement via Maven / Gradle
- Les résultats sont reproductibles sur tous les environnements
- Les tests échoués bloquent le pipeline CI/CD

---

### US-6.2 – Tests d’intégration des adapters

**Description**  
Les adapters REST et persistence doivent être testés en intégration  
afin d’assurer la cohérence et la sécurité des flux de données.

**Critères d’acceptation**
- Les endpoints REST sont testés via des tests d’intégration
- Les interactions avec la base de données sont simulées ou réelles selon l’environnement
- Les tests couvrent les principaux flux critiques
- Les tests sont automatisables dans le pipeline CI/CD

---

### US-6.3 – Documentation technique

**Description**  
La documentation technique et fonctionnelle doit être claire et accessible  
afin de faciliter l’onboarding et la maintenance du projet.

**Critères d’acceptation**
- README général du projet et README par module
- Schémas d’architecture et diagrammes UML disponibles
- Explications des endpoints REST, des rôles et privilèges
- Instructions de build, déploiement et exécution des tests

---

## Dépendances
- Dépend de **EPIC 1 à EPIC 5** pour assurer la couverture fonctionnelle
- Intègre la pipeline CI/CD définie dans EPIC 1

---

## Livrables attendus
- Tests unitaires du domaine avec couverture minimale définie
- Tests d’intégration des adapters avec rapports automatiques
- Documentation technique complète et à jour
- Guidelines pour le maintien de la qualité et conformité du code

---

## Notes techniques
- Les tests suivent les standards JUnit / Spring Test
- La CI/CD doit exécuter tests unitaires et intégration automatiquement
- La documentation est versionnée dans le dépôt Git pour assurer traçabilité
- Cet Epic constitue un socle qualité indispensable pour un MVP stable

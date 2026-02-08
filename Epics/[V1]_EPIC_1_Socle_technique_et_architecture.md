# EPIC 1 – Socle technique & architecture

## Objectif
Mettre en place une base technique saine, maintenable et évolutive, alignée avec une architecture hexagonale, afin de garantir la qualité du développement futur et la pérennité de l’application.

---

## Périmètre
Cet Epic couvre :
- l’initialisation du projet backend
- la mise en place de l’architecture hexagonale
- la gestion de la configuration et des secrets
- les fondations techniques nécessaires aux Epics suivants

---

## User Stories

### US-1.1 – Initialisation du projet backend

**Description**  
En tant qu’acteur du développement backend,  
un projet backend doit être initialisé avec Spring Boot  
afin de permettre un démarrage du développement sur une base standardisée et conforme aux bonnes pratiques.

**Critères d’acceptation**
- Le projet démarre correctement sans erreur
- Les profils applicatifs sont configurés (`dev`, `test`)
- La structure de l’architecture hexagonale est visible dès le départ
- Le projet est prêt à être versionné dans un dépôt Git

---

### US-1.2 – Mise en place de l’architecture hexagonale

**Description**  
Une séparation claire entre domaine, application et infrastructure doit être mise en place  
afin de garantir la maintenabilité, la testabilité et l’évolutivité du système.

**Critères d’acceptation**
- Le domaine ne dépend d’aucun framework (Spring, JPA, etc.)
- Les ports (inbound et outbound) sont définis explicitement
- Les adapters sont isolés et implémentent les ports
- Les dépendances respectent strictement l’inversion de contrôle

---

### US-1.3 – Gestion de la configuration et des secrets

**Description**  
La configuration et les secrets sensibles doivent être externalisés  
afin d’éviter toute fuite d’informations critiques et de faciliter le déploiement multi-environnements.

**Critères d’acceptation**
- Aucune information sensible n’est stockée en dur dans le code
- La configuration est externalisée via des fichiers ou des variables d’environnement
- Les secrets sont injectés dynamiquement selon l’environnement (`dev`, `test`, `prod`)
- L’application démarre correctement avec une configuration sécurisée

---

## Dépendances
- Aucune dépendance fonctionnelle
- Cet Epic constitue un prérequis obligatoire pour tous les autres Epics du MVP

---

## Livrables attendus
- Projet Spring Boot initialisé
- Architecture hexagonale opérationnelle
- Configuration sécurisée et externalisée
- Documentation minimale du socle technique

---

## Notes d’architecture
- Spring est utilisé exclusivement comme framework d’infrastructure
- Le domaine reste totalement indépendant de toute technologie
- Toute logique métier réside dans le domaine ou les cas d’utilisation
- Cet Epic représente le socle technique non négociable du projet

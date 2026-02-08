# EPIC 3 – Rôles & privilèges (RBAC)

## Objectif
Mettre en place un modèle de sécurité basé sur les rôles (RBAC), permettant un contrôle fin et cohérent des accès aux fonctionnalités du système.

---

## Périmètre
Cet Epic couvre :
- la définition des rôles
- la gestion des privilèges
- l’association entre utilisateurs, rôles et privilèges
- l’intégration avec le mécanisme d’autorisation applicatif

---

## User Stories

### US-3.1 – Création d’un rôle

**Description**  
Un rôle doit pouvoir être créé afin de regrouper un ensemble cohérent de privilèges.

**Critères d’acceptation**
- Un rôle possède un identifiant unique et un nom explicite
- Un rôle peut être actif ou inactif
- Un rôle peut être modifié ou supprimé selon les règles de gouvernance définies
- La création d’un rôle est réservée aux profils autorisés

---

### US-3.2 – Gestion des privilèges

**Description**  
Des privilèges doivent pouvoir être définis afin de contrôler finement l’accès aux ressources et aux actions du système.

**Critères d’acceptation**
- Les privilèges sont définis de manière explicite (ex. `READ`, `WRITE`, `ADMIN`)
- Un privilège peut être associé à un ou plusieurs rôles
- Les privilèges sont centralisés et réutilisables
- Toute modification des privilèges est tracée à des fins d’audit

---

### US-3.3 – Attribution rôle ↔ utilisateur

**Description**  
Un ou plusieurs rôles doivent pouvoir être attribués à un utilisateur  
afin de déterminer ses droits effectifs dans le système.

**Critères d’acceptation**
- Un utilisateur peut disposer de plusieurs rôles
- Les droits effectifs résultent de l’agrégation des privilèges associés aux rôles
- Les modifications d’attribution sont prises en compte immédiatement
- L’attribution des rôles est réservée aux profils autorisés

---

## Dépendances
- Dépend de **EPIC 2 – Gestion des utilisateurs**
- S’intègre avec le mécanisme d’authentification et d’autorisation (Keycloak)

---

## Livrables attendus
- Modèle RBAC opérationnel
- APIs de gestion des rôles et privilèges
- Mécanisme d’attribution rôle ↔ utilisateur
- Documentation des règles d’autorisation

---

## Notes de sécurité
- Les rôles constituent un regroupement logique de privilèges
- Les privilèges représentent l’unité minimale de contrôle d’accès
- L’autorisation est évaluée côté backend, indépendamment du frontend
- Cet Epic est un pilier fondamental de la sécurité applicative

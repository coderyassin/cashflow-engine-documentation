# EPIC 5 – API & exposition des services

## Objectif
Fournir des APIs REST sécurisées, conformes aux bonnes pratiques, permettant l’accès aux services backend tout en respectant le contrôle d’accès basé sur les rôles.

---

## Périmètre
Cet Epic couvre :
- l’exposition des services backend via des APIs REST
- l’authentification sécurisée via API
- la protection des endpoints selon les rôles et privilèges
- l’intégration avec Keycloak pour la gestion des tokens et des autorisations

---

## User Stories

### US-5.1 – API d’authentification

**Description**  
Une API sécurisée doit permettre l’authentification des utilisateurs  
afin que le frontend puisse obtenir un token valide pour accéder aux services.

**Critères d’acceptation**
- L’API valide les identifiants via le fournisseur d’identité (Keycloak)
- Un token d’accès est délivré après authentification réussie
- Les erreurs d’authentification sont renvoyées de manière standardisée
- La documentation de l’API est disponible (ex: OpenAPI / Swagger)

---

### US-5.2 – APIs protégées par rôles

**Description**  
Les APIs doivent être protégées afin que l’accès soit restreint selon les rôles de l’utilisateur  
conformément au modèle RBAC défini.

**Critères d’acceptation**
- Les endpoints REST sont sécurisés par rôle
- L’accès non autorisé est refusé avec un code HTTP approprié (ex: 403)
- Les permissions sont vérifiées côté backend, indépendamment du frontend
- La documentation indique clairement les rôles requis pour chaque endpoint

---

## Dépendances
- Dépend de **EPIC 1 – Socle technique & architecture**
- Dépend de **EPIC 2 – Gestion des utilisateurs**
- Dépend de **EPIC 3 – Rôles & privilèges (RBAC)**
- Dépend de **EPIC 4 – Authentification & MFA (OTP)**

---

## Livrables attendus
- APIs REST sécurisées et documentées
- Intégration avec Keycloak pour authentification et autorisation
- Flux de contrôle d’accès conforme au RBAC
- Tests unitaires et d’intégration des endpoints sécurisés

---

## Notes techniques
- Les APIs REST suivent les standards OpenAPI / RESTful
- L’authentification repose sur OAuth2 / OpenID Connect
- Les tokens JWT sont vérifiés côté backend pour chaque requête
- La sécurité et les rôles sont centralisés pour faciliter la maintenance et les audits

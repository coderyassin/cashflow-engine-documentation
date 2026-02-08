# EPIC 4 – Authentification & sécurité (MFA / OTP)

## Objectif
Assurer une authentification forte et conforme aux bonnes pratiques de sécurité, en imposant une authentification multi-facteurs (MFA) basée sur OTP.

---

## Périmètre
Cet Epic couvre :
- l’authentification par identifiant et mot de passe
- l’activation de l’authentification à deux facteurs (OTP)
- la validation OTP lors de la connexion
- le refus d’accès en cas d’OTP absent ou invalide
- l’intégration avec le fournisseur d’identité (Keycloak)

---

## User Stories

### US-4.1 – Authentification par login / mot de passe

**Description**  
Un utilisateur doit pouvoir s’authentifier à l’aide de ses identifiants  
afin d’accéder de manière sécurisée à l’application.

**Critères d’acceptation**
- L’authentification repose sur un mécanisme standard OAuth2 / OpenID Connect
- Les identifiants sont transmis de manière sécurisée
- Un échec d’authentification empêche tout accès aux ressources protégées
- Les tentatives échouées sont tracées à des fins de sécurité

---

### US-4.2 – Activation de l’OTP (2FA)

**Description**  
L’authentification à deux facteurs doit pouvoir être activée  
afin de renforcer la sécurité du compte utilisateur.

**Critères d’acceptation**
- Un secret OTP est généré de manière sécurisée
- Un QR Code est fourni pour l’enrôlement
- Le QR Code est compatible avec les applications d’authentification standards (Google Authenticator, Microsoft Authenticator, etc.)
- L’activation de l’OTP est persistée pour le compte utilisateur

---

### US-4.3 – Validation OTP lors du login

**Description**  
Un code OTP valide doit être requis après la vérification du mot de passe  
afin de finaliser le processus d’authentification.

**Critères d’acceptation**
- Le code OTP est requis systématiquement après l’authentification primaire
- Le code OTP est validé selon l’algorithme standard (TOTP)
- Une tentative avec OTP invalide entraîne un échec d’authentification
- Le jeton d’accès n’est délivré qu’après validation complète

---

### US-4.4 – Blocage en cas d’OTP absent ou invalide

**Description**  
L’accès au système doit être refusé en l’absence d’un OTP valide  
afin d’imposer strictement l’authentification multi-facteurs.

**Critères d’acceptation**
- Toute tentative sans OTP valide est rejetée
- Aucun accès partiel n’est accordé sans validation complète
- L’événement est journalisé à des fins d’audit et de sécurité
- Le comportement est identique sur tous les environnements

---

## Dépendances
- Dépend de **EPIC 2 – Gestion des utilisateurs**
- Dépend de **EPIC 3 – Rôles & privilèges (RBAC)**
- Repose sur l’intégration avec Keycloak comme fournisseur d’identité

---

## Livrables attendus
- Authentification OAuth2 / OIDC opérationnelle
- MFA (OTP) activé et obligatoire
- Flux d’authentification sécurisé et documenté
- Intégration complète avec le backend Spring Boot

---

## Notes de sécurité
- L’OTP constitue un facteur obligatoire et non optionnel
- L’authentification est centralisée au niveau du fournisseur d’identité
- Aucun secret OTP n’est exposé côté frontend
- Les règles de sécurité sont appliquées de manière homogène sur l’ensemble du système

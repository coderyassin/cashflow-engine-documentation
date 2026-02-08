# EPIC 2 – Gestion des utilisateurs

## Objectif
Permettre la création, la consultation et la gestion des utilisateurs du système, tout en garantissant la cohérence des données et le contrôle des accès.

---

## Périmètre
Cet Epic couvre :
- la gestion du cycle de vie des utilisateurs
- la consultation des informations utilisateur
- l’activation et la désactivation des comptes
- la préparation à l’intégration avec le système d’authentification et d’autorisation

---

## User Stories

### US-2.1 – Création d’un utilisateur

**Description**  
Un utilisateur doit pouvoir être créé avec ses informations de base  
afin de lui permettre un accès contrôlé au système.

**Critères d’acceptation**
- L’adresse email est unique dans le système
- Le mot de passe est stocké de manière chiffrée
- Le compte utilisateur est désactivé par défaut (optionnel, selon configuration)
- Les informations obligatoires sont validées lors de la création

---

### US-2.2 – Consultation d’un utilisateur

**Description**  
Les informations d’un utilisateur doivent pouvoir être consultées  
afin de vérifier son état, ses rôles et ses privilèges associés.

**Critères d’acceptation**
- Les informations utilisateur sont accessibles via un identifiant unique
- L’état du compte (actif / inactif) est visible
- Les rôles et privilèges associés sont affichés
- L’accès à cette fonctionnalité est restreint aux profils autorisés

---

### US-2.3 – Activation / désactivation d’un utilisateur

**Description**  
Un compte utilisateur doit pouvoir être activé ou désactivé  
afin de contrôler l’accès au système sans suppression des données.

**Critères d’acceptation**
- Un utilisateur désactivé ne peut pas s’authentifier
- L’activation ou la désactivation est tracée (audit minimal)
- L’opération est accessible uniquement aux profils autorisés
- L’état du compte est mis à jour immédiatement

---

## Dépendances
- Dépend de **EPIC 1 – Socle technique & architecture**
- Prépare l’intégration avec l’Epic Sécurité & Authentification

---

## Livrables attendus
- Modèle utilisateur fonctionnel
- APIs de gestion des utilisateurs
- Gestion des états (actif / inactif)
- Documentation des règles de gestion utilisateur

---

## Notes fonctionnelles
- La gestion des utilisateurs est indépendante du mécanisme d’authentification
- Les rôles regroupent des privilèges et ne sont pas attribués de manière implicite
- Cet Epic constitue une base fonctionnelle pour la sécurité et la gouvernance des accès

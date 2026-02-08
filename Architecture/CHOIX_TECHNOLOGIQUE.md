# Choix Technologique – Application de gestion des flux financiers

## Objectif
Documenter les décisions technologiques prises pour le développement de l’application, justifier leur pertinence et faciliter la compréhension pour l’équipe de développement et les parties prenantes.

---

## 1. Backend

**Technologie retenue : Spring Boot (Java 21+)**
- Framework mature et robuste pour développer des APIs REST et microservices
- Support complet pour **architecture hexagonale**, testabilité, et inversion de dépendance
- Intégration native avec **Spring Security**, **Spring Data JPA**, et **Keycloak** pour la sécurité

**Avantages**
- Productivité élevée grâce à l’écosystème Spring
- Sécurité robuste (JWT, OAuth2, RBAC)
- Maintenance simplifiée grâce à la structuration en **domaine, application, infrastructure**

---

## 2. Frontend

**Technologie retenue : Angular 18**
- Framework SPA moderne, fortement typé grâce à TypeScript
- Compatible avec une architecture **modulaire et standalone components**
- Intégration simple avec APIs REST sécurisées via OAuth2 / JWT

**Avantages**
- Expérience utilisateur fluide et réactive
- Réutilisation des composants
- Support long terme et communauté active

---

## 3. Base de données

**Technologie retenue : PostgreSQL**
- Base relationnelle robuste et scalable
- Supporte transactions complexes et contraintes d’intégrité
- Fonctionnalités avancées (JSON, indexation, performance)

**Avantages**
- Stabilité pour les données critiques (flux financiers)
- Intégration facile avec Spring Data JPA
- Performances et sécurité reconnues en production

---

## 4. Authentification et sécurité

**Technologie retenue : Keycloak (OAuth2 / OpenID Connect)**
- Fournisseur d’identité centralisé et mature
- Supporte OAuth2, OpenID Connect, SAML
- Intégration native avec Spring Security pour RBAC

**Fonctionnalités clés**
- Authentification via Google / Facebook / login interne
- Gestion des rôles et privilèges (RBAC)
- MFA obligatoire via OTP pour tous les utilisateurs

---

## 5. Architecture et bonnes pratiques

**Architecture hexagonale (Ports & Adapters)**
- Séparation stricte entre **domaine métier**, **cas d’usage** et **infrastructure**
- Adapters indépendants (REST, Persistence, Security)
- Facilite les tests unitaires et l’évolution future

**Avantages**
- Indépendance du framework pour la logique métier
- Maintenabilité et testabilité maximales
- Alignement avec les principes DDD (Domain Driven Design)

---

## 6. CI/CD et infrastructure

**Technologies et pratiques**
- GitHub Actions / GitLab CI pour automatisation des builds et tests
- Docker pour conteneurisation des services backend et frontend
- Déploiement Kubernetes / Helm chart pour orchestration (optionnel pour MVP avancé)

**Avantages**
- Déploiement reproductible et isolé
- Intégration continue et livraison continue
- Scalabilité et monitoring simplifiés

---

## 7. Tests et qualité

**Stratégie**
- Tests unitaires pour le domaine (JUnit, Mockito)
- Tests d’intégration pour adapters (Spring Test / Testcontainers)
- Vérification de la couverture et reporting CI/CD

**Avantages**
- Assure stabilité et fiabilité du MVP
- Réduit les risques en production
- Documentation technique intégrée

---

## 8. Conclusion

Les technologies sélectionnées permettent :
- Une **architecture robuste et maintenable**
- Une **sécurité complète** avec MFA et RBAC
- Une **expérience utilisateur moderne et réactive**
- Un **MVP stable et testable** prêt pour l’évolution

**Ces choix technologiques sont alignés avec les meilleures pratiques de développement, les standards industriels et les besoins du projet.**

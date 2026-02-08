# Architecture Hexagonale – Backend Spring Boot

## Objectif
Documenter en détail l’architecture hexagonale retenue pour le backend afin de garantir **maintenabilité, testabilité, évolutivité et indépendance technologique**.  
Cette architecture est utilisée pour organiser les composants du projet selon des **couches distinctes** : Application, Domaine, Infrastructure.

---

## 1. Vue générale

```
┌─────────────────────────────────────────┐
│         Application Layer               │
│      (Adaptateurs Primary)              │
│   REST, GraphQL, Messaging...           │
└──────────────┬──────────────────────────┘
               │ depends on
               ▼
┌─────────────────────────────────────────┐
│         Domain Layer (Hexagone)         │
│                                         │
│  ┌─────────────────────────────┐        │
│  │   Ports IN (Use Cases)      │        │
│  └─────────────────────────────┘        │
│              │                          │
│              ▼                          │
│  ┌─────────────────────────────┐        │
│  │   Business Logic            │        │
│  │   (Services + Models)       │        │
│  └─────────────────────────────┘        │
│              │                          │
│              ▼                          │
│  ┌─────────────────────────────┐        │
│  │   Ports OUT (SPI)           │        │
│  └─────────────────────────────┘        │
└──────────────┬──────────────────────────┘
               │ implemented by
               ▼
┌─────────────────────────────────────────┐
│      Infrastructure Layer               │
│     (Adaptateurs Secondary)             │
│  Persistence, Messaging, External...    │
└─────────────────────────────────────────┘
```
---

## 2. Application Layer (Adaptateurs Primary)

**Responsabilités**
- Fournir les interfaces d’accès à l’application (REST, GraphQL, Messaging)
- Traduire les requêtes externes en appels vers les **Use Cases (Ports IN)**
- Gérer la validation des données entrantes et la transformation vers les DTO ou modèles métiers
- Appliquer les règles de sécurité au niveau API (JWT, RBAC, MFA)

**Exemples dans notre projet**
- Contrôleurs REST Spring MVC ou WebFlux
- GraphQL Resolver
- Listeners pour Kafka / RabbitMQ
- Validation via Spring Validation / Hibernate Validator

**Dépendances**
- Dépend uniquement du **Domain Layer** (Ports IN / Use Cases)
- Ne doit jamais dépendre directement de l’infrastructure ou de la persistence

---

## 3. Domain Layer (Hexagone)

Le **cœur de l’application**, indépendant des frameworks et de l’infrastructure.

### 3.1 Ports IN (Use Cases)

**Rôle**
- Définissent les actions que l’application peut exécuter depuis l’extérieur
- Servent d’interface pour l’Application Layer
- Encapsulent les cas d’utilisation métier

**Exemples**
- `CreateUserUseCase`
- `AuthenticateUserUseCase`
- `ManageFinancialFlowUseCase`

**Critères**
- Strictement orientés métier, pas de logique technique (DB, REST, messaging)
- Interfaces publiques que l’Application Layer invoque

---

### 3.2 Business Logic (Services + Models)

**Rôle**
- Contient la logique métier réelle
- Modèles et entités du domaine
- Services applicatifs qui orchestrent les règles métiers

**Exemples**
- `UserService` avec logique de création / activation / OTP
- `FinancialFlowService` pour gérer flux entrants et sortants
- Modèles : `User`, `Role`, `Transaction`, `Account`

**Critères**
- Aucune dépendance technique (Spring, JPA, etc.)
- Testabilité maximale via tests unitaires

---

### 3.3 Ports OUT (SPI)

**Rôle**
- Interfaces que le domaine utilise pour accéder à l’extérieur (persistence, messagerie, services externes)
- Permet d’inverser la dépendance : le domaine ne connaît pas les implémentations concrètes

**Exemples**
- `UserRepository` (interface pour DB)
- `NotificationService` (interface pour envoi emails / SMS)
- `PaymentGatewayClient` (interface pour service externe)

---

## 4. Infrastructure Layer (Adaptateurs Secondary)

**Responsabilités**
- Implémenter les Ports OUT définis par le domaine
- Fournir des détails techniques : persistance, messagerie, intégrations externes
- Convertir les entités du domaine en formats techniques (DB, JSON, événements)

**Exemples**
- Spring Data JPA Repository pour persistance Postgres
- Kafka / RabbitMQ producers et consumers
- Clients REST externes pour API partenaires

**Critères**
- Cette couche dépend du **Domain Layer** mais jamais l’inverse
- Les détails techniques sont isolés et remplaçables

---

## 5. Avantages de cette approche

- **Indépendance technologique du domaine** : la logique métier ne dépend ni de Spring ni de la DB
- **Testabilité** : tous les services et use cases sont testables isolément
- **Maintenabilité** : les changements techniques n’impactent pas le métier
- **Flexibilité** : adaptation facile aux nouveaux adaptateurs (REST, GraphQL, Kafka…)
- **Conformité aux bonnes pratiques DDD** : séparation nette des responsabilités

---

## 6. Notes d’implémentation

- Chaque port (IN/OUT) doit avoir une interface claire
- Les adapters implémentent uniquement les ports qu’ils supportent
- Les services du domaine ne doivent jamais accéder directement à l’infrastructure
- Les DTO et mappers peuvent être définis dans l’Application Layer
- CI/CD doit inclure tests unitaires sur le domaine et tests d’intégration pour les adapters

---

**Résumé**
L’architecture hexagonale garantit que :
- Le **cœur métier reste pur**, indépendant des frameworks  
- L’**Application Layer** orchestre et traduit les requêtes externes  
- L’**Infrastructure Layer** est interchangeable et testable  
- Le système est prêt pour la **scalabilité, la sécurité et le maintien à long terme**


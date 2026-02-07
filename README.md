# 📁 README – Application de Gestion des Flux Financiers

Ce répertoire contient tous les documents de **cadrage, conception et spécifications** pour le projet de l’application de gestion des flux financiers.

---

## 1. Structure du projet

```
projet-cashflow-engine/
│
├── 1_Cadrage/
│   └── CADRAGE_Application_Gestion_Finances.pdf   # Fichier De Cadrage
│
├── 2_Specifications/
│   └── sfg
│   |   └── SFG_Application_Gestion_Finances.pdf   # Spécifications Fonctionnelles Générales
|   └── sfd
|       └── SFD_Application_Gestion_Finances.pdf   # Spécifications Fonctionnelles Détaillées
├── 3_Conception/
│   ├── Diagrammes_Vision_et_Cadrage/
│   │   ├── Diagramme_Contexte.puml
│   │   └── Diagramme_Use_Case.puml
│   │
│   ├── Diagrammes_Metier/
│   │   ├── Diagramme_Classes_Metier.puml
│   │   └── Diagramme_Etats_Objectif_financier.puml
|   |   └── Diagramme_Etats_Budget.puml
│   │
│   ├── Diagrammes_Comportement/
│   │   ├── Diagramme_Sequence_Ajouter_une_depense.puml
│   │   └── Diagramme_Activites_Simulation-financiere.puml
│   │
│   ├── Diagrammes_Architecture/
│   │   ├── Diagramme_Architecture_Logique.puml
│   │   ├── Diagramme_Composants.puml
│   │   └── Diagramme_Deployment.puml
│   │
│   └── Diagrammes_Donnees/
│       ├── Diagramme_ERD.puml
│       └── Diagramme_DFD-Ajouter-une-Depense.puml
```

---

## 2. Description des dossiers

### 1_Cadrage
Contient les documents de **vision globale** et **objectifs du projet**, lisibles par les parties prenantes métier.

### 2_Specifications
Contient les **Spécifications Fonctionnelles Générales** (SFG) et **Spécifications Fonctionnelles Détaillées** (SFD) avec :
- Cas d’usage
- Règles de gestion
- Critères d’acceptation
- Base pour le développement et les tests

### 3_Conception
Contient **tous les diagrammes UML et techniques**, organisés par catégorie :
1. Vision & Cadrage : diagramme de contexte, diagramme de cas d’utilisation
2. Métier : diagramme de classes, diagramme d’états
3. Comportement : diagramme de séquence, diagramme d’activités
4. Architecture : diagramme logique, diagramme de composants, diagramme de déploiement
5. Données : ERD, DFD

---

## 3. Notes techniques
- Tous les diagrammes sont fournis en **PlantUML (.puml)** pour faciliter la génération automatique.
- Les documents PDF sont exportés pour lecture facile par les parties prenantes.
- La structure reflète un projet **backend Spring Boot Hexagonal + Angular + PostgreSQL**.
- Les diagrammes et spécifications sont alignés avec les pratiques **DDD et Hexagonal Architecture**.

---

## 4. Recommandations
- Utiliser un visualiseur PlantUML pour générer les diagrammes depuis les fichiers `.puml`
- Vérifier la cohérence entre SFD et diagrammes UML avant de commencer le développement
- Respecter l’architecture hexagonale pour maintenir la testabilité et la maintenabilité du projet

---

**Auteur:** Yassin MELLOUKI  
**Projet:** Application de Gestion des Flux Financiers  
**Date:** 2026-02-07


# 📗 Spécifications Fonctionnelles Détaillées (SFD)
## Application de gestion des flux financiers

---

## 1. Objectif du document

Ce document décrit de manière **détaillée et opérationnelle** les fonctionnalités de l’application. Il sert de base directe pour le développement et les tests.

---

## 2. Cas d’usage – Gestion des revenus

### UC-01 : Ajouter un revenu

**Acteur** : Utilisateur

**Description** : L’utilisateur peut enregistrer un nouveau flux entrant.

**Règles de gestion** :
- Le montant est obligatoire
- La date est obligatoire
- La catégorie est obligatoire
- La fréquence peut être ponctuelle ou récurrente

**Résultat attendu** :
- Le revenu est enregistré
- Le tableau de bord est mis à jour

---

### UC-02 : Modifier un revenu
- L’utilisateur peut modifier toutes les informations
- Les projections futures sont recalculées

---

## 3. Cas d’usage – Gestion des dépenses

### UC-03 : Ajouter une dépense

**Règles de gestion** :
- Le montant doit être positif
- Une catégorie doit être sélectionnée
- Une dépense peut être récurrente

---

### UC-04 : Dépense récurrente

- La dépense est automatiquement dupliquée
- Peut être arrêtée ou modifiée

---

## 4. Cas d’usage – Budgets

### UC-05 : Créer un budget

**Règles** :
- Un budget est défini par période
- Un budget par catégorie est autorisé

---

### UC-06 : Dépassement de budget

- Une alerte est déclenchée à 80%
- Une alerte critique à 100%

---

## 5. Cas d’usage – Tableau de bord

- Mise à jour en temps réel
- Affichage des indicateurs clés

---

## 6. Cas d’usage – Prévisions

### UC-07 : Simulation financière

- L’utilisateur saisit un scénario
- L’application calcule l’impact

---

## 7. Cas d’usage – Objectifs financiers

### UC-08 : Créer un objectif

- Montant cible
- Date cible
- Calcul automatique de l’effort mensuel

---

## 8. Notifications

- Dépenses inhabituelles
- Objectif atteint

---

## 9. Exigences non fonctionnelles

- Performance < 2s
- Sécurité des données
- Disponibilité 99.5%

---

## 10. Critères d’acceptation (exemples)

- Une dépense ajoutée apparaît immédiatement
- Les budgets sont recalculés automatiquement

---

## 11. Annexes

- Glossaire
- Règles métiers


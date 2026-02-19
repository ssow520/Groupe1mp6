# Rapport   -   Projet : Application Web de Gestion Budgétaire  
**Équipe :** Souleymane Sow, Moses Kasindi, Ruth Kegmo  
**Date :** 2026-02-XX  

---
## Corrections Phase 1

### 1. Correction de l'accès au SRS

Suite aux commentaires concernant les liens cassés dans le `README.md`, les corrections suivantes ont été effectuées :

- Mise à jour des liens vers le bon chemin : `documentation/SRS.md`
- Vérification de la présence du fichier **SRS.md** dans le dossier `/documentation`
- Suppression des liens menant vers des fichiers inexistants à la racine
- Validation de l’accessibilité du SRS en un clic depuis la page principale du dépôt

Le SRS est désormais accessible directement sur GitHub.

---

### 2. Amélioration des exigences fonctionnelles (FR)

Les exigences fonctionnelles ont été renforcées afin de les rendre plus précises, complètes et testables :

- Reformulation selon le format standard : *“Le système doit…”*
- Ajout de critères de validation pour chaque exigence
- Couverture complète du périmètre annoncé (authentification, gestion des transactions, calcul automatique, résumé budgétaire, recommandation)

Des cas d’erreur ont été ajoutés, notamment :
- Email déjà utilisé
- Identifiants invalides
- Montant négatif ou nul
- Transaction inexistante

---

### 3. Renforcement des exigences non fonctionnelles (NFR)

Les NFR ont été précisées et rendues mesurables :

#### Sécurité (NFR-2)
- Hashage obligatoire des mots de passe
- Session active requise pour accéder au tableau de bord
- Isolation stricte des données par utilisateur

#### Performance (NFR-1)
- Temps de réponse des pages principales < 5 secondes

#### Expérience utilisateur (NFR-3)
- Ajout d’une transaction en maximum 3 clics
- Messages d’erreur compréhensibles

#### Disponibilité et maintenabilité
- Disponibilité minimale de 95 % durant la période de test
- Architecture claire frontend/backend

---

### 4. Clarification du périmètre

Le périmètre a été clarifié pour éviter toute dérive du projet.

#### Inclus (IN)
- Création et gestion de compte
- Authentification
- CRUD revenus et dépenses
- Calcul automatique du solde
- Historique des transactions
- Tableau de bord budgétaire
- Recommandations simples

#### Exclu (OUT)
- Connexion à des comptes bancaires réels
- Paiements en ligne
- Multi-devises
- Intelligence artificielle avancée

---

### 5. Amélioration de la structure du document

Les améliorations suivantes ont été apportées :

- Clarification des entités principales (User, Transaction, Budget)
- Ajout de règles métier explicites
- Ajout d’une “Definition of Done”

---



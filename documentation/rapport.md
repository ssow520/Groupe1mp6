# Rapport   -   Projet : Application Web de Gestion Budgétaire  
**Équipe :** Souleymane Sow, Moses Kasindi, Ruth Kegmo  
**Date :** 2026-02-20  

---
## Asana, tableau de bord agile
[Asana](https://app.asana.com/1/1213298021800524/project/1213303786003588/board/1213303344835469)

---
## Corrections Phase 1

### 1. Correction de l'accès au SRS

Suite aux commentaires concernant les liens cassés dans le `README.md`, les corrections suivantes ont été effectuées :

- Mise à jour des liens vers le bon chemin : `documentation/SRS.md`
- Validation de l’accessibilité du SRS en un clic depuis la page principale du dépôt

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

### 4. Clarification du périmètre

Le périmètre a été clarifié: 

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

### 5. Amélioration de la structure du document

Les améliorations suivantes ont été apportées :

- Clarification des entités principales (User, Transaction, Budget)
- Ajout de règles métier
- Ajout d’une “Definition of Done”

---


## Diagramme de composant.png

- [Diagramme_composant.png](documentation/Diagramme_composant.png)

Il illustre la structuration du système en trois sous-systèmes principaux :

- **Frontend (React)**
- **Backend (API REST)**
- **Data Layer (Base de données)**

Ce diagramme met en évidence les composants internes de chaque sous-système ainsi que les interfaces utilisées pour assurer la communication entre eux. On distingue:

### Sous-système Frontend

Le Frontend représente l’interface utilisateur développée en React.
Il contient les composants suivants :
- **UI App** : composant principal de l’application
- **AuthView** : gestion de la connexion et de la création de compte
- **DashboardView** : affichage du résumé budgétaire
- **TransactionView** : gestion des revenus et des dépenses

Le Frontend communique avec le Backend via des interfaces API :
- `IAuthAPI`
- `IBudgetAPI`


### Sous-système Backend

Le Backend expose des services via une API REST.
Il contient les composants :
- **AuthService** : gestion de l’authentification (hash des mots de passe, validation)
- **UserService** : gestion des informations utilisateur
- **BudgetService** : calcul automatique du solde
- **RecommendationService** : génération de messages d’aide selon le solde

Le Backend fournit les interfaces :
- `AuthAPI`
- `BudgetAPI`
Ces interfaces sont utilisées par le Frontend pour accéder aux fonctionnalités métier.


### 2.3 Sous-système Data Layer

La couche de données assure la persistance des informations :
- **UserRepository**
- **TransactionRepository**
- **Database**

---


## Diagramme des Cas d’Utilisation 

- [Diagramme_cas_d'utilisation](documentation/Diagramme_cas_d'uilisation.png)

Il illustre les fonctionnalités principales définies dans le SRS ainsi que les relations entre elles.

### Acteurs

#### Utilisateur
Acteur principal du système.  
Il peut :
- Créer un compte  
- Se connecter / se déconnecter  
- Ajouter, modifier et supprimer des transactions  
- Catégoriser les dépenses et définir leur fréquence  
- Consulter l’historique  
- Visualiser le résumé budgétaire  

#### Équipe technique
Acteur secondaire responsable de :
- La maintenance du système  
- La supervision technique  

Les cas d’utilisation sont regroupés en quatre blocs :

1. **Gestion du compte**  
2. **Gestion des transactions**  
3. **Calcul et résumé budgétaire**  
4. **Administration**


### Relations importantes

- Toute modification de transaction inclut automatiquement le **calcul du solde**.  
- L’ajout d’une dépense inclut la **catégorisation** et la **définition de fréquence**.  
- La consultation du résumé budgétaire inclut l’**affichage d’un indicateur visuel et la génération d’une recommandation**.

---


## Diagramme de Classe – Vue d’Ensemble du Budget (Dashboard)

- [diagramme_classe](documentation/diagramme_classe.png)

Ce diagramme de classe représente la structure logicielle du composant **Vue d’ensemble du budget (Dashboard)** de l’application.

Le diagramme est divisé en deux parties :

- **Frontend (React)**

La classe **DashboardPage** constitue le point d’entrée de la page tableau de bord.  
Elle est composée de plusieurs objets **Card**, représentant :
- IncomeCard (Total Revenus)
- ExpenseCard (Total Dépenses)
- BalanceCard (Solde)

La classe abstraite **Card** définit les attributs communs (titre, montant, couleur) ainsi que les méthodes de formatage et d’affichage.  
Les trois cartes spécialisées héritent de cette classe et implémentent leur propre logique d’application des couleurs.

Le **DashboardService** communique avec l’API via **ApiClient** afin de récupérer les données sous forme de **DashboardDTO**.


- **Backend (Node.js / Express)**

Le **DashboardController** expose l’endpoint `GET /dashboard`.

Le **DashboardServiceBackend** contient la logique métier permettant de calculer :
- Le total des revenus  
- Le total des dépenses  
- Le solde  

Les données sont récupérées via **TransactionRepository**, qui accède aux entités **Transaction** stockées en base de données.

### Relations UML

Le diagramme met en évidence :

- **Héritage** : IncomeCard, ExpenseCard et BalanceCard héritent de la classe abstraite Card.
- **Composition** : DashboardPage est composée de plusieurs Card.
- **Agrégation** : DashboardPage utilise DashboardService, qui utilise ApiClient.
- **Association** : Les services manipulent l’objet DashboardDTO pour le transfert des données.




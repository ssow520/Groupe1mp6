# Cahier des charges (SRS léger) — Application de gestion de budget

**Équipe :**  
Souleymane Sow, Moses Kasindi, Ruth Kegmo

**Date :** 2026-01-23  

**Version :** v1.0

---

## 1. Contexte & objectif
- **Contexte :** <La gestion du budget personnel représente un défi majeur pour les étudiants et les jeunes actifs. Entre les revenus limités, les dépenses récurrentes (logement, transport, alimentation) et les dépenses variables, il devient difficile d’avoir une vision claire de sa situation financière. Ce projet académique vise à développer une application web de gestion budgétaire permettant d’appliquer les concepts vus en cours (architecture logicielle, gestion des exigences, développement structuré).>
- **Objectif principal :** <Développer une application web permettant à un utilisateur : de créer un compte sécurisé, d’enregistrer ses revenus et ses dépenses (journalières, hebdomadaires, mensuelles), d’obtenir un calcul automatique de son solde, de recevoir des recommandations simples pour mieux gérer son budget.>
- **Parties prenantes :** <Utilisateur final (Client) : utilise l’application pour gérer son budget. Équipe de développement : conçoit et maintient l’application.Enseignant : évalue la conformité technique et documentaire.>

---

## 2. Portée (Scope)

### 2.1 Inclus (IN)
- IN-1 : <Création et gestion de compte utilisateur>
- IN-2 : <Authentification (connexion / déconnexion)>
- IN-3 : <Ajout, modification et suppression de dépenses>
- IN-4 : <Catégorisation des dépenses (ex : logement, alimentation, transport)>
- IN-5 : <Calcul automatique du solde (revenus – dépenses)>
- IN-6 : <Historique des transactions>
- IN-7 : <Affichage d’un résumé budgétaire (total revenus, total dépenses, solde)>
- IN-6 : <Ajout, modification et suppression de revenus>

### 2.2 Exclu (OUT)
- OUT-1 : Connexion à des comptes bancaires réels
- OUT-2 : Paiements en ligne
- OUT-3 : Application multi-devises ou internationale
- OUT-4 : Fonctionnalités avancées d’intelligence artificielle

---

## 3. Acteurs / profils utilisateurs
- **Acteur Client :** <rôle : Gérer ses finances personnelles. besoins : Interface simple, résultats clairs, rapidité d’utilisation. contraintes : connaissances limitées en gestion financière>
- **Acteur Equipe :** <Rôle : gestion technique de l’application, Besoins : accès aux données pour maintenance, Contraintes : accès restreint pour la sécurité>

---

## 4. Exigences fonctionnelles (FR)
> Forme recommandée : “Le système doit…”
- **FR-1 :** Création de compte : Le système doit permettre à un utilisateur de créer un compte client.
Critères de validation : Email valide + mot de passe valide donne compte créé, Email déjà utilisé donne un message d’erreur clair, mot de passe vide ou invalide donne un message d’erreur.
- **FR-2 :** Authentification: Le système doit permettre à un utilisateur de se connecter.
Critères :
Identifiants valides donne accès au tableau de bord, Identifiants invalides donne message d’erreur., Utilisateur non inscrit donne accès refusé.
- **FR-3 :** Ajout de revenu : Le système doit permettre à l’utilisateur d’ajouter un revenu (salaire, bourse, autre).
Critères :
Montant positif donne revenu enregistré, Montant négatif ou nul donne erreur affichée, Données sauvegardées en base.
- **FR-4 :** Ajout de dépense : Le système doit permettre à l’utilisateur d’ajouter une dépense avec catégorie et fréquence (journalière, hebdomadaire, mensuelle).
Critères :
Montant positif donne dépense enregistrée, Catégorie obligatoire donne sinon message d’erreur, Fréquence correctement enregistrée.
- **FR-5 :** Modification / suppression : Le système doit permettre à l’utilisateur de modifier ou supprimer une transaction.
Critères :
Modification valide donne mise à jour en base, Suppression confirmée donne transaction supprimée, Tentative sur donnée inexistante donne erreur.
- **FR-6 :** Calcul automatique : Le système doit calculer automatiquement le solde.
Règle : Solde = Total Revenus – Total Dépenses
Critères :
Mise à jour immédiate après ajout/suppression, Résultat exact selon les données enregistrées.
- **FR-7 :** Résumé budgétaire
Le système doit afficher un tableau de bord contenant :
Total des revenus, Total des dépenses, Solde restant, Indication visuelle (positif / négatif)
Critères: Tableau de bord avec les elements visibles
- **FR-8 :** Recommandation simple
Le système doit proposer un message d’aide basé sur le solde.
Critères :
Solde positif donne message d’encouragement, Solde négatif donne suggestion de réduire certaines dépenses.
---

## 5. Exigences non fonctionnelles (NFR)
> Performance / sécurité / disponibilité / UX / maintenabilité…
- **NFR-1 (Performance) :** <Le temps de réponse des pages principales doit être inférieur à 5 secondes. Le système doit supporter au minimum 100 utilisateurs simultanés (simulation académique)>
- **NFR-2 (Sécurité) :** <Les mots de passe doivent être chiffrés (hashés). L’accès au tableau de bord nécessite une session active. Un utilisateur ne peut voir que ses propres données.>
- **NFR-3 (UX) :** <L’utilisateur doit pouvoir ajouter une transaction en maximum 3 clics. Interface claire, cohérente et responsive. Messages d’erreur compréhensibles.>
- **NFR-4 (Disponibilité) :** <L’application doit être accessible 95 % du temps durant la période de test.>
- **NFR-5 (Maintenabilité) :** <Code structuré (architecture claire frontend/ backend). Utilisation de Git avec commits réguliers. Documentation mise à jour.>

---

## 6. Contraintes
- **C-1 (Technologie) :** <Javascript / React et Bootstrap>
- **C-2 (Plateforme) :** <Application web>
- **C-3 (Délai) :** <respect des phases et remises selon le calendrier du cours.>
- **C-4 (Outils) :** <Git, CI/ CD, VStudio Code etc.>

---

## 7. Données & règles métier (si applicable)
- **Entités principales :** <User (id, nom, email, mot de passe); Budget (revenus, dépenses, solde); Transaction (id, type (revenu ou dépense), montant, catégorie, fréquence, date, user_id)>
- **Règles métier :** <Un utilisateur doit être authentifié pour accéder à ses données. Les montants doivent être strictement positifs. Chaque transaction appartient à un seul utilisateur. Le solde est recalculé après chaque modification.>

---

## 8. Hypothèses & dépendances

### 8.1 Hypothèses
- H-1 : <Les utilisateurs disposent d’un accès internet>
- H-2 : <Les utilisateurs saisissent des informations exactes>
- H-3 : <Le serveur reste opérationnel durant la session.>

### 8.2 Dépendances
- D-1 : <Serveur Backend fonctionnels.>
- D-2 : <Base de données operationnelle.>
- D-2 : <Environnement React correctement configuré.>

---

## 9. Critères d’acceptation globaux (Definition of Done)
Le projet est considéré terminé si :

 Toutes les FR sont développées
- Code versionné proprement (Git)
- Toutes les Fonctionnalités principales développées et testées
- Les NFR principales sont respectées
- Authentification sécurisée fonctionnelle
- Calcul du budget exact et testé
- Gestion des erreurs implémentée
- README et SRS accessibles depuis le dépôt GitHub
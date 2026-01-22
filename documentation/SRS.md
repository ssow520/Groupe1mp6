# Cahier des charges (SRS léger) — <Nom du projet>

**Équipe :** 
Souleymane Sow, Moses Kasindi, Ruth Kegmo

**Date :** <2026-01-21>  

**Version :** <v0.1 / v1.0>

---

## 1. Contexte & objectif
- **Contexte :** <La gestion du budget personnel est un défi pour de nombreuses personnes, en particulier les étudiants et les jeunes actifs. Les dépenses quotidiennes, les revenus limités et le manque d’outils simples rendent difficile le suivi financier. Ce projet s’inscrit dans un cadre académique visant à appliquer les notions vues en cours à travers le développement d’une application concrète.>
- **Objectif principal :** <Développer une application permettant aux utilisateurs de saisir leurs informations financières afin de calculer et proposer un budget adapté à leur situation personnelle.>
- **Parties prenantes :** <Utilisateur(client), Equipe de développement(étudiant), Enseignant(évaluation du projet)>

---

## 2. Portée (Scope)
### 2.1 Inclus (IN)
- IN-1 : <Création d’un compte utilisateur>
- IN-2 : <Enregistrement des revenus et des dépenses>
- IN-3 : <Calcul automatique du budget>
- IN-4 : <Proposition d’un budget adapté à la situation de l’utilisateur>
- IN-5 : <Consultation de l’historique des données saisies>

### 2.2 Exclu (OUT)
- OUT-1 : <Connexion à des comptes bancaires réels>
- OUT-2 : <Paiements en ligne>
- OUT-3 : <Application multi-devises ou internationale>
- OUT-4 : <Fonctionnalités avancées d’intelligence artificielle>

---

## 3. Acteurs / profils utilisateurs
- **Acteur Client :** <rôle : saisir ses données financières et consulter son budget, besoins : simplicité, clarté des résultats, contraintes : connaissances limitées en gestion financière>
- **Acteur Equipe :** <Rôle : gestion technique de l’application, Besoins : accès aux données pour maintenance, Contraintes : accès restreint pour la sécurité>

---

## 4. Exigences fonctionnelles (FR)
> Forme recommandée : “Le système doit…”
- **FR-1 :** Le système doit permettre à un utilisateur de créer un compte client
- **FR-2 :** Le système doit sauvegarder les données de l’utilisateur dans une base de données
- **FR-3 :** LLe système doit permettre à l’utilisateur de saisir ses revenus
- **FR-4 :** Le système doit permettre à l’utilisateur de saisir ses dépenses
- **FR-5 :** Le système doit calculer automatiquement le budget à partir des données saisies
- **FR-6 :** Le système doit proposer un budget adéquat en fonction de la situation financière de l’utilisateur
- **FR-7 :** Le système doit afficher un résumé clair du budget

---

## 5. Exigences non fonctionnelles (NFR)
> Performance / sécurité / disponibilité / UX / maintenabilité…
- **NFR-1 (Performance) :** <Le calcul du budget doit s’effectuer en moins de 2 secondes>
- **NFR-2 (Sécurité) :** <Les données des utilisateurs doivent être protégées par une authentification>
- **NFR-3 (UX) :** <L’interface doit être simple et intuitive, avec un parcours utilisateur clair>
- **NFR-4 (Qualité) :** <Le code doit être structuré, commenté et facile à maintenir>

---

## 6. Contraintes
- **C-1 (Technologie) :** <langage / framework imposé>
- **C-2 (Plateforme) :** <web / mobile / desktop>
- **C-3 (Délai) :** <dates de phases>
- **C-4 (Outils) :** <Git, CI, etc.>

---

## 7. Données & règles métier (si applicable)
- **Entités principales :** <User (id, nom, email, mot de passe); Budget (revenus, dépenses, solde)>
- **Règles métier :** <Un utilisateur doit être authentifié pour accéder à son budget; Le budget est calculé comme : revenus – dépenses;Les montants doivent être positifs>

---

## 8. Hypothèses & dépendances
### 8.1 Hypothèses
- H-1 : <Les utilisateurs disposent d’un accès internet>
- H-2 : <Les utilisateurs saisissent des données exactes>

### 8.2 Dépendances
- D-1 : <Serveur web et base de données fonctionnels>
- D-2 : <Environnement de développement stable>

---

## 9. Critères d’acceptation globaux (Definition of Done – mini)
- [ ] Fonctionnalités principales développées et testées
- [ ] estion minimale des erreurs
- [ ] Calcul du budget fonctionnel
- [ ] Documentation à jour (UML + ADR si requis)
- [ ] Application conforme aux exigences du cahier des charges
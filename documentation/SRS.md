# Cahier des charges (SRS léger) — Application de gestion de budget

**Équipe :**  
Souleymane Sow, Moses Kasindi, Ruth Kegmo

**Date :** 2026-01-23  

**Version :** v1.0

---

## 1. Contexte & objectif
- **Contexte :** La gestion du budget personnel est un défi pour de nombreuses personnes, en particulier les étudiants et les jeunes actifs. Les dépenses quotidiennes, les revenus limités et le manque d’outils simples rendent difficile le suivi financier. Ce projet s’inscrit dans un cadre académique visant à appliquer les notions vues en cours à travers le développement d’une application concrète.
- **Objectif principal :** Développer une application permettant aux utilisateurs de saisir leurs informations financières afin de calculer et proposer un budget adapté à leur situation personnelle.
- **Parties prenantes :** Utilisateur (client), Équipe de développement (étudiants), Enseignant (évaluation du projet)

---

## 2. Portée (Scope)

### 2.1 Inclus (IN)
- IN-1 : Création d’un compte utilisateur
- IN-2 : Enregistrement des revenus et des dépenses
- IN-3 : Calcul automatique du budget
- IN-4 : Proposition d’un budget adapté à la situation de l’utilisateur
- IN-5 : Consultation de l’historique des données saisies

### 2.2 Exclu (OUT)
- OUT-1 : Connexion à des comptes bancaires réels
- OUT-2 : Paiements en ligne
- OUT-3 : Application multi-devises ou internationale
- OUT-4 : Fonctionnalités avancées d’intelligence artificielle

---

## 3. Acteurs / profils utilisateurs
- **Acteur Client :** saisir ses données financières et consulter son budget.  
  Besoins : simplicité, clarté des résultats  
  Contraintes : connaissances limitées en gestion financière

- **Acteur Équipe :** gestion technique de l’application  
  Besoins : accès aux données pour maintenance  
  Contraintes : accès restreint pour la sécurité

---

## 4. Exigences fonctionnelles (FR)

### FR-01 : Création de compte
Le système doit permettre à un utilisateur de créer un compte.

**Critères de validation :**
- Email valide → compte créé  
- Email déjà utilisé → message d’erreur  
- Mot de passe < 8 caractères → refus  
- Champs vides → message obligatoire  

### FR-02 : Sauvegarde des données
Le système doit sauvegarder les données de l’utilisateur dans une base de données.

**Critères de validation :**
- Données correctement saisies → sauvegarde réussie  
- Base de données indisponible → message d’erreur  
- Champs invalides → refus de sauvegarde  

### FR-03 : Saisie des revenus
Le système doit permettre à l’utilisateur de saisir ses revenus.

**Critères de validation :**
- Montant positif → revenu enregistré  
- Montant négatif ou non numérique → message d’erreur  
- Champ vide → message obligatoire  

### FR-04 : Saisie des dépenses
Le système doit permettre à l’utilisateur de saisir ses dépenses.

**Critères de validation :**
- Montant positif → dépense enregistrée  
- Montant négatif ou non numérique → message d’erreur  
- Champ vide → message obligatoire  

### FR-05 : Calcul automatique du budget
Le système doit calculer automatiquement le budget à partir des données saisies.

**Critères de validation :**
- Revenus ≥ dépenses → budget calculé correctement  
- Revenus < dépenses → budget négatif affiché  
- Données manquantes → message d’erreur  

### FR-06 : Recommandations simples
Le système doit afficher des recommandations simples si les dépenses dépassent les revenus.

**Critères de validation :**
- Dépenses > revenus → message de recommandation affiché  
- Dépenses ≤ revenus → aucune recommandation nécessaire  
- Données manquantes → message d’erreur  

### FR-07 : Résumé du budget
Le système doit afficher un résumé clair du budget.

**Critères de validation :**
- Revenus, dépenses et solde correctement affichés  
- Résumé lisible et format cohérent  
- Données manquantes → message d’erreur  

---

## 5. Exigences non fonctionnelles (NFR)

- **NFR-01 (Performance) :** Le calcul du budget doit s’effectuer en moins de 2 secondes  
- **NFR-02 (Sécurité) :** Les données des utilisateurs doivent être protégées par une authentification  
- **NFR-03 (UX) :** L’interface doit être simple et intuitive, avec un parcours utilisateur clair  
- **NFR-04 (Qualité) :** Le code doit être structuré, commenté et facile à maintenir  

---

## 6. Contraintes

- **C-01 (Technologie) :** Javascript / React et Bootstrap  
- **C-02 (Plateforme) :** Web / Desktop  
- **C-03 (Délai) :** Dates de phases définies par le cours  
- **C-04 (Outils) :** Git, CI/CD, Visual Studio Code  

---

## 7. Données & règles métier

**Entités principales :**  
- User (id, nom, email, mot de passe)  
- Revenu (id, montant, source, date, userId)  
- Dépense (id, montant, catégorie, date, userId)  
- Budget (id, solde, userId)  

**Règles métier :**  
- Un utilisateur doit être authentifié pour accéder à son budget  
- Le budget est calculé comme : revenus – dépenses  
- Les montants doivent être positifs  

---

## 8. Hypothèses & dépendances

### 8.1 Hypothèses
- H-1 : Les utilisateurs disposent d’un accès internet  
- H-2 : Les utilisateurs saisissent des données exactes  

### 8.2 Dépendances
- D-1 : Serveur web et base de données fonctionnels  
- D-2 : Environnement de développement stable  

---

## 9. Critères d’acceptation globaux (Definition of Done – mini)
- [ ] Un utilisateur peut créer un compte et retrouver ses données après reconnexion  
- [ ] Fonctionnalités principales développées et testées  
- [ ] Gestion minimale des erreurs et exceptions  
- [ ] Calcul du budget fonctionnel  
- [ ] Documentation à jour (UML + ADR si requis)  
- [ ] Application conforme aux exigences du cahier des charges

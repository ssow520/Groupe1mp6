# Guide général – Phase 1 (Repo + SRS)
**Objectif :** transformer tous les retours de correction Phase 1 en **une checklist unique** et un **mode d’emploi** pour produire un dépôt propre + un SRS “pilotable” (exploitable pour planifier, tester, et répartir le travail).

---

## 1) Ce qui fait gagner des points (ce qu’on attend en Phase 1)
### A) Un projet faisable et bien cadré
- Sujet **clair** + valeur utilisateur explicite. 
- Scope **IN/OUT** raisonnable : vous excluez volontairement les features lourdes (paiement, prédiction, social avancé, etc.) pour rester faisable sur une session. 

### B) Un SRS structuré et complet (même si V1)
- Sections présentes : contexte/objectif, parties prenantes, scope IN/OUT, FR, NFR, contraintes, hypothèses/dépendances, données & règles métier.

### C) Des exigences déjà orientées “test”
- Les FR existent et couvrent le cœur du produit (même si elles doivent souvent être précisées). 

---

## 2) Les problèmes les plus fréquents (et comment les corriger)
### Problème #1 — Documentation inaccessible (liens cassés / pas de lien)
**Symptômes**
- Le correcteur ne trouve pas le SRS en 1 clic (README sans lien, lien 404, fichiers rangés mais non référencés).     
- Liens SRS/ADR cassés → correction faite “en allant chercher” dans `documentation/`.                               

**Correctif attendu**
- Dans `README.md`, ajouter une section **Documentation** avec liens directs :
  - `documentation/SRS.md`
  - (optionnel) `documentation/ADR/ADR-001.md`  
Objectif : ouvrir le SRS **en un clic**.  

---

### Problème #2 — Dépôt non conforme aux bonnes pratiques Git (ex : ZIP)
**Symptôme**
- Livraison sous forme d’archive `.zip` dans le repo → impossible de suivre l’historique, les contributions, les diffs. 

**Correctif attendu**
- Mettre les fichiers `.md` **directement** dans le repo et faire des commits propres (ex : “add initial SRS”, “complete FR list”, “add NFR”). {index=8}

---

### Problème #3 — SRS “template” / placeholders / sections incomplètes
**Symptômes**
- Placeholders `<...>`, champs vides (OUT incomplet), sections “à vérifier”, incohérences de date/version.   
- OUT partiellement rempli (OUT-3/OUT-4 vides). 

**Correctif attendu**
- Zéro placeholder dans la V2.
- OUT complété avec **≥ 5 exclusions** concrètes pour empêcher le scope creep. 
---

### Problème #4 — FR trop générales (pas “testables”)
**Symptôme**
- FR “haut niveau” : on comprend l’idée, mais on ne peut pas vérifier si c’est fait. 

**Standard attendu (règle d’or)**
> **1 FR = 1 comportement observable et vérifiable.**

**Comment rendre une FR testable (modèle)**
- **Action** (verbe) : “Le système doit permettre de…”
- **Entrées** : champs requis / format attendu
- **Sortie** : résultat affiché / enregistré
- **Règles métier** : validations + droits (rôle)
- **Cas d’erreur** : quoi afficher / quoi bloquer

Exemples de précisions demandées (selon projets) :
- format CSV attendu + gestion fichiers invalides                             
- validations sur entités (ex : date future, champs obligatoires, doublons)   
- règles de workflow (statuts, transitions, permissions par rôle)           

**Cible recommandée**
- ~10–15 FR (minimum) jusqu’à 15–25 FR (max) selon la taille du projet, mais **petites et précises**. 

---

### Problème #5 — NFR vagues, non mesurables, ou incohérentes
**Symptômes**
- “Toujours disponible”, “rapide”, “sécurisé” sans métrique.             
- NFR dupliquées / mal étiquetées (souvent signe de copier-coller).      
- Incohérence (ex : Internet requis vs import CSV offline possible).    

**Standard attendu (exemples de formulations mesurables)**
- **Performance :** “95% des actions X chargent en < 2s” (préciser X : liste, recherche, détail…)
- **Disponibilité :** “99%/mois hors maintenance planifiée” (pas “toujours”).         
- **Sécurité :** hash mots de passe, rôles, sessions, minimisation des données.       
- **UX :** “import + affichage en ≤ 3 étapes”, messages d’erreur compréhensibles.     
- **Qualité :** conventions, architecture en couches, logs actions critiques.       

---

### Problème #6 — Données & règles métier insuffisantes
**Symptômes**
- Entités listées sans structure, ou placeholders “<User, Order…>”. 
- Règles métier pas reliées aux FR / workflows.

**Correctif attendu (structure simple)**
Pour chaque entité clé :
- **Entité :** (ex : Reservation)
- **Champs clés :** id, dates, statut, userId…
- **Contraintes :** unique, not null, range…
- **Règles :** qui peut créer/modifier, transitions de statut, validations

---

## 3) ADR (Architecture Decision Record) – optionnel en Phase 1
- **ADR non requis** à cette étape, mais si vous en mettez un, il doit être **rempli et cohérent** (décision, alternatives, conséquences, plan). 
- Un ADR bien rédigé peut être un **bonus** (comparaison d’alternatives, conséquences, plan d’implémentation).

---

## 4) Usage de modèles IA / texte généré : règle pratique
- Tout contenu “template” non finalisé (placeholders, doublons, sections vides) donne l’impression d’un texte généré / pas maîtrisé, et est pénalisant. 
- Certains cas incluent un **avertissement explicite** contre l’utilisation d’outils de génération pour rédiger la documentation : prenez ça au sérieux. 

👉 En pratique : vous pouvez vous aider d’outils pour reformuler, **mais** le document final doit être :
- cohérent,
- complet,
- sans placeholders,
- testable.

---

## 5) Checklist “V2” prête à appliquer (copier-coller)
### A) Repo & Git
- [ ] Pas de ZIP : fichiers `.md` directement dans le repo. 
- [ ] Dossier `documentation/` (ou `Documentation/`) clair et cohérent.
- [ ] Commits propres (plusieurs commits, pas un seul dump).  

### B) README
- [ ] Section **Documentation** avec lien direct vers `documentation/SRS.md`.   
- [ ] (Optionnel) liens ADR si vous les gardez.                                 

### C) SRS – contenu
- [ ] Zéro placeholder (`<...>`, “à vérifier”, “??”).                                         
- [ ] Scope IN/OUT complet (OUT : ≥ 5 exclusions concrètes).                                  
- [ ] FR : 10–25 max, petites, numérotées, testables.                                         
- [ ] NFR : 8–12 mesurables (perf, sécurité, disponibilité, UX, logs/traçabilité).            
- [ ] Données & règles métier structurées (entités → champs → contraintes → règles).          
- [ ] Cohérence globale (plateforme vs hypothèses, OUT vs dépendances, labels NFR, etc.).    

---

## 6) Mini-modèles réutilisables (templates “propres”)
### Modèle FR
**FR-XX :** Le système doit permettre à **[rôle]** de **[action]** afin de **[valeur]**, en respectant **[règles]**.  
- Entrées : …
- Validations : …
- Sortie : …
- Cas d’erreur : …

### Modèle NFR (mesurable)
**NFR-Perf-01 :** 95% des requêtes **[action]** répondent en **< 2s** avec un dataset de **X** éléments.  
**NFR-Avail-01 :** disponibilité **99%/mois** hors maintenance planifiée. 

---

## Conclusion
Si vous appliquez ce guide, vous obtenez automatiquement un livrable Phase 1 “fort” :
- dépôt corrigeable rapidement (liens OK, pas de ZIP),
- SRS sans placeholders,
- FR/NFR testables,
- règles métier et données structurées,
- scope maîtrisé.

> Prochaine étape logique après la V2 : transformer les FR en **backlog** (User Stories + critères d’acceptation + tâches techniques), mais ça vient après avoir verrouillé un SRS propre.

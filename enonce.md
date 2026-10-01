# TP — Travail collaboratif avec Git Flow

## Contexte

Vous travaillez en équipe de **3 à 4 développeurs** sur un petit site vitrine.

Votre objectif n'est pas uniquement de réaliser le site : vous devez surtout mettre en place et respecter un véritable workflow de développement collaboratif avec Git et GitHub.

Pendant ce TP, vous devrez utiliser :

- Les branches Git
- Git Flow
- Les Pull Requests
- Les protections de branches
- La revue de code
- La gestion de conflits
- Les branches `feature/*`
- Les branches `fix/*`
- Les branches `release/*`
- Les branches `hotfix/*`

---

# 1. Création du projet

Un membre du groupe crée un repository GitHub.

Le projet doit contenir initialement :

- `index.html`
- `style.css`
- `README.md`

Le fichier `index.html` doit contenir une structure HTML minimale.

Le fichier `style.css` peut être vide.

Effectuez un premier commit sur `main`.

Tous les membres du groupe doivent ensuite cloner le repository sur leur machine.

---

# 2. Mise en place de Git Flow

Créez une branche :

`develop`

L'organisation principale du repository doit maintenant être :

`main`
→ version stable du projet

`develop`
→ prochaine version en cours de développement

Les nouvelles fonctionnalités devront être développées dans des branches :

`feature/*`

Les corrections classiques seront réalisées dans :

`fix/*`

Les versions seront préparées dans :

`release/*`

Les corrections urgentes de production seront réalisées dans :

`hotfix/*`

---

# 3. Protection du repository

Configurez GitHub afin d'interdire le travail direct sur :

`main`

et

`develop`

Les modifications de ces branches doivent obligatoirement passer par une Pull Request.

Configurez également les règles suivantes :

- Interdire les push directs
- Obliger le passage par une Pull Request
- Exiger **2 validations** avant qu'une Pull Request puisse être fusionnée

À partir de maintenant, aucun membre du groupe ne doit directement modifier `main` ou `develop`.

---

# 4. Première phase — Développement des fonctionnalités

Chaque développeur doit créer sa propre branche à partir de `develop`.

Pour un groupe de 4 :

### Développeur 1

Branche :

`feature/header`

Créer le header du site avec :

- Nom du site
- Logo textuel
- Menu de navigation

### Développeur 2

Branche :

`feature/hero`

Créer la section principale du site avec :

- Un titre
- Un texte de présentation
- Un bouton d'appel à l'action

### Développeur 3

Branche :

`feature/services`

Créer une section présentant trois services sous forme de cartes.

Chaque carte contient :

- Un titre
- Une courte description

### Développeur 4

Branche :

`feature/footer`

Créer le footer avec :

- Nom du site
- Copyright
- Trois liens

Pour un groupe de 3, le développeur chargé de `feature/services` réalise également le footer.

---

# 5. Commits et publication

Chaque développeur travaille uniquement sur sa branche.

Effectuez plusieurs commits lorsque cela est pertinent.

Les messages de commit doivent permettre de comprendre les modifications réalisées.

Une fois la fonctionnalité terminée :

1. Publiez votre branche sur GitHub
2. Créez une Pull Request vers `develop`
3. Demandez une revue aux autres membres du groupe

Il est interdit de fusionner sa propre Pull Request immédiatement.

---

# 6. Code Review

Chaque Pull Request doit être relue par au moins **deux autres membres du groupe**.

Les reviewers doivent vérifier :

- La fonctionnalité demandée est présente
- Le HTML est correctement structuré
- Le code est lisible
- Les noms de classes CSS sont compréhensibles
- Aucun fichier sans rapport avec la fonctionnalité n'a été modifié
- La Pull Request cible bien `develop`

Un reviewer peut :

- Approuver la Pull Request
- Ajouter un commentaire
- Demander une modification

Une Pull Request nécessitant une correction ne doit pas être fusionnée.

Le développeur concerné doit effectuer la correction sur sa branche puis pousser un nouveau commit.

La Pull Request doit automatiquement être mise à jour.

Une fois les deux validations obtenues, la branche peut être fusionnée dans `develop`.

---

# 7. Gestion d'un conflit

Après l'intégration des premières fonctionnalités, deux développeurs doivent travailler simultanément sur le style global du site.

Créez depuis `develop` :

`feature/theme`

et

`feature/responsive`

## feature/theme

Modifier notamment les styles généraux du projet :

- Police
- Couleur de fond
- Couleur principale
- Styles généraux des titres

## feature/responsive

Modifier également les styles généraux et ajouter :

- Une largeur maximale au contenu
- Des adaptations pour les petits écrans
- Une modification de la taille des titres
- Une adaptation du menu

Les deux branches doivent volontairement modifier certaines lignes communes dans `style.css`.

Les deux développeurs travaillent sans attendre que l'autre ait terminé.

---

# 8. Première fusion

La branche `feature/theme` est terminée en premier.

Créez une Pull Request vers `develop`.

Effectuez la Code Review.

Après deux validations, fusionnez la Pull Request.

`develop` contient maintenant les modifications du thème.

---

# 9. Apparition du conflit

Le développeur travaillant sur :

`feature/responsive`

termine ensuite son travail.

Entre-temps, `develop` a évolué.

Avant de créer ou de finaliser la Pull Request, récupérez les modifications récentes de `develop` dans votre branche.

Un conflit doit apparaître dans `style.css`.

Analysez le conflit.

Identifiez :

- Les modifications provenant de `develop`
- Les modifications provenant de `feature/responsive`
- Les éléments qui doivent être conservés

Résolvez manuellement le conflit afin de conserver à la fois le thème et le comportement responsive.

Validez la résolution avec un commit.

Publiez la branche mise à jour.

La Pull Request peut ensuite être revue et fusionnée.

---

# 10. Correction d'un bug

Après intégration des fonctionnalités, l'équipe constate un problème :

**Sur mobile, le bouton principal dépasse de son conteneur.**

Ce bug concerne la version en cours de développement et n'est pas encore présent en production.

Créez depuis `develop` :

`fix/mobile-button`

Corrigez le problème.

Créez un commit puis publiez la branche.

Créez une Pull Request :

`fix/mobile-button` → `develop`

La Pull Request doit être validée par deux autres membres avant fusion.

---

# 11. Préparation de la version 1.0

Toutes les fonctionnalités prévues sont maintenant présentes dans `develop`.

L'équipe souhaite préparer la première version du site.

Créez depuis `develop` :

`release/1.0`

À partir de cette branche :

- Vérifiez le fonctionnement général du site
- Vérifiez les liens
- Vérifiez l'affichage mobile
- Corrigez uniquement les éventuels petits problèmes nécessaires à la livraison
- Ajoutez dans le README la mention `Version 1.0`

Aucune nouvelle fonctionnalité ne doit être ajoutée pendant cette étape.

Lorsque la version est considérée comme stable, créez une Pull Request :

`release/1.0` → `main`

Effectuez la Code Review.

Après deux validations, fusionnez la version.

La branche `main` représente maintenant la **version 1.0 en production**.

Créez sur GitHub le tag :

`v1.0`

La branche de release doit également être réintégrée dans `develop` si elle contient des corrections réalisées pendant la préparation de la version.

---

# 12. Incident en production

Après la publication de la version 1.0, un problème urgent est découvert.

**Le bouton principal de la page contient un lien incorrect et renvoie vers une page inexistante.**

La correction doit être mise en production immédiatement.

Il ne faut pas utiliser `develop`, car cette branche pourrait déjà contenir des modifications destinées à une future version.

Créez directement depuis `main` :

`hotfix/broken-link`

Corrigez uniquement le problème demandé.

Effectuez un commit puis publiez la branche.

Créez une Pull Request :

`hotfix/broken-link` → `main`

Effectuez la Code Review.

Après validation, fusionnez le hotfix.

Créez un nouveau tag :

`v1.0.1`

---

# 13. Attention : synchronisation de develop

Le bug corrigé dans `main` existe potentiellement toujours dans `develop`.

La correction doit donc également être réintégrée dans la branche de développement.

Assurez-vous que la correction du hotfix est présente dans :

`main`

et

`develop`

À la fin de cette opération, la prochaine version du projet ne doit pas réintroduire le bug corrigé en production.

---

# 14. État final attendu

À la fin du TP :

`main` contient la version stable `v1.0.1`.

`develop` contient les développements et la correction du hotfix.

Les fonctionnalités ont été développées dans des branches `feature/*`.

Une correction classique a été réalisée dans une branche `fix/*`.

Une version a été préparée dans une branche `release/*`.

Une correction urgente de production a été réalisée dans une branche `hotfix/*`.

Les branches `main` et `develop` sont protégées.

Les modifications passent obligatoirement par des Pull Requests.

Les Pull Requests nécessitent deux validations.

Un conflit Git a été rencontré et résolu.

Chaque membre du groupe a participé aux Code Reviews.

---

# Questions de synthèse

À la fin du TP, chaque groupe doit être capable d'expliquer :

1. Pourquoi les branches `feature/*` sont créées depuis `develop` et non depuis `main`.

2. Pourquoi une Pull Request est utile même lorsque le développeur sait que son code fonctionne.

3. Pourquoi deux validations ont été imposées avant un merge.

4. Pourquoi un conflit Git apparaît.

5. Pourquoi Git ne peut pas toujours résoudre automatiquement un conflit.

6. Quelle est la différence entre une branche `fix/*` et une branche `hotfix/*`.

7. Pourquoi un `hotfix` est créé depuis `main`.

8. Pourquoi la correction d'un `hotfix` doit également revenir dans `develop`.

9. Quel est le rôle d'une branche `release/*`.

10. Quelle différence existe entre `develop` et `main` dans ce workflow.
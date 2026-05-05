# Flux de travail

Découvrez une vue d’ensemble des workflows GitHub Actions, notamment les déclencheurs, la syntaxe et les fonctionnalités avancées.

## À propos des workflows

Un **workflow** est un processus automatisé configurable qui exécutera un ou plusieurs travaux. Les workflows sont définis par un fichier YAML archivé dans votre dépôt et s’exécutent lorsqu’ils sont déclenchés par un événement dans votre dépôt, ou ils peuvent être déclenchés manuellement ou selon une planification définie.

Les workflows sont définis dans l’annuaire `.github/workflows` d’un dépôt. Un référentiel peut comporter plusieurs workflows, chacun d’entre eux pouvant effectuer un ensemble de tâches différentes, telles que :

* Construire et tester les demandes de tirage
* Déployer votre application à chaque fois qu'une version est créée
* Ajout d'une étiquette à chaque fois qu'un nouveau numéro est ouvert

## Concepts de workflow de base

Un workflow doit contenir les composants de base suivants :

1. Un ou plusieurs *événements* qui déclenchent le workflow.
2. Un ou plusieurs *travaux*, dont chacun s’exécute sur un ordinateur *exécuteur* et exécute une série d’une ou plusieurs *étapes*.
3. Chaque étape peut exécuter un script que vous définissez ou une action, qui est une extension réutilisable qui peut simplifier votre workflow.

Pour plus d’informations sur ces composants de base, consultez « [Présentation des GitHub Actions](/fr/actions/learn-github-actions/understanding-github-actions#the-components-of-github-actions) ».

![Diagramme d'un événement déclenchant Exécuteur 1 pour exécuter Travail 1, lequel déclenche Exécuteur 2 pour exécuter Travail 2. Chacun des travaux est divisé en plusieurs étapes.](/assets/images/help/actions/overview-actions-simple.png)

## Déclencheurs de workflows

Les déclencheurs de workflow sont des événements qui entraînent l’exécution d’un workflow. Ces événements peuvent être les suivants :

* Événements qui se produisent dans le dépôt de votre workflow
* Événements qui se produisent en dehors de GitHub et qui déclenchent un événement `repository_dispatch` sur GitHub
* Heures planifiées
* Manuel

Par exemple, vous pouvez configurer votre workflow pour qu’il s’exécute lorsqu’un push est effectué vers la branche par défaut de votre dépôt, lorsqu’une version est créée ou lorsqu’un problème est ouvert.

Les déclencheurs de workflow sont définis avec la clé `on`. Pour plus d’informations, consultez « [Syntaxe de flux de travail pour GitHub Actions](/fr/actions/using-workflows/workflow-syntax-for-github-actions#on) ».

Les étapes suivantes se produisent pour déclencher une exécution de workflow :

1. Un événement se produit sur votre dépôt. Une référence Git et un SHA de commit sont associés à l’événement.
2. GitHub recherche dans le `.github/workflows`répertoire à la racine de votre référentiel les fichiers de workflow présents dans le commit SHA ou Git ref associé à l'événement.
3. Une exécution de workflow est déclenchée pour tous les workflows qui ont des valeurs `on:` correspondant à l’événement de déclenchement. Certains événements nécessitent également que le fichier de workflow soit présent sur la branche par défaut du dépôt pour qu’il s’exécute.

Chaque exécution de workflow utilise la version du workflow présente dans la référence Git ou le SHA de commit associés de l’événement. Lorsqu'un workflow s'exécute, GitHub définit les `GITHUB_SHA`variables d'environnement (commit SHA) et `GITHUB_REF`(Git ref) dans l'environnement du exécuteur. Pour plus d’informations, consultez « [Stocker des informations dans des variables](/fr/actions/learn-github-actions/variables) ».

Pour plus d’informations, consultez « [Déclenchement d’un workflow](/fr/actions/using-workflows/triggering-a-workflow) ».

## Étapes suivantes

Pour générer votre premier flux de travail, consultez [Création d’un exemple de workflow](/fr/actions/tutorials/creating-an-example-workflow).

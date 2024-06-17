# Workshop Git / GitHub

Bienvenue à ce workshop Git et GitHub! L'objectif de ce workshop est de vous familiariser avec les commandes de base de Git, le principe de Gitflow, et l'utilisation de GitHub, tout en intégrant Git à vos IDEs (Visual Studio et/ou Visual Studio Code).

Dans ce workshop, nous allons utiliser Git et Github pour collaborer au projet `Workshop git`. Cette collaboration consistera à ajouter son nom au fichier  `finishers.txt`. Easy 😎

Pour les plus curieux, une partie supplémentaire est disponible, à propos des conflits et d'autres commandes très utiles de git. Je vous la conseille 😁

**Ce worshop se fait en binôme** 👩‍💻👨‍💻 : certaines parties seront à faire par un seul des deux membres, mais il faut bien sûr que les deux membres suivent toutes les parties.

## Table des matières

1. **Késako ?**

2. **Parlons de Gitflow**

3. **Pré-requis**
   
   1. Installation de Git
   
   2. Création d'un compte GitHub

4. **Cloner le dépôt**
   
   1. Obtenir le lien de clonage
   
   2. Cloner le dépôt avec Git Bash
   
   3. Authentification

5. **Utilisation d'une nouvelle branche**
   
   1. Créer la branche d'un côté
   
   2. Récupérer la branche de l'autre côté

6. **1ère Modification du fichier `finishers.txt`**
   
   1. Cas général : Modification directe
   
   2. Modification avec Visual Studio
   
   3. Modification avec Visual Studio Code

7. **2ème Modification du fichier `finishers.txt` (gestion de conflit)**
   
   1. Comment éviter les conflits ?
   
   2. Comment gérer un conflit ?

8. **Pull Request sur GitHub**

9. **Commandes utiles**

10. **Faire un code Review**

## 1. Késako ?

Pour ceux qui se demandent ce qu'ils font là et s'ils auront la force d'aller plus loin dans ce workshop parce qu'ils ne savent même pas prononcer "Git", pas de panique. Voici deux vidéos expliquant les principes de Git et de Github : 

[LES BASES DE GIT (tuto débutant) - YouTube](https://www.youtube.com/watch?v=gp-k0UVOYMw&list=LL&index=2)

[Débutant : Comment utiliser GitHub - YouTube](https://youtube.com/watch?v=X3KCX99I2pQ&t=2s)

## 2. Parlons de Gitflow

Bon, maintenant on se parle entre pros. Pour bien utiliser Git, il faut respecter des conventions. L'une de ces conventions concerne la méthodologie de manipulation des branches et est largement utilisée dans le milieu du développement : c'est Gitflow.

Gitflow repose sur l'utilisation de branches spécifiques pour différentes phases du développement, permettant une séparation claire des tâches et une meilleure gestion des versions et des corrections de bugs.

### Rôles des branches

1. **main (ou master)** :
   
   - Contient le code de production stable.
   - Toujours prêt pour une mise en production immédiate.

2. **develop** :
   
   - Contient le code en cours de développement.
   - Point d'intégration pour toutes les nouvelles fonctionnalités.

3. **feature** :
   
   - Utilisée pour le développement de nouvelles fonctionnalités.
   - Dérivée de `develop` et fusionnée dans `develop` une fois terminée.
   - Convention de nommage : `feature/<nom-fonctionnalite>`, ou simplement `nom-fonctionnalite`.

4. **release** :
   
   - Utilisée pour préparer une nouvelle version.
   - Permet de corriger les bugs et de finaliser les détails avant la mise en production.
   - Fusionnée dans `main` et `develop` une fois prête.
   - Convention de nommage : `release/<version>`.

5. **hotfix** :
   
   - Utilisée pour corriger des bugs critiques en production.
   - Dérivée de `main` pour une correction rapide, puis fusionnée dans `main` et `develop`.
   - Convention de nommage : `hotfix/<description-du-bug>`.

### Processus Gitflow

1. **Développement d'une fonctionnalité** :
   
   - Créez une branche `feature` à partir de `develop`.
   - Développez la fonctionnalité, puis committez et poussez les modifications.
   - Fusionnez la branche `feature` dans `develop`.

2. **Préparation d'une nouvelle version** :
   
   - Créez une branche `release` à partir de `develop`.
   - Corrigez les bugs et finalisez les détails.
   - Fusionnez la branche `release` dans `main` et `develop`, puis créez un tag.

3. **Correction d'un bug critique** :
   
   - Créez une branche `hotfix` à partir de `main`.
   - Corrigez le bug, puis committez et poussez les modifications.
   - Fusionnez la branche `hotfix` dans `main` et `develop`, puis créez un tag si nécessaire.



Gitflow permet ainsi de structurer efficacement le développement, la préparation des versions et la correction rapide des bugs, tout en maintenant une qualité de code élevée.

## 3. Pré-requis

#### Installation de Git

*Cette partie est à effectuer par les deux membres du binôme.*

1. **Windows**:
   
   - Téléchargez Git à partir de [git-scm.com](https://git-scm.com/download/win).
   - Suivez les instructions pour l'installation.

2. **macOS 😔**:
   
   - Utilisez Homebrew:
     
     ```bash
     brew install git
     ```

3. **Linux**:
   
   - Utilisez votre gestionnaire de paquets:
     
     ```bash
     sudo apt-get install git # Debian/Ubuntu
     sudo yum install git # CentOS/RHEL
     ```

#### Création d'un compte GitHub

1. Allez sur [github.com](https://github.com) et cliquez sur "Sign up".
2. Suivez les instructions pour créer un compte.

## 4. Cloner le dépôt

*Cette partie est à effectuer par les deux membres du binôme.*

Pour cloner un dépôt GitHub, vous devez d'abord obtenir le lien de clonage du dépôt. Voici les étapes détaillées pour trouver ce lien et cloner le dépôt à l'aide de Git Bash.

### Obtenir le lien de clonage

1. **Accédez à GitHub :**
   
   - Ouvrez votre navigateur web et allez sur [GitHub](https://github.com).

2. **Trouvez le dépôt "Workshop git" :**
   
   - Connectez-vous à votre compte GitHub si ce n'est pas déjà fait.
   - Accédez à la page du dépôt "Workshop git". Si vous ne trouvez pas le dépôt, vous pouvez le rechercher dans la barre de recherche en haut de la page en entrant "Workshop git" ou le nom exact du dépôt que vous avez créé.

3. **Accédez à la page du dépôt :**
   
   - Cliquez sur le dépôt "Workshop git" pour accéder à sa page principale.

4. **Copiez le lien de clonage :**
   
   ![image]()
   
   - Sur la page principale du dépôt, cherchez le bouton vert "Code" en haut à droite de la liste des fichiers.
   
   - Cliquez sur le bouton "Code" pour ouvrir un menu déroulant.
   
   - Dans ce menu, vous verrez plusieurs options, y compris l'URL de clonage du dépôt.
     
     - **Clonage via HTTPS :** Cliquez sur l'icône de copie à côté de l'URL commençant par `https://`.
     - **Clonage via SSH :** Si vous avez configuré une clé SSH, vous pouvez cliquer sur l'onglet "SSH" et copier l'URL commençant par `git@github.com:`.
     
     Dans notre cas, on va utiliser *HTTPS*

### Cloner le dépôt avec Git Bash

1. **Ouvrez Git Bash :**
   
   - Si vous utilisez Windows, vous pouvez ouvrir Git Bash avec un clic droit dans le répertoire où vous souhaitez cloner le dépôt
   
   <img title="" src="file:///C:/Users/louisc/AppData/Roaming/marktext/images/2024-06-06-16-45-13-image.png" alt="" width="390" data-align="center">

2. **Cloner le dépôt :**
   
   - Utilisez la commande `git clone` suivie de l'URL que vous avez copiée.
     
     ```bash
     git clone https://github.com/ApitechFR/workshop-git.git
     ```
   
   - Si vous utilisez SSH :
     
     ```bash
     git clone git@github.com:ApitechFR/workshop-git.git
     ```

3. **Accédez au répertoire cloné :**
   
   - Une fois le clonage terminé, naviguez dans le répertoire du dépôt cloné :
     
     ```bash
     cd workshop-git
     ```

### Authentification

1. **Clonage via HTTPS :**
   
   - Si vous utilisez l'URL HTTPS, vous serez invité à entrer votre nom d'utilisateur et votre mot de passe GitHub.

2. **Clonage via SSH :**
   
   - Si vous utilisez l'URL SSH, vous devez avoir une clé SSH configurée sur votre machine et ajoutée à votre compte GitHub. Si ce n'est pas déjà fait, vous pouvez suivre les instructions pour [générer une nouvelle clé SSH](https://docs.github.com/en/authentication/connecting-to-github-with-ssh) et l'ajouter à votre compte GitHub.

## 5. Utilisation d'une nouvelle branche

À ce stade, la situation ressemble à ça : 

![](C:\Users\louisc\AppData\Roaming\marktext\images\2024-06-12-17-02-27-image.png)

### Créer la branche d'un côté

*Cette partie est à effectuer par le membre A, avec toute l'attention du membre B.*

Gitflow préconise l'utilisation de branches pour différentes étapes du développement. Pour ce workshop, nous allons créer une branche à partir de `develop`.

Créons une nouvelle branche portant le nom du binôme (pour l'exemple je prends "tic-et-tac", mais trouvez votre propore style) dérivée de develop :

```bash
git checkout develop #on se met sur develop
git checkout -b tic-et-tac #on se met sur une nouvelle branche tic-et-tac
```

![](C:\Users\louisc\AppData\Roaming\marktext\images\2024-06-12-17-03-08-image.png)

C'est la commande `git push` qui nous permettra de mettre la branche sur le dépôt.

Vous allez me dire "Ok, alors allons-y pour `git push` 🥱". Malheureusement la vie n'est pas si facile...

En effet, la branche que vous avez créée n'existe que sur votre ordinateur. Si vous tapez `git push`, git va chercher une branche `<tic-et-tac>` sur le dépôt pour y déposer le contenu de votre branche locale, et bien entendu il ne va pas la trouver.

Heureusement, Git a tout prévu, et en particulier la commande `git push -u` (ou `git push --set-upstream`), qui est utilisée pour définir une branche distante de suivi pour la branche actuelle.

Dans notre cas, on peut donc taper :

```bash
git push -u origin tic-et-tac
```

`origin` étant le mot clé désignant le dépôt.

![](C:\Users\louisc\AppData\Roaming\marktext\images\2024-06-12-17-03-39-image.png)

### Récupérer la branche de l'autre côté

*Cette partie est à effectuer par le membre B, avec toute l'attention du membre A*

Nous voulons que les binômes A et B travaillent sur la même branche, donc il faut que B récupère la branche créée par A.

Rien de plus simple, pour cela on tape la commande :

```bash
git fetch
```

## ![](C:\Users\louisc\AppData\Roaming\marktext\images\2024-06-12-17-04-07-image.png)

## 6. 1ère Modification du fichier `finishers.txt`

*Cette partie est à réaliser par le membre A, avec toute l'attention du membre B.*

Ici, on va voir et expliquer tout le process pour la modification d'un fichier du projet. Dans un premier temps, pour faciliter la compréhension, on parlera d'un cas général en détaillant chaque étape. Dans un second temps, on verra comment utiliser Visual Studio et Visual Studio Code pour faire les choses plus facilement.
Prêt ? C'est parti !🏃‍♂️

Voilà, en image et en résumé, ce que l'on va faire ici : 

![](C:\Users\louisc\AppData\Roaming\marktext\images\2024-06-13-17-03-45-image.png)

### Cas général : Modification directe

1. Ouvrez `finishers.txt` dans un éditeur de texte.
2. Ajoutez uniquement vos prénom et nom (sous la forme "Prénom Nom") à la fin du fichier.
3. Sauvegardez le fichier.
4. Ouvrez maintenant git bash dans le dossier du projet (sous Windows, clic droit > "git bash here")

#### Add

C'est la commande `git add` qui est utilisée pour ajouter des modifications à l'index (ou staging area) de Git, en préparation pour un commit. Elle indique à Git de suivre les modifications apportées aux fichiers spécifiés, en les incluant dans le prochain commit. Par exemple, après avoir modifié un fichier, vous utilisez `git add <nom-du-fichier>` pour inclure ces modifications. Vous pouvez aussi utiliser `git add .` pour ajouter toutes les modifications dans le répertoire courant.

Dans notre cas, on peut donc taper :

```bash
git add finishers.txt
```

#### Commit

La commande `git commit` est utilisée pour enregistrer les modifications ajoutées à l'index (ou staging area) dans l'historique du dépôt. Chaque commit représente un point de sauvegarde de l'état du projet, incluant un message descriptif qui explique les changements apportés. Par exemple, après avoir ajouté des modifications avec `git add`, vous utilisez `git commit -m "Message descriptif"` pour créer un nouveau commit. Le message doit être clair et concis, décrivant la nature des changements effectués. Cette commande permet de garder un historique détaillé des évolutions du projet, facilitant ainsi le suivi des modifications et la collaboration avec d'autres développeurs.

Dans notre cas, on peut donc taper :

```bash
`git commit -m "Ajout de tic-et-tac à finishers.txt"
```

#### Push

On a déjà pushé la branche une première fois, donc on peut simplement taper : 

```bash
git push
```

### Modification avec Visual Studio

Refaisons tout ça beaucoup plus simplement grâce à un outil rapide, robuste et parfaitement stable : Visual Studio.

1. Ouvrez le projet `workshop-git` dans Visual Studio.
2. Ouvrez `finishers.txt`.
3. À côté de votre nom, inscrivez votre film préféré. Si êtes un(e) vrai(e) cinéphile, vous pouvez inscrire "Prénom Nom - Les Bronzés 3" par exemple.
4. Sauvegardez le fichier.
5. Intégrez Git à Visual Studio 
6. Allez dans "Team Explorer" > "Git Changes".

Ici, on peut observer les modifications effectuées, et les ajouter au prochain commit directement depuis Visual Studio.

### Modification avec Visual Studio Code

1. Ouvrez le projet `workshop-git` dans VSCode.
2. Ouvrez `finishers.txt`.
3. À côté de votre nom et votre film préféré, ajouter votre animal préféré. Par exemple, si vous êtes féru de chasse, vous pouvez écrire "Prénom Nom - Les Bronzés 3 - Sanglier".
4. Sauvegardez le fichier.
5. Intégrez Git à VSCode via l'extension Git intégrée.

Ici, on peut observer les modifications effectuées, et les ajouter au prochain commit directement depuis Visual Studio Code.

## 7. 2ème Modification du fichier `finishers.txt` (gestion de conflit)

### Comment gérer un conflit ?

*Cette partie est à effectuer par le du membre B, avec l'attention du membre A.*

Le membre A vient de faire sa modification. C'est donc à votre tour. 

- Ouvrez le projet `workshop-git` dans un explorateur de fichiers
- Ouvrez `finishers.txt` dans un éditeur de texte
- Ajoutez directement votre nom, votre film préféré, et votre animal préféré à la fin du fichier. Par exemple, si vous êtes mordu de danse, vous pouvez écrire "Prénom Nom - Dirty Dancing - Samba".
- Sauvegardez le fichier.
- Utilisez git bash pour add, commit et push

Là, si vous avez bien travaillé, il devrait y avoir un problème. Et quel problème.... 

Ce qui se passe est un "conflit". Cela arrive parce que vos modifications ont pour point de départ une version du fichier qui n'est plus d'actualité. Par conséquent git ne sait pas quelle modification choisir entre la vôtre et celle de votre binôme. Pour vous l'indiquer, la mention `MERGING` est affichée à côté du nom de la branche dans git bash.

Pour vous aider à résoudre le conflit, git a une stratégie qui est de vous afficher les 2 versions pour que vous choisissiez quelles modifications garder.

Ouvrez votre projet sur Visual Studio Code, puis cliquez sur finisers.txt depuis l'onglet Git.

Les parties conflictuelles du fichier se colorent et VSCode vous propose différentes solutions : "Accept current change", "Accept incoming", "Accept both", "Compare". Dans notre cas, on veut bien sûr conserver les deux modifications, donc on clique sur "Accept both changes".

Magie, tout est réglé.

Faites un Add, Commit et Push une nouvelle fois, et tout va de nouveau bien se passer.

### Comment éviter les conflits ?

Pour éviter les conflits, vous devez vous assurer en permanence que votre branche locale a les dernières modifications apportées à la branche distante. Pour la mettre à jour, il vous suffit de faire un `git pull`. Si des conflits surviennent, vous savez les régler maintenant 😉

## 8. Pull Request sur GitHub

*Cette partie est toujours à effectuer par le du membre B, avec l'attention du membre A.*

On a fait le plus dur. Maintenant, votre code est sur la branche `tic-et-tac` du dépôt. Mais nous, on veut mettre ça sur la branche develop. Et pour ça, il va falloir faire une demande via Github : une Pull Request (entre pros on dit une PR). Vous serez peut-être surpris d'apprendre qu'une "Pull Request" sur GitHub est l'équivalent d'une "Merge Request" sur GitLab.

Bon, au travail.

1. Allez sur le dépôt GitHub.
2. Cliquez sur "New Pull Request".
3. Sélectionnez votre branche `tic-et-tac` comme branche source et `develop` comme branche de destination.
4. Cliquez sur "Create Pull Request".
5. Ajoutez un titre et une description pour la Pull Request.
6. Soumettez la Pull Request et attendez une revue.
7. Une fois la revue faite, **et seulement après**, vous pouvez merger la PR pour que vos changements arrivent sur develop.
8. Si tout est ok, il est recommandé de supprimer la branche de travail, c'est à dire `tic-et-tac`. Sinon il y aura 51465857 branches sur le repo et quand dans 2 ans un(e) développeur(euse) reprendra le projet il ne sera pas très heureux(se). Pensez à lui(elle).

### 9. Faire un code Review

*Cette partie est toujours à effectuer par le du membre A, avec l'attention du membre B.*

Voyons ce que ça donne de l'autre côté du miroir. Supposons qu'un(e) de vos collègues ait fait une PR et vous demande de la relire. Ça peut arriver, il faut se préparer à tout.

À cette occasion, vous recevez ce message : 

*Coucou! J'ai fini de coder le machin qu'il manquait au truc pour que le bidule fonctionne comme indiqué dans les specs! Je te donne le lien de la PR, tu peux la review ASAP ?*

Vous ne pouvez plus reculer, vous êtes pris au piège... Cliquez sur le lien et rendez-vous sur la PR. Ici, vous pouvez voir les modifications faites par votre collègue, et vous pouvez choisir d'approuver ou de rejeter la PR. Vous pouvez également faire un commentaire et ne pas approuver tout de suite.

Vous pouvez également faire une suggestion de modification pour faciliter la vie de votre collègue.

## 10. Commandes utiles

Ce workshop aborde les points élémentaires de Git, mais vous vous trouverez aussi dans des situations moins conventionnelles.

Les commandes présentées ci-après ne sont pas accessoires, elles sont vraiment importantes et **vous en aurez besoin**.

Voici donc quelques commandes Git que vous pouvez utiliser pour vous en sortir :

- `git pull` : Vous permet de récupérer sur votre machine la dernière version de la branche courante sur le dépôt. Par exemple, si vous êtes actuellement sur la branche `develop`, un `git pull` mettra sur votre machine la version de `develop` du dépôt.

- `git pull origin <nom-de-branche>` : Cela permet de récupérer sur votre branche courante la version de la branche `<nom-de-branche>` du dépot. Par exemple, si vous travaillez sur une branche `a` en local et que vous voulez récupérer les changements posés sur `develop` par un(e) collègue, vous pouvez aller sur la branche `a` et taper `git pull origin develop`.

- `git status` : Vous permet de visualiser les modifications en local, notamment voir celles qui sont `staged` et celles qui ne sont pas.

- `git reset --soft HEAD^1` : Cette commande supprime votre précédent commit et passe les modifications qu'il contenait dans l'état `staged`, c'est à dire comme si vous veniez de faire un `git add .`. `HEAD^1` indique que vous souhaitez annuler le dernier commit. En inscrivant `HEAD^2`, ce sont les 2 derniers qui seront annulés.

- `git restore <filename>` : Cela vous permet de faire passer un fichier de l'état de `staged` à l'état de `unstaged`. Plus simplement, cela sert à annuler un `git add`. on peut remplacer `<filename>` par `.` pour prendre en compte tous les fichiers dans l'état `staged`

- `git stash` : Cette commande permet de mettre des modifications de côté. Ils sont alors `stashed`.

- `git stash clear` : Supprimer le contenu de la liste des éléments `stashed`.

- `git stash apply` : Appliquer les changements mis de côté dans la liste des `stashed`.

- `git branch -D <nom-de-branche>` : Supprime la branche locale `<nom-de-branche>`.

- `git fetch --all` : Récupère les changements d'obets et de références du dépôt. Globalement, cela sert à récupérer une branche du dépôt qui n'existe pas en local. Si Jean-Michel a créé une branche `a` et l'a mise sur le dépôt, vous pouvez taper `git fetch --all` pour que vous puissiez aussi travailler sur sa branche.

- `git bisect` : Cette commande est moins necessaire, mais extrêmement utile en cas de coup dur. Elle sert à détecter quel commit est responsable d'un bug, et facilite donc la correction. Je vous invite à aller voir dans la documentation pour en savoir davantage.

Si quelque chose n'est pas clair, allez voir la documentation Git, qui est très complète et très instructive.

### Conclusion

Ce workshop vous a permis de comprendre les commandes de base de Git, le principe de Gitflow, et l'utilisation de GitHub, tout en intégrant Git à vos IDEs. Pratiquez régulièrement ces commandes et conventions pour devenir plus efficace dans la gestion de vos dépôts Git.

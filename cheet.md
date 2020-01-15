# Git - Gestionnaire de Versions
## 1. Objet du document
			
L'objet de ce document est de donner une définition au logiciel Git et de détailler les principales commandes d'utilisation.

### 1.1 Définition

Git est un système de contrôle de version open source gratuit, créé par Linus Torvalds, en 2005. C'est un logiciel distribué : chaque développeur dispose en local de l'historique complet du dépôt de son code. Un serveur est très souvent utilisé en tant que point de rencontre entre les développeurs : Le serveur connaît l’historique des modifications et permet l’échange d’informations entre les développeurs, qui eux possèdent également l’historique des modifications.

![Schema de logiciel distribué avec un serveur](https://user.oc-static.com/files/236001_237000/236864.png)

* Liens intéressants :
	* [Et si vous compreniez enfin Git et GitHub ?](https://blog.lesieur.name/comprendre-et-utiliser-git-avec-vos-projets/)

## 2. Création de repository (local et remote)

	Petit rappel les <...> indique qu'il s'agit d'un paramètre à inserer 
	Tandis que les [...] indique un paramètre facultatif.

### 2.1 Le repository local
	git init          -> permet de créer un repository en local 
	git clone <URL>   -> permet de cloner("copier") un repository distant sur son propre ordinateur dans un repository local.
			     permet d'avoir toutes les anciennes versions du projet contenu dans le repository distant. 
### 2.2 Le repository remote (à distance)
	git remote       	     -> permet de voir tout les repository distants existants.
	git fetch [<NOM>]	     -> permet de recuperer des données depuis un repository distant.
	git remove <NOM> 	     -> supprime un repository distant.
	git add <NOM> <URL>	     -> permet d'ajouter un nouver repository distant.
	git pull         	     -> permet de recuperer le contenue d'un repository distant et met le nouveau contenu du repository local dans le working directory.
			    	       ! correspond a un git fetch suivi d'un git merge !
	git push [<NOM> [<BRANCHE>]] -> Envoyer les dernières versions (commits) de la branche du repository local à la même branche du repository remote.
					Envoyer son travail vers les repository distant. Fair d'abord un git add et git commit.
	On peut également créer un repository en ligne directement sur github.com en appuyant sur New en haut gauche de la page il suffit ensuite de remplir les différents champs. On peut le mettre en publique ou bien privé également et récuperer son url.

## 3. Définition des 3 états possibles (working directory, staging area, et repository)
![Schema](https://miro.medium.com/max/686/1*diRLm1S5hkVoh5qeArND0Q.png)
### 3.1 Définition de working directory

<p>La zone de travail ou working directory est l'espace où se trouvent les fichiers tout juste modifiés.</p>


## 4. Definition des commandes `git add`  &  `git commit`

### 4.1 ADD
`git add <nomDuFichier>`

<p> Stages the files, ready for commit </p>

<p>La commande <i>git add</i> permet l'ajout d'un fichier du working directory à la staging area</p>

commande associée | Definition
--- | --- 
`-f` ou `--force` | Autoriser l'ajout de fichiers autrement ignorés.
`-n` ou `--dry-run` | N'ajoutez pas réellement le ou les fichiers, montrez simplement s'ils existent et / ou seront ignorés.


### 4.2 COMMIT

`git commit <nomDuFichier>`

<p> commit all staged files to versioned history </p>

<p>La commande <i>git commit </i> permet l'ajout d'un fichier de la staging area au repository. L'execution de cette commande lance un editeur de texte afin de préciser la description synthétique du commit </p>

commande associée | Definition
--- | --- 
`-m "commit message"` | Utilisez le < commit message> donné comme message de validation. Si plusieurs -m options sont données, leurs valeurs sont concaténées en paragraphes séparés. L' -m option est mutuellement exclusive avec -c, -Cet -F.
`--cleanup = <mode>` | Cette option détermine comment le message de validation fourni doit être nettoyé avant la validation. Le <mode> peut être strip, whitespace, verbatim, scissorsou default.
`-a` ou `--all`| commit tous les fichiers qui ont été modifiés et supprimés, mais les nouveaux fichiers dont vous n'avez pas parlé à Git ne sont pas affectés.


## 5. Commandes pour vérifier l'état des fichiers (status et diff)
###  5.1 Le git status: 
Montre les chemins qui ont des différences entre le fichier d’index et le commit HEAD actuel.
	Exemple: Avant d'effectuer une modification -> ```git status``` : Sur la branche tp3-blabla-monNom, 
																		rien à valider, la copie de travail est propre

###  5.2 Le git diff:
C'est une commande multi-fonction qui affiche les modifications entre l’arbre de travail et l’index ou un arbre, les modifications entre l’index et un arbre, les modifications entre deux arbres, les modifications entre deux objets blobs ou les modifications entre deux fichiers sur disque.
	Exemple: Mon texte initial est 'blabla' et je le change en blapbloup -> ```git diff``` : - bla 
																							 + pbloup
							

## 6.Commande pour vérifier l'historique des modifications (log)

### 6.1 Terminaison 
git-log - Afficher les journaux de validation

### 6.2 Ecriture 
git log [<options>] [<plage de révision>] [[--] <chemin>…​]

### 6.3 A quoi ça sert ?!
Le log de Git est un outil formidable pour analyser l’historique des commits et resituer un contexte. Il nous permet aussi bien de suivre un projet dans sa globalité que dans ses détails : fonctionnalités, correctifs, fichiers et répertoires, auteurs, dates…

### 6.4 Pourquoi l'utilser ?!
#### 6.4.1.Afficher un historique pour se resituer
  Limiter la profondeur/le nombre de commits affichés
  Limiter le suivi à certains fichiers et répertoires
  Voir les modifications introduites par chaque commit
#### 6.4.2.Voir l’historique récent des branches
  cibler une branche dédiée
  cibler un motif de branche (feat/*)
#### 6.4.3 Vérifier le travail terminé
  Voir les fusions effectuées
  Lister les commits entre 2 versions
#### 6.4.4 Rechercher
  Dans les métadonnées du commit : dates, auteur, message…
  Dans les modifications introduites par les commits :
      - les ajouts et suppressions du texte recherché
      - les changements survenus autour d’un texte connu (sur la même ligne)
  Dans un fichier précis, les évolutions d'un fragment (typiquement le corps d’une fonction/méthode)
  Obtenir des statistiques pour le projet

## 7.Commandes pour revenir en arrière (reset)
### 7.1 Que fait le git reset
Le git reset permet d’agir sur notre historique de versions et notre travail en cours. Concretement, il réintialise la HEAD actuelle à l'état spécifié.
### 7.2 Qu'est-ce que le HEAD ?
Head est un pointeur. En temps normal HEAD est positionné sur une branche qui constitue une référence, et qui est positionnée sur un commit. Lorsqu'un nouveau commit est créé, la branche se positionne sur ce nouveau commit, et HEAD suit la branche.
### 7.3 Comment cibler une version antérieur ?
La première chose à faire pour revenir à une version antérieure est d'abord de repérer cette version. La commande git log liste les différents commit (enregistrements) effectués. La chaîne de caractères situé à côté du mot commit permet d'identifier l'enregistrement. Elle sera utilisée dans toutes les commandes nécessitant un numéro d'enregistrement.
### 7.4 Comment revenir en arrière ? 
Il est possible de revenir en arrière et de supprimer toutes les modifications qui ont été enregistrées depuis la révision mais la commande ne sera pas la même si vous ayez publié les commits ou non.
Si vos commits n'ont pas été publiés, il suffit de revenir à la version antérieure du répertoire de travail grâce à la commande git reset :
--> git reset --hard {numéro de version}
Si vous possédez des modifications non enregistrées dans votre répertoire de travail et que vous souhaitez les conserver, il faut exécuter en plus la commande get stash.
--> git stash #sauvegarde les modifications
--> git reset --hard {numéro de version}
 remet à zéro le répertoire de travail par rapport à la révision spécifiée
git stash pop #applique les modifications sauvegardées
Si un fichier est concerné à la fois par les modifications en cours et le retour à la version antérieure du répertoire de travail, il y aura un conflit à résoudre.

## 8.Commandes liées aux branches (création, vérification et changement de branche
###  8.1 definition de Branch 

Une branche dans Git est simplement un pointeur léger et déplaçable vers un de ces commits. La branche par défaut dans Git s'appelle master.

###  8.2 Commande git branch

Nous obtenons la liste de toutes les branches, la branche actuelle sera marquée du caractère * avec la couleur verte

`git branch`

###  8.3 Comment créer une nouvelle branche

`git branch  [nom de votre nouvelle Branche]` 

###  8.4 Renommez la branche actuelle 

`git branch -m <nouveau nom de la branche>`

###  8.5 Passer à une branche existante appelée "branche-nom"

`git checkout <branch_name>`

## 9.Commandes pour la synchronisation (merge et rebase)

### 9.1 Definition Merge

Comme son nom l’indique, merge réalise une fusion. On souhaite faire avancer la branche courante de sorte qu’elle incorpore le travail d’une autre branche.

## 9.2 Definition Rebase

Comme son nom l’indique, rebase est là pour changer la « base » d’une branche, c’est-à-dire son point de départ. Elle rejoue une série de commits à partir d’un nouvelle base de travail.

## 9.3 Utilisation


## 10.Définition et intérêt dans l'utilisation d'un repository remote (ex : Github)

### 10.1 : définitions du repository remote :
Le Remote Repository est le dépôt distant. C'est le dossier dans lequel est stocké le projet sur le serveur qui fait office de référant. Vous ne pouvez pas directement modifier ces fichiers.C'est la référence lorsque vous clonez un projet sur votre environnement afin d'en créer une réplique local et d'en initialiser la révision la plus récente en tant qu'état des fichiers de l'espace de travail.



### 10.2 : interêt du repository remote :

Pour pouvoir collaborer sur un projet Git, il est nécessaire de savoir comment gérer les dépôts distants. Les dépôts distants sont des versions de votre projet qui sont hébergées sur Internet ou le réseau d’entreprise. Vous pouvez en avoir plusieurs, pour lesquels vous pouvez avoir des droits soit en lecture seule, soit en lecture/écriture.
Collaborer avec d’autres personnes consiste à gérer ces dépôts distants, en poussant ou tirant des données depuis et vers ces dépôts quand vous souhaitez partager votre travail.
Gérer des dépôts distants inclut savoir comment ajouter des dépôts distants, effacer des dépôts distants qui ne sont plus valides, gérer des branches distantes et les définir comme suivies ou non, et plus encore. Dans cette section, nous traiterons des commandes de gestion distante.


## 11.Commandes pour récupérer modifications dans le repository remote (pull et fetch)
### 11.1 définition git pull
Récupérer le contenu du repository distant et met le nouveau contenu du repository local dans le working directory. 

`git pull`

### 11.2 définition git fetch:

	git fetch[<NOM>]

	Récupérer le contenu du repository distant, équivalent à le télécharger.

	git fetch

	Synchronizer avec le remote
	Récupérer les commits et pointeurs distants.

## 12. Envoie des modifications du repository local à l'origine (push et pull request)
### 12.1 Définition de git push
Git push: envoie des modifications sur le repository.
### 12.2 Définition de pull request
Une pull-request désigne l'action qui consiste à demander au détenteur du dépôt original de prendre en compte les modifications que vous avez apportées et que vous souhaitez partager.

Il a alors plusieurs possibilités de son côté : commenter votre demande (par exemple si votre code ne respecte pas les normes), refuser votre demande ou bien entendu, l'accepter !

Le fait d'accepter votre pull-request a aussi un petit nom, c'est le merge.
## 13. Commande pour avoir de l'aide et d'autres commandes qui peuvent être utiles à connaître
### 13.1 Commandes d'aide
Pour avoir de l'aide, tapez cette commande:

`git command --help`

### 13.2 Liens utiles

Pour avoir un entrainement sur Git, on peut aller sur le site suivant :

https://training.github.com/


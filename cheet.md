# Git - Gestionnaire de Versions
## 1. Objet du document
			
L'objet de ce document est de donner une définition au logiciel Git et de détailler les principales commandes d'utilisation.

## 2. Création de repository (local et remote)
## 3. Définition des 3 états possibles (working directory, staging area, et repository)
### 3.1 Définition de working directory
## 4. Commandes pour modifier un fichier (add + commit)
### 4.1 le git add :
#### 4.1.1 Stages the files, ready for commit
### 4.2 le git commit :  
#### 4.2.1 commit all staged files to versioned history
## 5. Commandes pour vérifier l'état des fichiers (status et diff)
###  5.1 Le git status: 
Montre les chemins qui ont des différences entre le fichier d’index et le commit HEAD actuel.
###  5.2 Le git diff:
C'est une commande multi-fonction qui affiche les modifications entre l’arbre de travail et l’index ou un arbre, les modifications entre l’index et un arbre, les modifications entre deux arbres, les modifications entre deux objets blobs ou les modifications entre deux fichiers sur disque.

## 6.Commande pour vérifier l'historique des modifications (log)

### 6.1 Terminaison 
git-log - Afficher les journaux de validation

### 6.2 Ecriture 
git log [<options>] [<plage de révision>] [[--] <chemin>…​]

### 6.3 A quoi ça sert ?!
Le log de Git est un outil formidable pour analyser l’historique des commits et resituer un contexte. Il nous permet aussi bien de suivre un projet dans sa globalité que dans ses détails : fonctionnalités, correctifs, fichiers et répertoires, auteurs, dates…

## 7.Commandes pour revenir en arrière (reset)
### 7.1 Que fait le git reset
### 7.2 Qu'est-ce que le HEAD ?
## 8.Commandes liées aux branches (création, vérification et changement de branche
###  8.1 definition de Branch 

Une branche dans Git est simplement un pointeur léger et déplaçable vers un de ces commits. La branche par défaut dans Git s'appelle master.

###  8.2 Commande git branch

Nous obtenons la liste de toutes les branches, la branche actuelle sera marquée du caractère * avec la couleur verte

`git branch`

## 9.Commandes pour la synchronisation (merge et rebase)
### 9.1 Definition Merge
## 10.Définition et intérêt dans l'utilisation d'un repository remote (ex : Github)
###10.1 : définitions du repository:Le répertoire caché .git est nommé dépôt (en anglais repository).
###10.2 : interêt du repository:
## 11.Commandes pour récupérer modifications dans le repository remote (pull et fetch)
### 11.1 définition git pull
## 12. Envoie des modifications du repository local à l'origine (push et pull request)
### 12.1 Définition de git push
Git push: envoie des modifications sur le repository.
### 12.2 Définition de pull request
Une pull-request désigne l'action qui consiste à demander au détenteur du dépôt original de prendre en compte les modifications que vous avez apportées et que vous souhaitez partager.

Il a alors plusieurs possibilités de son côté : commenter votre demande (par exemple si votre code ne respecte pas les normes), refuser votre demande ou bien entendu, l'accepter !

Le fait d'accepter votre pull-request a aussi un petit nom, c'est le merge.
## 13. Commande pour avoir de l'aide et d'autres commandes qui peuvent être utiles à connaître
### 13.1 Commandes d'aide
### 13.2 Liens utiles





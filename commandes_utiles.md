~ Commandes swag ~

git config --global user.name "Sami Lefebvre"
git config --global user.email "sami.lefebvre@gmail.com"
git config --global color.ui auto

git add fichier -> ajoute le fichier pour le prochain commit
git rm fichier -> supprime le fichier physiquement, et le supprime dans le git
git mv -> Pour git, un déplacement est un suppression puis un ajout

( parfois, fichiers que l'on ne veut pas enregistrer dans le git )
 ex :   *.class
	*.o
	*.~
	fichier secret

=> on peut les lister dans un fichier nommé .gitignore (un fichier par ligne,
   (*, ?, etc. sont acceptés)
=> le .gitignore est lui enregistré)

git commit -a -> fait également le "add" (n'ajoute pas les nouveaux fichiers)
git commit -n "Message"

git show

git status

git log -p -> affiche les commits
git log --stat --summary -> résumé
git log --summary
git log --summary -M -> voir les déplacements (devine)
git log --oneline

git push -> eregistrer ses commits sur le serveur

git fetch -> récupérer les commits depuis le serveur
git pull -> fetch + merge


**** Stash ****

Brouillon : enregistre les modifs non enregistrées pour y revenir plus tard.
	    C'est une pile.

git stash -> enregistre dans stash
git stash show
git stash list
git stash pop
git stash drop


**** Les branches ****

Différentes branches de développement.
(branche expérimentale, ou chacun sa branche, branche pour corriger des bugs
(1.1)

git branch experimental -> nouvelle branche
git branch : liste les branches
git checkout experimental : change de branche

git merge experimental : fusionner /!\ possibilité de conflits
				       git diff pour les voir
gitk --all -> gitk avec toutes les branches
git branch -d <branche> -> supprime la branche


**** Désigner un commit ****

- identifiant (éventuellement abrégé) ex : 45ef456
	ex : $ git show <identifiant>

- nom de branche : dernier commit de la branche
	ex : $ git show experimental

- HEAD : dernier commit de la branch ecourante
	ex : $ git show HEAD

- commit ^ : parent du commit donné
	ex : $ git show HEAD^ (avant-dernier commit)
	     $ git show HEAD^^ (avant-avant-dernier commit
	     $ git show HEAD~4 (= HEAD^^^^)

- Si plusieurs parents :
	par défaut, le premier parent est affiché
	commit^1 : le premier parent
	commit^2 : le deuxième parent


**** Étiqueter un commit ****

git tag

ex : $ git tag v2.5 2af3728

Ce nom peut ensuite être utilisé :
$ git show v2.5
$ git diff v2.5 HEAD
$ git log v2.5..v2.6
$ git log v2.5..
$ git log v2.5.. makefile


**** Autres commandes utiles ****

- Rechercher des lignes, recherche dans le dépôt :
	$ git grep "motif" (expr. rationnelle)
	$ git grep "motif" v2.5 (ou tout autre commit)

- Retrouver qui a modifié les lignes d'un fichier :
	$ git blame fichier

- Retrouver le commit à l'origine d'un problème :
	$ git bisect
	$ git bisect start (pour commencer)
	$ git bisect good v0.2 (la version 0.2 ne contient pas le bug)
	$ git bisect bad (le dernier commit a le bug)
	=> git va extraire une version intermédiaire
	   Il faut tester et répondre :
		$ git bisect good OU
		$ git bisect bad  OU
		$ git bisect skip		

	$ git bisect reset pour arrêter


**** Faire des commits "propres" ****

- Sélectionner ce que l'on met dans un commit :
	$ git add -p [fichiers] -> on va pouvoir choisir interactivement parmi
				   les modifications ce que sera intégré ds le
				   commit.

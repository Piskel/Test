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

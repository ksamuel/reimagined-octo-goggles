
# Initialiser la configuration de git

```bash
git config --global user.name "John Doe"
git config --global user.email johndoe@example.com
```

# Créer un repo git

```bash
git init 
```

Ou, pour un repo sans copie de travail:

```bash
git init --bare
```

# Ajouter un fichier à l'index

```bash
git add filename # ajoute le fichier
git add . # ajoute le dossier récursivement
git add *.ext # ajoute tous les fichiers avec l'extensions
```

Attention, ne pas oublier de rajouter les fichiers importants au `.gitignore` (ex: http://gitignore.io/).

# Retirer un fichier de l'index

```bash
git reset fichier # git restore fichier --staged
```

# Arrêter de traquer un fichier

```bash
git rm filename  
```

Arreter de traquer, mais garder la copie de travail

```bash
git rm filename  --cached
```

Ceci n'a rien à voir avec la commande rm, et le fichier existe toujours dans l'historique

# Transformer l'index en change set (aka "commit")

```bash
git commit -m "Message de commit" # Si -a, ça ajoute tout sauf les untracked
```

# Regarder l'état du dépôt:

```bash
git status
```

# Regarder l'historique

```bash
git log
```

Petit alias:

```bash
git config --global alias.lg "log --color --graph --pretty=format:'%Cred%h%Creset -%C(yellow)%d%Creset %s %Cgreen(%cr) %C(bold blue)<%an>%Creset' --abbrev-commit"
```

On l'utilise en tapant `git lg`.

Alternativement, vous avez une version graphique:

```bash
gitk
```

# Annuler le dernier commit:

Remplacer le commit precedent par le commit actuel:

```bash
git commit -m "Message de commit" --amend
```

A ne faire que si on a pas publié sa branche

Inverser le dernier:

```bash
git revert HEAD -m "Message"
```

# Manipuler les branches

Créer une branche

```bash
git branch nom
```

Changer de branche

```bash
git checkout nom # ou git switch nom 
```

Les deux d'un coup

```bash
git checkout -b nom # ou git switch -c nom 


Il faut une copie de travail propre

# Manipuler les tags

```bash
git tag nom
```

# Mettre de côté des modifications


```bash
git stash
```

Appliquer le stash:

```bash
git stash apply [ref du stash]
```

Lister les stash

```bash
git stash list
```

# Récupérer un fichier dans le passé

```bash
git checkout ref -- fichier # ou git restore  wololo [--source HEAD]
```

# Merger deux branches

```bash
git merge branche_a_amener
```

Annuler

```bash
git reset --merge # git merge --abort
```

Merger uniquement en conservant mes changements:

```bash
git reset --merge -X ours
```

Ou leurs changements:

```bash
git reset --merge -X theirs
```

Régler les conflits à la main

```bash
git mergetool
```

# Ajouter un depôt distant

```bash
git remote add nom  URI
```

# Envoyer les données sur le dépôt distant

```bash
git push nom_remote nom_branche [--set-upstream]
```

# Trouver l'auteur du ligne

```bash
git blame fichier
```

# Trouver un bug par dichotomie

```bash
git bisect start le_plus_recent le_plus_vieux 
git bisect run script
git bisest reset
```
# Rebase

```bash
git rebase [-i] ref 
```

La resolution se fait avec `git mergetool`.

`git rebase --continue`, après mergetool OU `git rebase --abort`

Si on a fait un "edit", il faudra faire un `git commit --amend` après l'édition avant le --continue

# Filter branch

```bash
git filter-branch -f --index-filter "commande" HEAD
```

# Créer sa clé ssh

```bash
ssh-keygen
```



# La suite sur github : 
https://github.com/ksamuel/reimagined-octo-goggles
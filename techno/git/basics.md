# git basics

#### Difference des fichiers locaux avec le repo:
```sh
> git diff origin/develop
```

#### Commit locaux:
```sh
> git log origin/develop
```

### 1. Tester le code de la conf en créant une nouvelle branche
#### 1.1 Créer une nouvelle branche à partir de ma branche locale (avec commit) et bascule dessus.
```sh
> git checkout -b leNomDeMaBrancheDeTest
```

#### 1.2 Efface tout pour avoir la même chose que sur la branche origin/developp (du repo)
(la commande générique: git reset --hard "SHA du comit" ou par ex "origin/develop")
```sh
> git reset --hard origin/develop
```

#### 1.3 Switch de branch pour develop
```sh
> git checkout develop
```
### 2. Créer une branche en local et la créer sur le serveur
#### 2.1 Créer une nouvelle branche à partir du dernier commit de ma branche locale courante et basculer dessus sur la branche nouvellement crée
```sh
> git checkout -b feature/nom_de_branche
```

#### 2.2. Créer la branche sur le serveur et push
```sh
> git push -u origin feature/nom_de_branche
```

#### 2.3. Créer une branche en local à partir d'une branche présente sur le serveur
```sh
> git checkout -b nom_branche_locale origin/nom_branche_serveur
```

### 3. Gestion des retours à la ligne
#### 3.1 Change la config des retours en local pour  qu'ils soient windows
```sh
> git config core.autocrlf true
```

#### 3.2 Change la config des retours en global pour  qu'ils soient linux
```sh
> git config --global core.autocrlf false
```

### 4. Gestion des branches
#### 4.1 Supprimer une branche sur le serveur
```sh
> git push origin --delete feature/toto
```

#### 4.2 Nettoyer les branches locales
```sh
> git fetch -p
```

### 5. Mergetool params
```sh
> git config --global merge.tool p4merge
> git config --global mergetool.p4merge.cmd "C:/Program\ Files/Perforce/p4merge.exe \"$BASE\" \"$LOCAL\" \"$REMOTE\" \"$MERGED\""
> git config --global diff.tool p4merge
> git config --global difftool.p4merge.cmd "C:/Program\ Files/Perforce/p4merge.exe \"$BASE\" \"$LOCAL\" \"$REMOTE\" \"$MERGED\""
```

### 6. Submodules management
```sh
> git submodule update --init --recursive
```

### 7. Ignore local local changes on git file
```sh
> git update-index --skip-worktree <filepath>
```

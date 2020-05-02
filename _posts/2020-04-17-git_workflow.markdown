---
layout: post
categories: git
title: git_workflow
---
# Git
"Il est facile de se tirer dans le pied avec `git`, mais l'on peut aussi aisément revenir à un pied précédent et le fusionner avec votre jambe actuelle."  
  —Jack William Bell

## Commençons par les bases

Vous venez d'avoir accès à un nouveau projet, vous clonez le répertoire:
```bash 
git clone git@gitlab.ensimag.fr:userName/projectName.git
```

Vous pouvez maintenant développer sur ce projet localement.

Ce qui suit est **très important**. Vous allez le faire tout le temps.

---
Premièrement *la modification ou l'ajout de fichiers* :
```bash
git status # Vous affichez l'état du dépôt
git add <fichier> # Vous stagez un fichier que vous avez modifié
git commit # Vous commitez un fichier </fichier>
```
Quand est-ce que vous faites cette procédure ? Lorsque vous avez **fini** de développer une feature ou **fini** de corriger un bug.
J'insiste sur le fait qu'il faut le faire pour **chaque** feature et **chaque** bug. 
Par exemple :
- vous n'allez pas mélanger la correction d'un bug sur `fct1` et l'ajout de `fct2` sans avoir réalisé un `commit` de votre correction de bug avant de passer au développement d'une autre fonction.
- vous n'allez pas corriger un bug dans `fichier1` puis un autre dans `fichier2` sans `commit` la correction de bug effectuée dans `fichier1` avant de passer à la correction de `fichier2`
- ... 

---

Cela nous amène à **la rédaction d'un bon message de commit**. Si vous ne respectez pas la procédure ci-dessus vous n'allez pas réussir à écrire un bon message de commit.
Un message de commit doit expliquer les modifications que vous avez effectuées:
 - pourquoi ces modifications ?
	 - Correction de bug,
	 - Ajout de fonctionnalité,
	 - ...
 - où vous les avez effectué ?
	 - Correction d'un bug sur `ft1`,
	 - Ajout d'une fonction `fct2` dans le fichier `fichier3` qui réalise la fonctionnalité ...
	 - ...

On pourrait rajouter plus de points mais déjà ça c'est bien. Il faut que le message soit **explicite**. Vous l'écrivez pour la personne qui va développer sur le projet après vous. **Il doit savoir ce que vous avez fait, où vous l'avez fait et surtout pourquoi vous l'avez fait.**

---

Maintenant que l'on a vu comment *modifier et ajouter des fichiers* nous allons voir comment collaborer avec vos amis développeurs sur ce même projet.

La **première** chose à faire dès que vous retourner travailler sur le projet est de faire
```bash
git pull
```
Avant toute chose. Vraiment c'est **très** important.

Ensuite vous faites vos modifs, vous commitez **souvent** sur **chaque** modif, et là vous faites
```bash
git push
```

---

Passons aux problèmes que vous allez rencontrer (sans parler du ssh...).

 - Vous n'arrivez pas à `push`. Le terminal vous affiche un truc du genre : `vous êtes en retard sur la branche master, vous pouvez pas push`. Cela arrive lorsque quelqu'un à `push` des modifications sur des fichiers que tu as modifié **avant** que tu ai toi-même `push` tes modifications (le salaud).
	 - La solution est de faire un `pull` et de gérer les conflits localement avant de `push` la version finale acceptant les modifications des deux personnes.
	 - Comment éviter ce problème ? Ne pas modifier la même partie du même fichier chacun de son côté. Il faut donc **communiquer** sur ce que tu comptes développer ou modifier avant de le faire.

## Un petit peu plus en détails

La branche de développement par défaut se nomme `master`. Vous pouvez voir la liste des branches locales avec la commande `git branch`. La branche précédée d'une `*` est la branche sur laquelle vous développez actuellement.

---

Il existe pleins d'outils pour se faciliter la vie. Notamment la rédaction du message de commit. En effet c'est pas facile d'écrire un message parlant sur une seule ligne de terminal - d'où l'intérêt de `commit` souvent pour avoir des petits messages de commit. Vous pouvez utiliser l'éditeur que vous voulez pour écrire vos message de commit.
```bash
git config --global core.editor "nano"
```
J'utilise `nano` personnellement mais vous pouvez mettre celui de votre choix.
Une fois que vous avez votre éditeur favori vous faites simplement un `git commit`. Cette commande ouvrira automatiquement votre éditeur.

## Dans la pratique

```bash
git status
git pull

# Je fais mes modifs...

git add -A  # ici j'ajoute tous les fichiers modifiés pcq flemme d'écrire le nom du fichier.
git commit -m "Mon (petit) message explicite"
# ou simplement git commit

git push

# Hop là ça fonctionne pas
# pas de problème, faisons un pull

git pull --rebase # c'est pas obligé de mettre l'option --rebase mais ça fait un historique de commits plus propre

# s'il y a des problème de conflits, la commande précédente renvoie qqch du genre :
# CONFLICT (content): Merge conflict in <fichier>

git status # pour voir une liste des conflits

# Modification des fichiers pour corriger le conflit

git add <fichier>
git rebase --continue # on passe au commit suivant et on refait la même procédure

git push # finalement je push une fois tous les conflits corrigés

```

## Le mot de la fin
Pour tout problème de terminologie sur les termes utilisés (répertoire, branche, ...) n'hésitez pas à me poser des questions.
<!--stackedit_data:
eyJoaXN0b3J5IjpbLTk2Njk1NDA0NCw3MDQ2ODkyNDBdfQ==
-->
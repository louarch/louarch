# Projet NSI n.7 pour Mme Nequest

## Jeu de Mathématiques en anglais

## Fonctionnement du site

### Structure du client

#### /

Tout commence sur la page index, qui permet de déterminer notre thème.

*Selection du thème*
- Une fois le thème selectionné, on est redirigé vers la page [/game-select/\<theme>](#game-selecttheme)

*Le choix de dissocier le choix du thème et le choix du jeu a été fait pour réduire le nombre d'éléments sur la page, et donc simplifier l'utilisation du site*

#### /game-select/&lt;theme&gt;

Cette page permet de choisir le jeu auquel on veut jouer. On y selectionne
- Le type de jeu
- La difficulté

Une fois les choix effectués, les informations sont envoyées à [/game?data](#gamedata) via une requête GET

*Le choix d'utiliser une requete GET et non POST a été fait pour retirer le warning lorsqu'on recharge la page. Cela simplifie ainsi la réinitialisation des jeux, et la navigation globale sur le site*

#### /game?data

Cette page permet de jouer au jeu selectionné. Elle est appelée avec les paramètres suivants :
- theme
- game_name
- level

Elle permet de jouer au jeu selectionné, et de revenir à la page [/game-select/\<theme>](#game-selecttheme) en cas de victoire ou de défaite.

Lors de l'appel de la page, un travail est fait côté serveur pour renvoyer les informations correctes à la page. Plus d'infos sur [le côté serveur](#get-gamedata)

### Structure du serveur

#### GET /game?data

Lors de l'appel de cette route, on reçoit les informations suivantes à partir du GET Query
- theme
- game_name
- level

On va ensuite chercher les informations du jeu dans la base de données
- Dans la table game_info

On va également chercher les données à mettre dans le jeu :
- Dans la table game_data


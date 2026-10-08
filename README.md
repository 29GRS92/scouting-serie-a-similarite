# Scouting Serie A 2025/26 : similarité de joueurs

Un outil qui, pour chaque joueur de Serie A, trouve les joueurs qui lui ressemblent le plus statistiquement, **au même poste**. Cas d'usage : un club ne peut pas se payer un joueur et cherche des alternatives au profil proche.

**Site en ligne : [À COMPLÉTER : lien GitHub Pages]**


## Ce que fait le site

1. On choisit un poste (attaquant, milieu, défenseur, gardien) puis un joueur.
2. Un **radar** montre son profil statistique par 90 minutes, ramené sur 100 par rapport au meilleur joueur du poste.
3. On peut le **comparer à un deuxième joueur** : radar superposé, tableau côte à côte et pourcentage de ressemblance entre les deux.
4. La liste des **10 profils les plus proches** donne leur équipe, leur année de naissance et leur temps de jeu. Un clic sur un nom lance la comparaison.
5. Le lien de la page garde le poste et les joueurs choisis, pour partager une comparaison.

## Méthode

1. **Collecte** des statistiques de 586 joueurs sur Sofascore (effectifs actuels, puis complétion par les feuilles de match pour ne pas perdre les joueurs partis en cours de saison).
2. **Filtre** : au moins 900 minutes jouées (environ 10 matchs complets), soit 339 joueurs.
3. **Statistiques par 90 minutes**, pour comparer des rythmes et non des totaux de saison.
4. **Un jeu de statistiques par poste**, puis normalisation des échelles séparément pour chaque poste.
5. **Similarité cosinus** entre joueurs du même poste, convertie en pourcentage de ressemblance : 100 pour un profil identique, 50 pour aucun lien. Chez les attaquants, seulement 4 % des paires dépassent 90 %, donc un score élevé a un vrai sens.
6. **Export** des données dans un fichier lu par une page web, sans serveur ni base de données.

## Limites

- La ressemblance compare des profils statistiques, **pas la qualité** : deux joueurs à 95 % peuvent avoir des niveaux très différents.
- Les postes sont larges : un ailier et un avant centre sont tous deux des attaquants.
- Le contexte d'équipe pèse sur les chiffres et n'est pas corrigé.
- Les joueurs de moins de 900 minutes sont absents. Une seule saison, un seul championnat, une seule source (Sofascore, y compris xG et xA).

## Contenu du dépôt

| Fichier ou dossier | Rôle |
|---|---|
| `scouting_serie_a_similarite.ipynb` | Le notebook complet : collecte, nettoyage, similarité, export, site |
| `docs/modele.html` | Modèle de la page du site |
| `docs/index.html` | La page générée, publiée avec GitHub Pages |
| `docs/donnees_joueurs.json` | Les données lues par la page |

Une annexe facultative du notebook montre l'export vers une base MySQL (version de départ du projet).

## Lancer le projet

1. Installer les bibliothèques : `pip install pandas numpy scikit-learn cloudscraper`.
2. Ouvrir le notebook et l'exécuter de haut en bas. La première exécution collecte les données (environ 35 minutes) et les sauvegarde. Les suivantes les relisent.
3. Ouvrir `docs/index.html` dans un navigateur.

## Source

Statistiques : [Sofascore](https://www.sofascore.com), saison 2025/26 de Serie A.

## Auteur
29GRS92

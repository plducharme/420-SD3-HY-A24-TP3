# Visualisateur d'émissions de gaz à effet de serre

# Survol de l'application
L'application permet de visualiser les émissions de CO2 de différentes entités (pays/régions). 

# Notions évaluées
- PySide6
  - Widgets
  - Signaux et slots
  - Layouts
  - Dessin sur canevas
  - Interaction avec d'autres bibliothèques
- Matplotlib
- Pandas
- BD SQLite

# Prérequis
- Python 3.12
- PySide6
- Matplotlib
- Pandas
- SQLite
- SQLAlchemy (optionnel)

# Critères d'évaluation
Ce travail pratique compte pour 30% de la note finale.  
Le travail doit être effectué en équipe de 2 ou 3 personnes.  
**Tout travail solo sera refusé.**

Critères d'évaluation :
- Interface graphique
  - Implémentation des requis
  - Efficacité et esthétique de l'interface
- Pandas
  - Utilisation adéquate des fonctionnalités de Pandas
- Matplotlib
  - Affichage des graphiques
- SQLite
    - Implémentation des requis BD
- Gestions des exceptions
  - Gestion des exceptions lors de l'importation des données
- Code
  - Lisibilité
  - Organisation
  - Commentaires
  - Conventions PEP-8

## Requis Interface graphique (10 points)
- Créer une interface graphique avec PySide6 comprenant les éléments suivants :
  - Un canevas pour afficher les graphiques Matplotlib
    - Doit ajouter une barre de navigation pour zoomer et déplacer le graphique (NavigationToolbar2QT)
  - Une liste déroulante pour sélectionner l'entité à visualiser
    - Doit afficher les entités uniques contenues dans le DataFrame
    - Doit mettre à jour les graphiques et les statistiques de l'entité sélectionnée
    - Doit être triée par ordre alphabétique
  - Un widget permettant de sélectionner le type de graphique à afficher
    - barres
    - lignes (plot)
  - Un ensemble de widgets permettant d'activer ou de désactiver le tri des données
    - Tri ascendant ou descendant
    - Si désactivé, les données doivent être affichées dans l'ordre d'importation
  - Un bouton pour exporter la vue courante du graphique en pdf
    - Doit ouvrir un QFileDialog pour sélectionner le dossier et le nom du fichier à sauvegarder
    - Doit exporter le graphique courant en pdf 
  - Un menu "Fichier"
    - Une action "Importer"
      - Doit ouvrir un QFileDialog pour sélectionner un fichier CSV
      - Doit importer les données du fichier CSV
        - dans une BD SQLite nommée `emissions.db`
          - Doit créer la BD si elle n'existe pas
          - Si elle existe, on doit l'écraser
        - dans un DataFrame Pandas
        - Doit gérer les exceptions lors de l'importation des données
    - Une action "Quitter" avec un raccourci clavier Ctrl+Q
      - Doit fermer l'application
  - Un menu "Aide"
    - Une action "À propos"
      - Doit afficher une boîte de dialogue avec les informations suivantes :
        - Nom de l'application
        - Nom des auteurs
    - Une action "Info données"
      - Doit afficher une boîte de dialogue avec les informations suivantes :
        - Nombre de données total
        - Les Séries (avec leur type) contenues dans le DataFrame
        - Le nombre d'entités uniques
          - Devra provenir d'une requête à la BD
  - Si lors du lancement de l'application, la BD `emissions.db` existe, les données doivent être chargées automatiquement
  - Un canevas avec un pixmap pour afficher les statistiques de l'entité 
    - Doit être dessiné sur le canevas
    - Le nombre de données affichées
    - Moyenne des émissions de CO2
    - L'écart-type des émissions de CO2
    - Le minimum et le maximum des émissions de CO2
- La facilité d'utilisation de l'interface graphique sera évaluée
- L'esthétisme de l'interface graphique sera évalué

## Requis Pandas (8 points)
- Utiliser Pandas pour importer les données du fichier CSV
- Modifier le type des Series pour une meilleure utilisation des données
- Vous avez le droit de renommer les Series pour faciliter leur utilisation
- Utiliser Pandas pour trier les données si l'option de tri est activée
- Utiliser Pandas pour calculer les statistiques de l'entité sélectionnée (optionnel, mais recommandé)
- Filter les données pour l'entité sélectionnée pour utiliser seulement les lignes contenant des données d'émissions
  - Pas de données d'émissions == 0
  - Pas de données d'émissions == NaN

## Requis Matplotlib (5 points)
- Utiliser Matplotlib pour afficher les graphiques sur le canevas
- Un exemple d'affichage avec Matplotlib dans un canevas
  - https://www.pythonguis.com/tutorials/pyside6-plotting-matplotlib/
- Utiliser matplotlib avec Pandas pour afficher les graphiques
  - https://pandas.pydata.org/pandas-docs/version/0.13.1/visualization.html


## Requis SQLite (2 points)
- Vous pouvez utiliser SQLAlchemy pour simplifier l'interaction avec la BD ou faire une simple requête SQL
- Requête pour obtenir le nombre d'entités uniques


## Requis Code (5 points)
  - Lisibilité
  - Organisation
    - Découpage en fonctions
    - Nom des variables, fonctions, classes, etc
  - Commentaires
    - Expliquer les sections principales du code
      - Utilité des fonctions
      - Utilité des classes
  - Conventions PEP 8
    - Sauf les "duplicated lines found"
  - Des points pourront être retirés pour un excès de fautes de français


### Notes additionnelles
Cette fois, aucun gabarit de code n'est fourni. Vous devez créer votre propre application en respectant les critères d'évaluation.  
Un bloc de code semblant provenir de l'IA sans aucun commentaire ou explication sera pénalisé.

Si PyCharm vous demande si vous voulez ajouter le dossier `.idea` à git, répondez non. Ceci va faciliter
la vie de vos coéquipiers et de l'enseignant lors de la correction.
  - Si vous les avez ajoutés, vous pouvez les retirer en utilisant les commandes suivantes :
    - `git rm --cached -r .idea`
    - `git commit -m "Enlever .idea"`
    - `git push`

Petit rappel : Toujours utiliser un environnement virtuel pour vos projets.

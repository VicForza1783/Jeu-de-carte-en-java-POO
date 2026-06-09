# Jeu-de-carte-en-java-POO
On souhaite développer une application imitant le jeu Inscryption. Vous vous retrouvez dans une cabane, perdu en pleine forêt. Dans l'obscurité, attablé face à vous se dresse un adversaire aux yeux inquiétants qui vous défie à un étrange jeu de cartes...

## Technologies utilisé :
Langage de programation : Java avec une approche de développement accès programation orienté objet 

Gestion des tests : JUnit 4 & Hamcrest

Modélisation : PlantUML

<img width="460" height="215" alt="image" src="https://github.com/user-attachments/assets/e81a4d9e-916f-489c-b112-18754fbab6eb" />
<img width="750" height="422" alt="image" src="https://github.com/user-attachments/assets/1df6f442-8ab1-44a3-a476-8787abc33cad" />


### interface joueur : 

<img width="704" height="813" alt="Capture d’écran du 2026-06-09 13-55-06" src="https://github.com/user-attachments/assets/6c3ae439-b5bd-41ec-b234-ef93743bdee5" />
<img width="706" height="270" alt="Capture d’écran du 2026-06-09 13-55-18" src="https://github.com/user-attachments/assets/70df9086-0402-4cc6-981d-3d9544d79972" />

## Fonctionnalités de l'appli
🤖 Gestion des Parties et du Jeu

Structure globale : Le jeu complet se joue en 3 parties. Le joueur doit gagner les 3 pour remporter la victoire finale.
La condition de victoire/défaite d'une partie : La partie s'arrête dès qu'un écart de 5 points est atteint en faveur de l'un des deux joueurs.

Initialisation d'une partie : Mise en place d'une pioche de 15 cartes (majoritairement des Écureuils). Distribution automatique des 4 premières cartes dans la main du joueur.Placement possible de cartes obstacles (Rocher, Sapin) sur le plateau dès le début.


🗺️ Le Plateau et les Cartes

Le Plateau : Une grille de 2 lignes et 4 emplacements (Ligne du haut = Adversaire, Ligne du bas = Joueur). Les Cartes "Animal" possède : un Nom, des points d'Attaque, des points de Vie (PV), un coût en Gouttes de sang, un coût en Os, et une propriété "Volant" (Oui/Non). Les Cartes "Obstacle" : Possèdent uniquement un Nom et des PV (Rocher : 5 PV, Sapin : 3 PV). Ils bloquent un emplacement jusqu'à leur destruction.

Mécanique des ressources :Gouttes de sang : Nombre de cartes actuellement sur votre plateau à sacrifier (tuer) pour poser la nouvelle carte. Os : Nombre de cartes déjà mortes (tuées ou sacrifiées) depuis le début de la partie pour poser la carte.



⚔️ Déroulement d'un Tour

Prédiction : L'application affiche au joueur les cartes que l'adversaire va jouer au prochain tour (via une ligne fictive au-dessus du plateau). Pioche : Le joueur pioche obligatoirement 1 carte au début de son tour.Phase d'action : Le joueur peut poser autant de cartes qu'il le souhaite (dans la limite des 4 places et de ses ressources/sacrifices).

Phase d'attaque (Fin de tour) : Chaque carte attaque face à elle. Si un ennemi est en face : l'ennemi perd des PV égaux à l'attaque de la carte. Si la case est vide : les points d'attaque sont ajoutés directement au score global (la balance). Cas spécial "Volant", l'attaque va directement au score, même si une carte adverse bloque le passage.

Affichage : Un message doit résumer tous les dégâts infligés à la fin du tour.

Tour de l'adversaire : L'IA joue ses cartes selon une stratégie entièrement prédéterminée  et attaque de la même façon.


💻 Interface et Erreurs (CLI)Affichage textuel complet du plateau, du score, de la main et de la pioche. Gestion des erreurs de saisie : Si le joueur tape une commande invalide (mauvais format, carte inexistante, pas assez de ressources), l'application doit lui expliquer pourquoi et lui redemander sa saisie.


🧬 Système de Pouvoirs

Il y a 6 pouvoirs spécifiques appliqués aux créatures.

Nombreuses vies pour les chats : La carte ne meurt pas et reste sur le plateau lorsqu'elle est sacrifiée pour en poser une autre. 

Croissance pour le Louveteau : Se transforme automatiquement en Loup au début de son deuxième tour sur le plateau.

Puant pour la punaise : Réduit de 1 le score d'attaque de la carte adverse qui lui fait face. 

Coureur pour l'Élan : Se déplace d'une case vers la droite après avoir attaqué. Si c'est bloqué, va à gauche. Si tout est bloqué, ne bouge pas.

Contact Mortel pour la Vipère : Tue instantanément n'importe quelle créature à qui elle inflige des dégâts (ne fonctionne pas sur les obstacles). 

Piques pointues pour le Porc-épic : Inflige automatiquement 1 point de dégât à la carte qui l'attaque.



🏛️ Événements Inter-ManchesFin de la Partie 2 : * Le joueur choisit 1 nouvelle carte bonus parmi 2 propositions pour l'ajouter à sa pioche. La Pierre de Sacrifice : Le joueur doit choisir une carte à sacrifier pour extraire son pouvoir et l'appliquer définitivement sur une autre carte de son deck(non développé).

#pensées 
2/1/25
___
# Ça va vite
Quand Jean est venu vers nous, vers l'ULB pour le projet, beaucoup d'outils n'existaient pas encore, ça a évolué HYPER vite ces derniers mois. 
Notre rôle n'est plus tellement de savoir si c'est possible (spoiler ça l'est), mais plutôt comprendre les limitations, comprendre comment fine-tune un modèle afin qu'il fit mieux les attentes, celle des designers industriels de la Cambre en l'occurence, (même si je pense que c'est utile de garder un côté général). 

Les plans d'attaque sera plutôt quelque chose du genre
- la génération de _vues isométriques_ intéressantes et fidèles sur base de dessins 2D. 
- savoir comment transformer ça en _OBJ_ ou autre afin de pouvoir les mettre dans un _LLM_ (notre "première" intuition finalement). 
- réaliser une _preuve de concept_ sur quelques familles de formes $\to$ avoir un dataset béton pour quelques familles de formes, avoir de quoi tester dans la pipeline. 
- expliquer comment train un huge modèle pour la suite. 

# Descriptions des shapes
Je pense à autre chose : quid des descriptions manuelles faites par les gens ? En avons nous seulement besoin ? Est ce que c'est intéressant dans le cadre du programme de la Cambre ? Est ce qu'on est pas en train de bloater les étudiants pour rien ? _En parler à Jean._
Une approcher potentiellement plus intéressante pour tout ça serait de se poser des questions sur l'interaction avec un LLM dans le cadre du design. Introduire le concept de prompt engineering, comment sortir les meilleurs résultats d'un modèle, comme la query "An isometric view of a 3D CAD model depicting a mechanical part" dans l'utilisation de GPT dans [Text2Cad](Text2Cad.md). 
Maintenant comment lier les concepts et travaux réalisés pour ce mémoire avec toute cette discussions ? Il faudrait dormir dessus, et probablement en parler à Jean. 

# Big picture
Et puis de manière plus large, je pense il faut absolument profiter de ce mémoire pour comprendre le milieu de la 3D pour l'IA, vu à quel point c'est en train d'évoluer en ce moment (⚠️opportunités ?). Il y a clairement des applications de tout ça dans les domaines alternatifs comme les JV ou l'art, profitons en pour nous faire une culture, on sait jamais. 
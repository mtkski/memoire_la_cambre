# Réunions
[Notes réu Debeir](Notes%20réu%20Debeir.md)
[Visite LaCambre](Visite%20LaCambre.md)
[Notes réu chez Ohme](Notes%20réu%20chez%20Ohme.md)
[Réunion salle détente 30-12-24](Réunion%20salle%20détente%2030-12-24.md)

# Etat de l'art
[State of the art](State%20of%20the%20art.md)

# Question en vrac
- Comment assurer la création de formes en 3D de manière robuste et durable. 
- Quel outil utiliser pour le pipeline de toute les outils ? $\to$ retrouver outil proposé par Seb de PYL
- _Challenge_ : having clean UV unwrapping and topology (mentionné dans les considérations de Meshy) : topology, le problème est relativement bien résolu par les avancées récentes comme D
- Est ce que utiliser des outils comme RSV sur des vues CAD ça sert à quelque chose ? L'intérêt du move ça serait de 1) utiliser un outil de l'ULB et 2) faire quelque chose que je n'ai pas beaucoup vu dans la doc $\to$ approche nouvelle (mais il faut se renseigner, si ça se trouver il y a des choses similaires qui marchent mieux dans l'état de l'art)
- Voir comment entrainer la "culture" de notre LLM générateur de fichier obj avec des ressources custom $\to$ web scraping, préparation du dataset, labeling etc. 

## Définition de la problématique
Les questions auxquelles on doit tenter de répondre :
- Comment modéliser, généraliser et générer un dataset qui répond à des demandes très spécifique comme le milieu du design industriel et de l'art en général. $\to$ 2D to 3D, generation of the 3 CAD views.  
- Comment créer une pipeline fiable de génération 3D (partie plus pratique)
- Comment optimiser le training ? $\to$ faire un cas naïf puis chercher des moyens créatifs/techniques pour accélérer cela. $\to$ structures de données ? 

# Ressources en vrac
- [Lexique mémoire](Lexique%20mémoire)
- [SDI](SDI.md)
- [Latent NeRF](Latent%20NeRF.md)
- [NeRF](NeRF.md) 
- [[Gaussian splatting]]
- [Open3D library-software](Open3D)
- [[Photogrametry, nerf, gaussian]] : video qui compare les 3
- [Course on generative 3D from Individual Kex](Video%20Individual%20Kex.md) 
- [Site de Jiaxiang Tang](https://me.kiui.moe/) chercheur PhD en IA spécialisé dans la 3D (EdgeRunner et Stable Dreamfusion c'est lui) 
- [Tanks and temples](https://www.tanksandtemples.org/details/8610/) : pour du benchmarking, pas + creusé
- [Instant mesh](https://arxiv.org/pdf/2404.07191) 
- [[Comparaisons fichiers 3D]]
- 

## Ressources La Cambre
- [Génération de Formes - sept 2024](La%20Cambre%20Design%20Industriel%20-%20Projet%20A%20I%20–%20Génération%20de%20Formes%20-%20sept%202024.pdf)
- [Notes Enoncé FORMALL](Notes%20Enoncé%20FORMALL.md)

# Pensées random (boîte à idées)
- [Pensées Hausdorff distance](Pensées%20Hausdorff%20distance.md)
- [Pensées état du mémoire 2/1/25](Pensées%20état%20du%20mémoire.md)
- [[Pensées LISA 4-1-25]]
- [[Écriture mail Debeir]]
- 

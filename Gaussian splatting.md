#technique #concept 
[Paper](https://arxiv.org/pdf/2308.04079)
[Video tuto postshot](https://www.youtube.com/watch?v=ERuRMOVO58Q)
[Inria github](https://github.com/graphdeco-inria/gaussian-splatting?tab=readme-ov-file)
[GS for ThreeJS](https://github.com/mkkellogg/GaussianSplats3D)
___
# Description
Sert à représenter des scène, en utilisant des "Gaussians" en 3D. Une proba d'avoir une couleur, un alpha. Le plus gros argument c'est la vitesse : c'est juste du calcul de profondeur et du alpha blending. 
___
It's a __differentiable rasterization__ technique: 
- _Differentiable_ : les modèles sont nuls avec des données brutes, ils aiment quand c'est 'fuzzy' et continu (c'est à dire differentiable). 
- _Rationizable_ : ça veut dire prendre la data et la dessiner sur un écran (aka 'discrétisation'). En mode 3D data -> 2D data pour être affichée sur un écran. 

## Idée
On part d'images, on choppe un point cloud plutôt moyen avec des méthodes plutôt standard de _structure from motion_. On met des gaussians sur ce point cloud, et on utilise le gradient descent pour fit ces gaussians aux photos de bases. Il y a possibilité que des gaussians s'ajoutent pour mieux fit les formes complexes, d'autres redondantes pourraient disparaitre. Au final on a des gaussians qui fit super bien les images $\to$ photo-réalisme. 

# Technique
## Qu'est ce qu'un gaussian
Chaque point d'un gaussian splat consiste en 4 param : pos, cov (_how it's stretched_), color, alpha. 

## Rasterization
1) Project all points into 2D
2) for every pixel : calculate contribution of every point. 

Pas super opti que tout les pixels influencent tout les autres, mais du coup, on utilise une tile based rendering approach pour optimiser cela (pas bien capter). 
Si on est pas en training, il ne faut pas d'office que ça soit differentiable, on peut les afficher comme des instant quad (ce qui est fait en général dans les viewers en ligne). 

## Training 
1) Point cloud avec algo de structure from motion
2) Ces points sont rasterized, comparés avec l'image de base pour le loss.
3) Gradient descent pour optimiser pos, cov, color, alpha. 

Des heuristics sont utilisées pour densification and pruning (ajouter des points là où c'est utile, et supprimer ceux pas très utiles). 


Vat is this : `Z-buffer (prevent to draw useless gaussians that are not )`
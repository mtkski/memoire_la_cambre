
#technique #concept 
[Paper](https://arxiv.org/pdf/2308.04079)
[Video tuto postshot](https://www.youtube.com/watch?v=ERuRMOVO58Q)
[Inria github](https://github.com/graphdeco-inria/gaussian-splatting?tab=readme-ov-file)
___
# Description
Sert à représenter des scène, en utilisant des "Gaussians" en 3D. Une proba d'avoir une couleur, un alpha. Le plus gros argument c'est la vitesse : c'est juste du calcul de profondeur et du alpha blending. 

## Idée
On part d'images, on choppe un point cloud plutôt moyen avec des méthodes plutôt standard de _structure from motion_. On met des gaussians sur ce point cloud, et on utilise le gradient descent pour fit ces gaussians aux photos de bases. Il y a possibilité que des gaussians s'ajoutent pour mieux fit les formes complexes, d'autres redondantes pourraient disparaitre. Au final on a des gaussians qui fit super bien les images $\to$ photoréalisme. 

# Technique
Z-buffer (prevent to draw useless gaussians that are not )
#implementation #hilevel 
___
[Paper](https://arxiv.org/pdf/2211.07600)
[Github](https://github.com/eladrich/latent-nerf?tab=readme-ov-file)
Pas l'outil qui fait les rendus les plus clean, et peut être un peu "all over the place" avec l'espace latent. 
Explorer si cet espace latent est quelque chose qui pourrait être utile. 
# Description 
Basé sur [NeRF](NeRF.md)
## Abstract
[[Full text abstract latent NeRF]]
#todo recheck les conneries que j'ai pu dire ici sans vraiment lire le paper
L'implémentation d'un espace latent dans la génération de forme 3D pour aider à avoir un meilleur contrôle sur les différents aspect de l'objet. C'est à dire qu'on a une Sketch-Shape, qui est une image un peu générale, et puis on rajoute des détails etc avec la [distillation](SDI.md) pour obtenir un truc + complexe. 


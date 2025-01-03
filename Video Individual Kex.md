__Introduction to generative 3D [full course, hands-on]__
[Video link](https://www.youtube.com/watch?v=BswQQNkbMW4) à regarder en x2, il est un peu lent. 
Prise de note de la video
___

# Intro
Meshes are hard for ML. 
3 grandes étapes dans la pipeline de génération 3D : ![200](screenshot%202025-01-02%20à%2017.26.16.png)
Gros progrès pour la _non-mesh representation_, mais le changement vers les mesh c'est chaud (⚠️ video pré Meshtron et llama-mesh). 

# Pipeline
![200](screenshot%202025-01-02%20à%2017.28.42.png)
## Multiview stable diffusion
It's usually the first step. Not in details here, but there is a course on hugging face. 
ça va rester utile pour nous pour ce qui est la vue isométrique 2D etc). [Lien du google collab](https://colab.research.google.com/github/dylanebert/ml-for-3d-course-notebooks/blob/main/multi_view_diffusion.ipynb#scrollTo=ARoZb5Shk8t6) de l'implémentation d'une pipeline de génération d'image 2D avec le modèle `dylanebert/multi-view-diffusion`. Marche pas trop, je dois comprendre pourquoi, et c'est une bonne première étape pour mettre les mains dedans. 

## ML-friendly ?
ML-friendly representations : [NeRF](NeRF.md) or [GS](Gaussian%20splatting) par exemple. Dans ce cours il focus sur le Gaussian splatting. 
Pour être ML friendly : _differentiable_ 
Les modèles sont nuls avec des données brutes, ils aiment quand c'est 'fuzzy' et continu (c'est à dire differentiable). 
[GS collab](https://colab.research.google.com/github/dylanebert/ml-for-3d-course-notebooks/blob/main/gaussian_splatting.ipynb)
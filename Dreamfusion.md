#tool #implementation #model #hilevel
2022 Made in Google
[Paper](https://arxiv.org/pdf/2209.14988) : DREAMFUSION: TEXT-TO-3D USING 2D DIFFUSION
[Notebook](https://colab.research.google.com/drive/1MXT3yfOFvO0ooKEfiUUvTKwUkrrlCHpF?usp=sharing) de codes de NeRF avec dream diffusion. (stable dreamfusion)
___
[Github](https://github.com/ashawkey/stable-dreamfusion?tab=readme-ov-file) stable dreamfusion : implémentation pytorch d'un PhD Chinois. 
[Github](https://github.com/threestudio-project/threestudio) de threestudio, pas bien capté ce que c'est, mais ça a l'air lié à Stable Dreamfusion. 

Le travail réalisé dans le paper décrit l'adaptation d'un modèle de génération d'image 2D (text2img come Stable Diffusion) pour créer des assets 3D. Fortement ressemblant à des outils plus récents, plus puissant comme [EdgeRunner](EdgeRunner.md), [MeshAnything](MeshAnything.md). 

Utilisation de [zero123](zero123) dans la pipeline. 

Ce qui reste pertinent ça serait toute l'analyse sur la loss function, score distillation etc. 
#implementation #hilevel 
___
[Paper](https://arxiv.org/pdf/2305.11588)
[Video du paper](https://www.youtube.com/watch?v=G3xiabqcv3E)
Implémentation du modèle [NeRF](NeRF.md) avec de la reco de texte. Paper chinois, voir si c'est pas juste du réchauffé, j'ai l'impression que c'est une implémentation basique. Voir c'est quoi la dif avec text2mesh. $\to$ #todo à confirmer avec les autres papers

# Pipeline description
[Pipeline text2nerf full explanation](Pipeline%20text2nerf.md)
![](screenshot%202024-12-23%20à%2011.38.32.png)

## Steps in a nutshell
- inpainting : a view with a changed perspective (variation of the initial view $I_{0}$). 
- $I_{k}^R$ en mode raw, avec les zones qui manquent et 
- $\hat{I}_{k}$ la reconstruction d'une scene complète en 3D (avec sa depth map $D_{k}^E$)
- Et puis le mix entre la depth map originale $D^R_{k}$ et la nouvelle $D_{k}^E$ pour créer la depth map finale $\hat{D}_{k}$ (j'imagine le mix des 2 c'est pour assurer une cohérence). 


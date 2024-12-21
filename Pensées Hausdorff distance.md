Imaginons un espace latent avec des formes, et suivant le même référentiel d'espace, avoir un espace latent avec les mots. 
On query des mots, et on calcule l'endroit de ce mot dans l'espace latent. 
On calcule la distance entre la query et les mots les + proches (10-20 mots les plus proches) et on estime cet endroit dans l'espace latent avec les formes. 
Ensuite, en fonction de la distance entre 2 mots, calculer la distance de Hausdorff en 3D, et trouver la forme qui réside précisément à la bonne distance des formes les + proches. 
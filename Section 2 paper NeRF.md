Les auteurs comparent leur solutions avec d'autres méthodes. Les ressources dans cette section pourraient être intéressantes. 

## Neural 3D shape representation
3D shapes as level sets : neural network that maps xyz to _signed distance functions_ or _occupancy fields_. 
Problème, il faut un dataset d'objets 3D assez robuste (ils utilisent le mot ground truth 3D shapes) ([ShapeNet](ShapeNet) dataset). __Intéressant en vrai pour ce qu'on veut faire.__
Il parle de quelques techniques puis dis ça : _Though these techniques can potentially represent complicated and high- resolution geometry, they have so far been limited to simple shapes with low geometric complexity, resulting in oversmoothed renderings._
A voir ce que ça veut dire over-smooth, mais ça pourrait être intéressant dans notre cas. 

## View synthesis and image-based rendering
Light field interpolation techniques. 
__Mesh based__ representation of the scene. Differentiable rasterizers or pathtracers peuvent optimiser la représentation d'un mesh pour reproduire un set d'image en input. Désavantage c'est qu'il faut un template mesh avec une topologie fixée (faisable pour nous ?). 

__Volumetric representations__ : recheck, g lu mais rien retenu


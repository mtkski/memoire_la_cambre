# App existantes

## Implémentations commerciales
- [Meshy](https://www.meshy.ai/?noRedirect=true) : close source, le + solide, multiple art styles, meshes with marching cubes certainly
- [Spine](https://spline.design/) : close source, 3D asset generator, more cartoon, close source, meshes with marching cubes certainly
- [Adam AI](https://www.makewithadam.com/) : close source, idée sliders
- [ThreeStudio](ThreeStudio.md) : open source, implémentation de Dreamfusion

# Scene gen
## NeRF
- [SIGNeRF](https://github.com/cgtuebingen/SIGNeRF)  ([paper](https://arxiv.org/pdf/2401.01647)): outil puissant pour l'editing de scene 3D, pour générer des NeRF à partir de scans.

## Gaussian splatting


# 'implicit' to mesh
- [EdgeRunner](EdgeRunner) 9/10/24 : trouvé sur le site d'un chercheur trouvé sur hugging face. 
- [MeshAnything](MeshAnything) 26/9/24 : Chercheurs NVIDIA de Pékin, img, NeRF, 3D GS, dense mesh, point cloud to __3D__. 
- [Dreamfusion](Dreamfusion.md) 2022 : + technique, low-level, made in google, mais pas le plus récent. 
- [Direct and Explicit 3D Generation from a Single Image](https://arxiv.org/pdf/2411.10947)
- [PartGen: Part-level 3D Generation and Reconstruction with Multi-View Diffusion Models](https://arxiv.org/pdf/2412.18608) : 29/12/24 
- [Treillis](https://trellis3d.github.io/) [paper](https://arxiv.org/pdf/2412.01506) 2/12/24 : imgto3D, textto3D, MicroSoft research


# Text to shape
## Meshes  
- [text2nerf](text2nerf.md) 31/1/24 : implémentation du modèle NeRF (check si ça fit dans cette catégorie ou plutôt dans ## NeRF). 
- [text2mesh (notes)](text2mesh.md) 6/12/24 : opensource, peut être intéressant dans la pipeline. 
- [Llama mesh](https://research.nvidia.com/labs/toronto-ai/LLaMA-Mesh/)
- [Meshtron](https://developer.nvidia.com/blog/high-fidelity-3d-mesh-generation-at-scale-with-meshtron/)

## NeRFs
- 

## CAD 
- Text to CAD de Raoul (juste une implémentation en ligne, mais quelle techno ?)
- [[Text2Cad]] : IA Technical Drawings and diffusion 

# Datasets
- [Obja-verse XL](Obja-verse%20XL)
- [ShapeNet](ShapeNet.md)
- [ABC (a big cad dataset)](https://arxiv.org/pdf/1812.06216v2)
- [ChangeIt3D](https://changeit3d.github.io/#dataset) : dataset qui lie des qualités géométriques aux mots. 
# Tools, UI & others
- [Comfy UI](https://github.com/comfyanonymous/ComfyUI) : UI pour implémenter des pipelines de diffusion etc. Potentiellement pas mal pour tout mettre ensemble (plutôt qu'un notebook)
- 
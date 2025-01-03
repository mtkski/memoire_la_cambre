#software #hilevel #tool 
___
[Lien du site](https://www.open3d.org/)
Logiciel qui sert à l'implémentation de pipeline et logiciels 3D. La force c'est de pouvoir le run dans un notebook, utile pour des POC, ou pour représenter des données brutes à mon avis. 
À voir si c'est utile ou pas spécialement. Comment l'utiliser ? 
___
Open3D is an open-source library that supports rapid development of software that deals with 3D data. The Open3D frontend exposes a set of carefully selected data structures and algorithms in both C++ and Python. The backend is highly optimized and is set up for parallelization. Open3D was developed from a clean slate with a small and carefully considered set of dependencies. It can be set up on different platforms and compiled from source with minimal effort. The code is clean, consistently styled, and maintained via a clear code review mechanism. Open3D has been used in a number of published research projects and is actively deployed in the cloud. We welcome contributions from the open-source community.

# Outils utiles (après survol de la doc)
- `point_cloud, compute_convex_hull`, `create_from_point_cloud_alpha_shape()`: representation et outils sur les point cloud.
- draw_geometries() et la classe _Vizualizer_.
- `transformer` des objets 3D (rotation, trans, scale) et calcul du mean et covariance du _point cloud_ pour le centrer. 
- `voxel_downsample(), remove_statistical_outlier(), estimate_normals()` : en gros filtrage et traitement. 
- `registration_icp()`: Enregistrement (alignement) rigide par l’algorithme _ICP_ (Iterative Closest Point). et `registration_ransac_based_on_feature_matching()`: Alignement initial basé sur les features et _RANSAC_. (je sais pas ce que c'est ptdr)
- `segment_plane()`: Détection et _segmentation_ des plans dans un nuage de points. `cluster_dbscan()`: Segmentation basée sur l'algorithme _DBSCAN_ pour détecter des clusters dans les données.
- `poisson_surface_reconstruction` maillage et surface (`create_from_point_cloud_alpha_shape()` également)
- `KDTreeFlann`: Structure pour des recherches rapides de voisinage (_k-nearest neighbors_). `Octree`: Structure hiérarchique pour organiser efficacement de grandes quantités de données.

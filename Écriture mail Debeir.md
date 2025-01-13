# Contexte
La première chose que l'on pourrait dire du domaine de la génération d'objets 3D, c'est que c'est un domaine en plein boom, tout comme la génération d'images 2D ou de videos il y a un an. 
Les papers sont assez récents, rarement open source, mais en tout cas cela prouve que la tâche est pertinente et au centre des préoccupations du monde de l'IA générative aujourd'hui. 

## Domaines
- Applications industrielles de VR/AR/XR. Par exemple Nvidia met beaucoup de moyens dans la recherche dans le domaine de la 3D dans une optique de développer l'interaction de systèmes informatiques et robotiques avec le monde réel comme la création de [digital twins](https://developer.nvidia.com/blog/experience-digital-twins-in-xr-with-nvidia-omniverse-spatial-streaming/) très précis (digital twin d'entrepôts pour des robots y travaillant par exemple) ou pour le scan et la création de modèle 3D précis pour l'industrie. ![300](https://developer-blogs.nvidia.com/wp-content/uploads/2025/01/wind-turbine-spatial-streaming-omniverse-digital-twins-workflow-apple-vision-pro.gif)
- L'aspect créatif : la génération d'assets 3D pour l'animation ou la création de scènes 3D artistiques. Les implémentations commerciales se basent sur la générations d'objets 3D aux formes et textures intéressantes, en ne cherchant pas le photo-réalisme. 
  _Génération 3D from text avec Spline ou d'animations 3D avec Meshy_. 
  ![200](screenshot%202025-01-10%20à%2016.12.28.png) ![100](https://www.meshy.ai/_next/image?url=https%3A%2F%2Fcdn.meshy.ai%2Flanding-assets%2Ffeatures%2Fanimation%2Fvictory_cheer_render.gif&w=640&q=75)![100](https://www.meshy.ai/_next/image?url=https%3A%2F%2Fcdn.meshy.ai%2Flanding-assets%2Ffeatures%2Fanimation%2Fvictory_cheer_skeleton.gif&w=640&q=75)![100](https://www.meshy.ai/_next/image?url=https%3A%2F%2Fcdn.meshy.ai%2Flanding-assets%2Ffeatures%2Fanimation%2Fcounter_strike_render.gif&w=640&q=75)
- Aide à la CAD : génération de modèles précis utilisables dans des logiciels de CAD, visant à accélérer, simplifier et rendre accessible la CAD. Les contraintes sont donc des objets 2D précis, idéalement modifiable selon les besoins. 
  ![300](screenshot%202025-01-10%20à%2016.17.49.png)

Le contexte de ce mémoire tombe précisément entre ces 2 derniers domaines d'application. Les designers industriels travaillent évidemment avec des modèles précis, dans des logiciels tels que Fusion360, mais une grande partie de leur travail implique la connaissance de principes artistiques, d'esthétisme, de considérations culturelles et de design. 

# Diffusion 2D
La plupart des outils de génération d'objets 3D partent d'un modèle de diffusion 2D pré-entrainé pour l'image initiale. Il y a une génération de multivues, et dans un second temp une interpolation de la géométrie complète du modèle, que ça soit par des NeRFs, du Gaussian Splatting ou plus récemment la génération de mesh directement. 

## Dataset 2D ?
Une des grandes questions de ce mémoire c'est comment générer un bon dataset, comment avoir une quantité de données suffisantes. Comme ordre de grandeur, on peut citer que pour un modèle de génération 2D pertinent, on aurait besoin de ±500K images, donc pour de la 3D, on devrait avoir besoin d'au moins quelques dizaines, voire centaines de milliers idéalement. 
Il y a des datasets d'objets 3D qui existent, pour ne citer que les 2 plus gros : [Obja XL](https://arxiv.org/pdf/2307.05663), [ShapeNet](https://arxiv.org/pdf/1512.03012). Ces datasets contiennent énormément d'objets physiques (voitures, meubles, animaux, etc) mais il manque une certaine part de "design" et de "conscience" géométrique. 

Générer un dataset complet de fichiers 3D n'est pas réaliste. Une idée serait alors de renforcer le modèle de diffusion 2D initial, les images étant bien plus répandues que les modèles 3D. Dans l'idée d'étoffer les connaissances du modèle en termes de design etc, on pourrait imaginer faire du webscraping en fonction des besoins de la Cambre pour ce modèle.

L'autre idée est de récupérer des données venant des étudiants etc, mais la plus grande question est de savoir si c'est pertinent au vu du nombre de données requise. Nous pensons que ça reste quelque chose qui serait assez intéressant, mais il reste à voir comment implémenter ceci dans une IA (par exemple donner + de poids pour cette petite partie des données). Ou alors imaginer des workshop avec la Cambre pour sensibiliser aux outils de générations, apprendre à communiquer avec ces modèles statistiques pour en sortir les choses les plus pertinentes possible etc. 

# Traduction 2D-3D
Cette étape est cruciale pour générer des mesh propres utilisables dans les logiciels de CAD pour le design industriel. Il existe plein de représentation d'objets et de scènes en 3D. On pourrait citer les [NeRFs](https://arxiv.org/pdf/2003.08934) ou le [Gaussian Splatting](https://arxiv.org/pdf/2308.04079), qui sont des représentations dites "implicites". C'est à dire qu'elle ne font que _représenter_ une scène 3D, pour de la VR ou AR par exemple. On peut voir ceci comme un réseau de neurone qui est overfité au maximum sur des données bien précises pour représenter au mieux la scène. 
Mais le paradigme principal du monde de la 3D est basé sur les maillages, les _mesh_. Plusieurs méthodes existent pour générer des mesh, ce qui était principalement utilisé précédemment est la méthode des marching cubes, plus récemment la recherche se dirige vers l'idée de tokeniser les vertices et générer les formes 3D par des LLM. 

## Marching cubes
Le paper initial de l'algorithme date de 1987. Des améliorations notables ont eu lieu pendant son histoire, notamment assez récemment avec "Neural Marching Cubes" en 2021. Les surfaces générées sont plus propres, donnant moins cette illusion d'approximation. 
Mais le plus gros problème reste la topologie assez complexe et difficilement utilisable dans un contexte de CAD ou de design. 
_Image issue de "Neural Marching cubes". On voit le côté un peu imprécis des marching cubes traditionnels, la meilleure netteté des NMC, mais tout de même une complexité topologique._ 
![400](screenshot%202025-01-10%20à%2015.33.48.png)
_Comparaison entre des mesh générés par marching cubes (version non précisée) vs un mesh généré par Meshtron de Nvidia._
![400](https://developer-blogs.nvidia.com/wp-content/uploads/2024/12/mesh-comparisons-625x487.jpg)

## Génération de mesh par diffusion
[Paper](https://arxiv.org/abs/2312.11417). 
L'idée est de faire de la diffusion avec des objets 3D. Assez lourde d'un point de vue computation, et de meilleurs outils ont été développés depuis un an. 
![](screenshot%202025-01-10%20à%2019.41.22.png)

## Génération du mesh par LLM
L'idée est de tokeniser les formes 3D par un LLM, en encodant les vertices de manière optimisée et en entrainant le modèle à générer des suites de vertices pertinentes en fonction de requêtes textuelles, comme un modèle de language classique. Plusieurs papers explorant cette idée sont parus récemment, avec des rendus relativement proches, mais avec des différences dans l'approche. 

### MeshAnything
[MeshAnything v2](https://arxiv.org/pdf/2408.02555). 

### Meshtron
Une approche intéressante, adoptée par Nvidia dans le paper "[Meshtron](https://developer.nvidia.com/blog/high-fidelity-3d-mesh-generation-at-scale-with-meshtron/)" est d'entrainer un LLM, qui apprendrait à "tokeniser" des objets 3D qui sont codées sous forme explicite, comme les fichiers `.obj` qui sont du simple texte qui décrit les élèments géométriques clés de l'objet. 
___
Le format de fichier OBJ permet à l’utilisateur de tesseller une surface de modèle 3D à l’aide de formes géométriques simples ou complexes. Pour l’encodage de la géométrie de surface d’un modèle, un fichier stocke les sommets et la normale à chaque polygone. On peut également générer des courbes de formes libre. 
___
De par son expressivité et son encodage plutôt lisible, le type `.obj` parait être un bon candidat pour cette méthode. 

Meshtron est un outil capable de générer des mesh 3D topologiquement correct. Le terme qu'ils utilisent est _artist-like_ meshes, c'est à dire un mesh qui est utilisable dans des contextes de création, on peut facilement modifier l'aspect du mesh sans devoir fort le retravailler. C'est une qualité qui manquait dans certains modèles de génération 3D qui utilisaient en général la méthode des _marching cubes_. Les rendus étaient moins précis, donnant une illusion d'approximation. 

_A diagram shows that hand-designed algorithms like Marching Tetrahedra and Marching Cubes produce dense meshes that lack adaptivity. This results in meshes with missing details, bumpy geometry, and uninformative tessellation. Meshtron, as a data-driven algorithm, produces artist-like topology with great geometric detail, even at a lower face count._

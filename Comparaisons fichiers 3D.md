#lowlevel 
___
La question c'est de savoir quel type de fichier va être le plus performant  avec un LLM. Qu'est ce qui va bien marcher. 

# Types de fichiers
## STL 
Séries de _triangles_, big file size.
Utile pour l'impression 3D (de base développé pour ça). 
Type de fichier binaire, mais version ascii existe. 
Les vertices des n triangles qui constituent le mesh sont encodés de la manière suivante : 
``` .stl
facet normal ni nj nk
    outer loop
        vertex v1x v1y v1z
        vertex v2x v2y v2z
        vertex v3x v3y v3z
    endloop
endfacet
```
Les coordonnées des points sont arbitraires.  
### Vertex to vertex rule
According to this rule, each triangle shares _two vertices_ with each of its adjacent triangles. Thus, a vertex of one triangle cannot lie on the side of another triangle.

## STEP 
Vector file. Cleaner surface, cleaner file, smaller file.  
Binaire ? Peut être pas le plus lisible pour un LLM. 

## OBJ
[Bonne explication](https://docs.fileformat.com/fr/3d/obj/) de ce que c'est, de quoi c'est capable. 
Encodage des vertices, assez léger, plutôt lisible. Ma question c'est comment il arrive à faire sens de ces chiffres randoms et discriminer entre les formes etc. 
Ça a l'air d'être le type de fichier le + expressif. Vu que c'est du plain text, c'est "facilement" tokenizable, maintenant il faut comprendre combien il faut lui donner, (et comment) pour que le LLM capte quelque chose. 

## 

# Que veut un LLM ?
[[LLMs]]
Le plus gros challenge c'est la tokenization. Comment encoder des coordonnées (ou autre) pour un LLM ? 
On peut s'inspirer de ce qui se fait dans le paper de meshtron. Capter exactement ce qu'ils tokenizent, dans l'article sur Nvidia dev ils ne rentrent pas trop dans les détails. 

# Combien ?
Idées de l'ordre de grandeur (généré par GPT),  

| Domaine             | Nombre de données nécessaires |
| ------------------- | ----------------------------- |
| Génération de texte | 100M+ de phrases              |
| Images (diffusion)  | 1M+ d'images                  |
| Musique             | 10k morceaux                  |
| 3D (formes)         | 🔥 Entre 10k et 100k          |


- **1 000 formes** → Génère des formes similaires au dataset d’origine. Peu créatif.
- **10 000 formes** → Commence à créer des designs nouveaux mais parfois incohérents.
- **50 000 formes** → Produit des formes cohérentes avec une bonne diversité.
- **100 000 formes** → Génération ultra-variée et utile pour des applications réelles

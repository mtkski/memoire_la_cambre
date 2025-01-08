#lowlevel #technique 
___
[Paper](https://arxiv.org/pdf/2003.08934): Representing Scenes as Neural Radiance Fields for View Synthesis.
[Video computerphile](https://www.youtube.com/watch?v=wKsoGiENBHU)
NeRF = [Neural Radiance Field](Neural%20Radiance%20Field)
NerfStudio : outil (framework?) pour travailler avec des nerfs. 

# Questions
- Diff between fully connected neural network (as in the paper) and convolutional. 
- Comprendre l'idée du rendering. On a juste une représentation 2D implicite ? Ou un objet 3D + complet ? ✅
- Différence entre light field et radiance field ? 
- COLMAP pour la structure from motion. C quoi ? Utile ? 

# L'idée
3 grandes choses proposées dans le paper : 
- C'est représenter un "neural radiance field" 5D d'une scène 3D, paramétrisé sous forme d'un réseau neuronal. 
- Technique de rendering différentiel (ça veut dire qu'on peut utiliser le gradient descent pour calculer l'erreur de la représentation 2D). #todo bien capter cette partie là.  
- Encodage de chaque input 5D vers un espace de dimension supérieure qui permet d'améliorer la précision des high frequency (les détails). 

# Technique 
Our method optimizes a deep _fully-connected neural network_ without any convolutional layers (often referred to as a multilayer perceptron or MLP) to represent this function by regressing from a single 5D coordinate (x,y,z,θ,φ) to a single volume density and view-dependent RGB color.

L'entrée c'est un light field 5D : xyz et l'angle θ,φ. 
L'output c'est une représentation '2D' : couleur rgb et la "densité"

La __pipeline__ c'est  : 
1) une représentation des rayons, 
2) qu'on plug dans un réseau neuronal et cela donne la couleur et la "densité". 
3) on génère un volume. 
4) On minimise l'erreur entre ce qui est généré et le réel. 

# Revue de la littérature
[Revue de la litérature](Section%202%20paper%20NeRF)

# Neural radiance field scene representation
The 5D scene is approximated by a MLP network : $F_{Θ} : (x, d) → (c, σ)$. 
Les weights $\Theta$ sont optimisées pour mapper chaque coord input 5D à son volume density et couleur directionnelle émise correspondante. 
On encourage le multivue en demandant au réseau de prédire le _volume density_ seulement en fonction de (x, y, z) (l'angle de vue n'auras donc pas d'influence, scène + robuste). 
Pour faire ça : 
1) $F_{\Theta}$ process __x__ = $(x, y, z)$ avec 8 couches fully connectées (ReLU et 256 channels per layers). Il output $\sigma$ et un vecteur de features de 256D. 
2) Ce feature vecteur est concatené avec l'angle de vue ($\theta, \phi$) et est passé dans une couche supplémentaire (ReLU et 128 channels) that output the view-dependent RGB color. 

# Volume Rendering with Radiance Fields (math math math)
Section vide pcq monkey brain. 

# Optimizing a NeRF
⚠️ Les réseaux neuronaux profond ont du mal à aproximer des fonctions haute fréquence. (This is consistent with recent work by Rahaman et al. [35], which shows that deep networks are biased towards learning lower frequency functions.). 

## Positional encoding
C'est pour ça qu'en fait $F_{\Theta}$ est une composition de 2 fonctions, une apprise, l'autre pas : $F_{\Theta}=F_{\Theta}'\circ \gamma$. 
$\gamma$ est un mapping de $\mathbb{R}$ vers $\mathbb{R}^{2L}$ et $F_{\Theta}'$ est toujours un MLP. 
$$\gamma(p) = (\sin(2^{0}\pi p), \cos(2^{0}\pi p), \dots, \sin(2^{L-1}\pi p), \cos(2^{L-1}\pi p))$$

Appliquée séparement à chacune des 3 coords de $\textbf{x}$, normalisées pour être entre \[-1, 1\]. 
Dans leur architecture: L = 10 for $\gamma(\mathbf{x})$ and L = 4 for $\gamma(\mathbf{d})$.

## Hierarchical volume sampling
À la place de sampler de manière random, et finalement quand même donner de l'importance à des rayons qui n'ont aucune influence sur la scène finale (rayons cachés ou "free" (jsp ce qu'ils entendent par free)) on va essayer d'influencer le sampling pour qu'il soit + pertinent. 
$\to$ la solution est d'avoir 2 networks : __coarse__ et _fine_.
__Coarse__ est constitué de $N_{c}$ samples, via les équations vues plus haut. À l'aide de l'output de ce réseau coarse, on va faire un sampling + informé qui sera biaisé vers les parties relevant du volume. C'est fait en réécrivant la formule de $\hat{C}(\mathbf{r})$. Il va être fait un sampling de $N_f$ sample, et la couleur va être trouvée avec l'equation de C plus haut en lui donnant $N_{c}+N_{f}$. 
_This procedure allocates more samples to regions we expect to contain visible content._

## Détails de l'implémentation
Ils optimisent un réseau séparé pour chaque scène : nécessite simplement un dataset d'images RGB, les cameras poses et données cam, limites de la scène _(we use ground truth camera poses, intrinsics, and bounds for synthetic data, and use the COLMAP structure-from-motion package [39] to estimate these parameters for real data)_. 
Le loss est simplement calculé comme le total squared error entre le rendu et le true pixel color, du __coarse__ ET du _fine_. 
Note : même si le resultat final vient du fine, on minimise le loss du coarse pour avoir un sampling  intéressant.
[Chiffres de l'implémentation](Détails%20techniques%20implémentation%20NeRF)

# Results
#todo éplucher un peu ça. 
Il compare d'autres méthodes, et parle de leur utilisation en espace et en temps. 
Leur méthodes est vraiment très clean. 
Chapeau l'artiste. 

A propos  de [Text2Cad](https://arxiv.org/pdf/2411.06206) 

Ce paper explique comment générer des fichier CAD a partir de prompt.
Pour ceci, plusieurs technologies sont utilisées.

Ils passent par la génération d'image Isométrique avec un model de diffusion qui est ensuite transformé en fichier STEP au travers d'un pipeline de transformation.
**Isometric image of a gear**
![[isometric_view_of_gear.png|400]] 





Le pipeline de training se passe comme ceci:
```mermaid

flowchart TB

    A[STEP files] --> |With FreeCAD| B[Isometric Image]

    A --> |With FreeCAD|C(Front view)

    A --> |With FreeCAD|D(Front view)

    A --> |With FreeCAD|E(Front view)

    B --> |Ask GPT for description|F[generated prompt]

    F --> |Train a diffusion model to generate isometric image bases on prompte| G[isometric diffusion model]

    G --> |Train a zero-1-to-3 model to generate top,front and side image base on isometric image|H[TOP FRONT SIDE diffusion model]

    C --> H

    D --> H

    E --> H

    H --> |Reconstruct 3D file with Photo2CAD| I[STEP file]
    


````



**ZERO-1-to-3** model allow to generate other angle view from a single image (ideal pour générer les top, front et side view)


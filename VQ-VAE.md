#lowlevel #concept 
[Paper](https://arxiv.org/pdf/1711.00937) made in Google, 2018. 
___
VQ-VAE = Vector quantized auto-encoder. 

L'idée c'est de pouvoir output des _données discrètes_ avec un modèle de ML. Et les données discrètes qu'on output ne sont pas statiques, mais apprises pendant le learning. 
Dans les exemples d'output c'est des images, des videos, et aussi le speech (il a une grosse capacité à segmenter en phonemes, d'où l'utilité des représentation dites apprises). 
Apparemment avec la première phase qui est la _vector quantization_, on évite des problèmes récurrents qu'on a typiquement avec les VAE classiques. 

Maintenant qu'est ce qu'ils entendent par données discrètes ? Est ce qu'un "chien" c'est une donnée discrète ? Une catégorie qu'il aurait apprise en fonction du dataset ? Ou quelque chose de plus bas niveau, genre des pixels ou jsp. Pour le speech, dans l'abstract il a parlé de phonemes, pas spécialement de mots. À vérifier si le besoin se présente. 

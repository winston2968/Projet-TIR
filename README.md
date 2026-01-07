# 🔬 Travaux d'Initiation à la Recherche

Ce repo présente le travail effectué dans cette UE au cours du S8 du Master IMA. L'objectif est de rédiger une état de l'art dans un domaine précis de la recherche en Intelligence Artificielle. 

---
## 📁 Structure 

Le projet se structure comme suit : 

```
.
├── notes
├── README.md
├── report
│   ├── figures
│   │   └── logo_UT.png
│   ├── main.pdf
│   ├── main.tex
│   ├── Makefile
│   ├── references.bib
│   └── sections
│       └── example_1.tex
└── ressources
```

---
## 📑 Rapport 

### Rédaction 

Le rapport est compilé en LaTeX. La rédaction des sections se fait dans des fichiers dédiés du dossier ```report/sections/``` pour ne pas compromettre le travail global. L'Introduction et la Conclusion se feront directement dans le fichier ```main.tex```. 

Comme montré dans le fichier ```main.tex```, l'ajout de nouvelles sections n'est pas difficile. Il suffit seulement de créer un nouveau fichier ```.tex```dans le dossier ```sections/```puis de l'inclure à l'endroit voulut dans le rapport via la commande ```\input{chemin-du-fichier}```. 

### Compilation 

Un fichier ```Makefile``` est dédié à la compilation du rapport directement dans le dossier ```report/```. 
Pour cela, il suffit d'avoir installé la commande ```pdflatex``` disponible nativement dans la plupart des distributions LaTeX. 

La compilation de l'ensemble du rapport se fait en laçant la commande ```make```depuis le dossier ```report/```. Les fichiers de builds peuvent être supprimés via la commande ```make clean```pour éviter de polluer le GitHub. 

---
## 📚 Notes 

Le dossier ```notes/``` est consacré à la relecture des articles choisis qui peuvent éventuellement être stockés dans le dossier ```ressources/```. L'édition des notes pourra se faire au format Markdown (```.md```) qui supporte les formules LaTeX et est facile à modifier. 

Ces notes seront la base du rapport, rédigé dans un second temps. 





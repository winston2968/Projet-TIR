# État de l'Art : Fiabilité et Certification des Frameworks d'Explicabilité en IA

## Description du sujet
Ce projet explore le paysage actuel des méthodes d'explicabilité (XAI), en opposant les outils populaires utilisés en entreprise (comme SHAP ou LIME) aux récentes avancées de la recherche fondamentale qui pointent leurs failles. L'objectif est de comprendre comment transformer l'explicabilité d'un simple outil de visualisation en un mécanisme de **défense et de certification** robuste. Nous analysons si les explications fournies par les frameworks actuels sont mathématiquement fondées, computables à grande échelle et protégées contre la manipulation.

---

## Plan de l'État de l'Art

### I. Introduction
* **Contexte :** L'omniprésence des modèles "boîtes noires" et l'exigence de transparence (IA Act).
* **Problématique :** Les frameworks d'explicabilité actuels sont-ils suffisamment fiables pour servir de preuve juridique ou de mécanisme de défense ?
* **Définitions :** Interprétabilité intrinsèque vs explicabilité post-hoc.

### II. Panorama des Frameworks d'Explicabilité Pratiques
* **Méthodes basées sur les perturbations :** Focus sur SHAP (Shapley Values) et LIME.
* **Méthodes basées sur les gradients :** Integrated Gradients, Grad-CAM (pour le Deep Learning).
* **Explications contrefactuelles :** Le modèle "What-if" pour l'utilisateur final.



### III. L'Approche Axiomatique : Définir la "Bonne" Explication
* **Théorie :** Pourquoi l'intuition ne suffit pas (le besoin de propriétés mathématiques).
* **Stabilité et Sensibilité :** Une explication doit être constante pour des entrées similaires.
* **Lien avec la Réf (1) (Amgoud et al.) :** Utilisation des caractérisations axiomatiques pour évaluer si les explicateurs basés sur des échantillons sont légitimes.

### IV. La Complexité du Passage de l'Individu au Modèle (Local vs Global)
* **Le défi du changement d'échelle :** Pourquoi comprendre une décision locale ne signifie pas comprendre le modèle entier.
* **Limites computationnelles :** La difficulté de certifier un modèle globalement.
* **Lien avec la Réf (2) (Bassan et al.) :** Analyse de la complexité algorithmique (NP-dureté) du passage de l'interprétabilité locale à globale.

### V. Vers une Explicabilité Certifiée et Trustable
* **Le problème des approximations :** Les dangers des scores SHAP estimés.
* **Audit et Vérification Formelle :** Comment rendre les scores inattaquables.
* **Lien avec la Réf (3) (Létoffé et al.) :** Étude des méthodes permettant d'obtenir des scores SHAP exacts et vérifiables pour garantir la confiance.

### VI. Synthèse Critique : Défense et Robustesse
* **La manipulation des explications (Fairwashing) :** Comment des modèles biaisés peuvent paraître "justes".
* **Recommandations :** Vers un standard d'ingénierie pour le choix des frameworks selon la criticité du domaine (Santé vs Marketing).

### VII. Conclusion
* Résumé des enjeux : de l'explication "esthétique" à l'explication "certifiée".
* Perspectives : L'explicabilité des Large Language Models (LLM).

---

## Liens avec vos références clés

1.  **Amgoud et al. (ECAI 2024) :** Utilisé dans la **Section III** pour fournir le cadre théorique. Cet article permet de critiquer les frameworks comme LIME en montrant qu'ils ne respectent pas toujours les axiomes fondamentaux de stabilité.
2.  **Bassan et al. (ICML 2024) :** Central dans la **Section IV**. Il sert à démontrer que la "défense" globale d'un modèle est mathématiquement coûteuse et aide à choisir entre une approche locale (spécifique) ou globale (générale).
3.  **Létoffé et al. (AAAI 2025) :** Pilier de la **Section V**. Il permet de traiter le cas pratique de SHAP, en montrant comment passer d'une application "floue" à un outil de haute précision pour les systèmes critiques.

---

## Références complémentaires suggérées

* **Ribeiro et al. (2016) :** *"Why Should I Trust You?": Explaining the Predictions of Any Classifier* (L'article fondateur de LIME).
* **Lundberg & Lee (2017) :** *A Unified Approach to Interpreting Model Predictions* (L'article fondateur de SHAP).
* **Molnar, C. (2022) :** *Interpretable Machine Learning* (Une excellente ressource globale pour la partie pratique).
* **Slack et al. (2020) :** *Fooling LIME and SHAP* (Pour la partie sur la défense et la manipulation des explications).
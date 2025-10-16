# Projet d'Audit Commercial (Retail Audit) CHOCOCAM 

## Phase ASK

Ce projet a été conçu pour transformer des données de ventes brutes en informations stratégiques, afin d'évaluer la Part de Marché (PDM) estimative de CHOCOCAM sur cinq ans. L'objectif global est de justifier la position actuelle de l'entreprise face à la concurrence et de recommander des ajustements stratégiques basés sur la croissance et la politique de Prix Unitaire Moyen.

---

### 1. Définition Claire du problème : 
Déterminer la Part de Marché (PDM) estimative de CHOCOCAM par rapport à la concurrence sur les cinq dernières années. L'analyse doit identifier et quantifier les facteurs clés (croissance des ventes, élasticité prix-volume, performance des marques et segmentation géographique) qui justifient la position actuelle de l'entreprise sur le marché.

### 2. Description des sources de données : 
- Données Primaires : Fichiers bruts d'enquêtes de Retail Audit (.csv ou .sav) fournissant les volumes de stock et d'achat par point de vente.
- Données Secondaires : Fichiers de référence pour la nomenclature des produits et la hiérarchie commerciale.

### 3. Documentation de tout Nettoyage ou Manipulation (Plan) :
- Création de la Métrique Clé : Dérivation de la Vente au Client Final (Stock Initial + Achat – Stock Final).
- Gestion des Aberrations : Détection et exclusion des valeurs de Vente_Finale négatives et des outliers extrêmes.
- Contrôles d'Intégrité : Vérification de la cohérence entre les colonnes (Chiffre_Affaires_XAF doit être ≈ Volume_Ventes_KG × Prix_Unitaire_Moyen_XAF) et traitement des outliers de Prix_Unitaire_Moyen_XAF.
- Standardisation : Uniformisation des chaînes de caractères pour les colonnes Marque, Acteur et Catégorie.
- Formatage : Conversion des champs monétaires et volumétriques en format numérique et des champs Date en format Date.

### 4. Résumé de votre Analyse (Plan d'Action)
L'analyse se concentrera sur l'évaluation de la performance et de l'efficacité opérationnelle :
- Analyse de Corrélation : Quantification de l'impact des facteurs d'exécution (Distribution Numérique et Taux de Rupture de Stock) sur la PDM.
- Analyse de Pareto : Identification des points de vente ou des segments de produits qui génèrent la majorité des ventes (Principe 80/20).
- Analyse de la Série Chronologique : Évaluation de la PDM de CHOCOCAM vs. Concurrence par Mois et Année sur 5 ans (justification de la tendance).
- Analyse de l'Élasticité Prix : Quantification de l'impact des variations du Prix Unitaire Moyen (PUM) sur le Volume_Ventes_KG et la PDM globale.
- Analyse de Segmentation : Décomposition de la PDM par Acteur (canal de distribution) et par Zone_Géo pour identifier les points forts/faibles.

### 5. Visualisations de Soutien et Constatations Clés (Plan)
Les visualisations principales seront conçues pour l'impact stratégique :
- Carte Géographique : Mise en évidence des zones de forte demande mais de faible Distribution Numérique (Opportunités d'investissement).
- Diagramme de Pareto/Barres : Représentation du Taux de Rupture de Stock par région pour quantifier l'inefficacité opérationnelle.
- Graphique Linéaire de PDM : Évolution de la Part de Marché de CHOCOCAM vs. Concurrence sur 5 ans (Tendance Stratégique).
- Carte de Chaleur (Heatmap) : Matrice PDM vs. PUM par Zone_Géo (Visualisation de la stratégie de positionnement prix par marché).
- Diagramme en Barres Empilées : Décomposition de la PDM par Acteur pour montrer les canaux de distribution qui soutiennent le plus la position actuelle.

### 6. Livrables Supplémentaires pour Exploration Future
- Modèle de Prédiction de Rupture de Stock : Développer un modèle de machine learning pour anticiper les points de vente à haut risque de rupture, permettant une - ---------- intervention logistique proactive.
- Tableau de Bord de Data Quality : Un outil de supervision pour évaluer les biais et la fiabilité des données collectées par les enquêteurs.

### 7. Insights de haut niveau
- Justification de la PDM : La PDM actuelle est principalement soutenue par le canal Acteur X et la Zone_Géo Y.
- Optimisation des Prix : La croissance du volume (KG) est freinée par une politique de prix trop rigide. Une stratégie de PUM plus dynamique par zone pourrait stimuler la PDM.
- Risque de Concentration : La PDM présente un risque de concentration élevé, dépendant fortement de la performance de deux marques clés.
- Priorité à l'Exécution (TRS) : La croissance de la PDM de CHOCOCAM est potentiellement plus limitée par les problèmes de Taux de Rupture de Stock que par la demande consommateur.
- Ciblage Stratégique : La consolidation des ventes est concentrée sur un petit réseau de détaillants ; le renforcement de la Distribution Numérique doit être ciblé sur ces - points de vente à forte valeur.
- Menace Concurrentielle : Identification des régions spécifiques où la croissance d'un concurrent nécessite une réponse immédiate.



## Phase PREPARE
Cette phase consiste à obtenir et à structurer les données du Retail Audit pour garantir leur qualité et leur pertinence (test ROCCC). L'objectif est d'assurer que l'ensemble de données est propre et organisé pour le calcul de la Part de Marché (PDM) et l'analyse de l'élasticité prix..

---

### 1. Where is your data located?
Les données initiales sont collectées sur le terrain via une application mobile (ex: CSEntry) et sont stockées dans une base de données centralisée (souvent SQL Server ou PostgreSQL) pour l'harmonisation. Les fichiers bruts sont ensuite importés dans l'environnement d'analyse (R ou Python).

### 2. How is the data organized?
- Les données brutes sont organisées en tables relationnelles qui seront combinées en un modèle en étoile (Star Schema) pour l'analyse.
- La Table de Faits contiendra les métriques clés (Volume_Ventes_KG, Chiffre_Affaires_XAF) et sera liée aux Tables de Dimensions qui fournissent le contexte (Marque, Catégorie, Zone_Géo, Date).

### 3. Are there issues with bias or credibility in this data? Does your data ROCCC?
- Biais : Le risque principal est le biais de saisie (erreurs des enquêteurs sur les stocks ou les prix) et le biais d'échantillonnage (si le réseau de points de vente audité n'est pas parfaitement représentatif du marché national).
- Crédibilité : La crédibilité est forte car la source est interne (collecte contrôlée) et repose sur une méthodologie de calcul standard de la vente finale (Stock Initial + Achat – Stock Final).

#### ROCCC :
- Relevant : Oui, toutes les colonnes sont directement liées au calcul de la PDM et à l'analyse de la performance prix.
- Original/Complet : Oui, après imputation des valeurs manquantes faibles. La profondeur de l'historique (5 ans) est un atout de complétude.
- Current : Oui, les données sont mises à jour mensuellement, assurant leur actualité pour la prise de décision.
- Correct : Oui, après l'exclusion des outliers de prix et des valeurs logiquement impossibles (ventes négatives).
- Comprehensive : Oui, les données sont standardisées et les identifiants de zone sont clairs pour les équipes.

### 4. How did you verify the data’s integrity?
- Contrôle Automatique : Utilisation de scripts R/Python pour vérifier la cohérence arithmétique (Chiffre_Affaires_XAF ≈ Volume_Ventes_KG × Prix_Unitaire_Moyen_XAF).
- Validation Manuelle : Les valeurs aberrantes de PUM sont signalées et renvoyées aux superviseurs pour une vérification terrain.

### 5. Are there any problems with the data?
Le problème principal est la gestion des valeurs manquantes dans les colonnes de stock pour les points de vente non observés. De plus, les erreurs de saisie des prix unitaires nécessitent une détection et un traitement rigoureux pour éviter de fausser les calculs de PDM en valeur.

### 6. How are you addressing licensing, privacy, security, and accessibility?
- Licensing & Security : L'analyse est effectuée sur une instance de base de données sécurisée. L'accès aux données brutes est limité aux analystes et auditeurs autorisés via des identifiants et des rôles.
- Privacy : Les données des points de vente sont agrégées par Zone_Géo et Acteur dans les rapports finaux. Aucune donnée individuelle ou sensible de détaillant n'est divulguée.
- Accessibility : Les résultats finaux (PDM, tendances) sont partagés via un Tableau de Bord Power BI interactif, assurant une accessibilité facile pour les managers.

### 7. How does it help you answer your question?
L'organisation et la qualité des données (après nettoyage) sont cruciales, car elles permettent de calculer la PDM de manière fiable (un calcul basé sur la cohérence des ventes de CHOCOCAM et de l'ensemble du marché). Sans intégrité des données, toute conclusion stratégique sur l'élasticité prix ou la croissance serait invalide.


## Phase PREPARE

Cette phase décrit l'utilisation des outils et les étapes de nettoyage pour garantir la qualité et la reproductibilité de l'analyse.

---

### 1. What tools are you choosing and why? (Quels outils choisissez-vous et pourquoi ?)
- R (avec le package tidyverse) : Choix privilégié pour le nettoyage, la transformation et la création de variables. R excelle dans la manipulation de données tabulaires (avec dplyr) et la gestion des séries chronologiques, ce qui est crucial pour le suivi de la PDM sur 5 ans.
- Power BI : Utilisé pour la visualisation dynamique et le calcul de la PDM finale via DAX. Power BI permet une modélisation efficace du schéma en étoile pour l'analyse agrégée par zone et par marque.

### 2. Have you ensured your data’s integrity? (Avez-vous assuré l'intégrité de vos données ?)
Oui, l'intégrité est assurée par un processus en deux étapes :
- Contrôle en Amont : Vérification de la cohérence arithmétique de la variable Chiffre_Affaires_XAF (qui doit être égale ou très proche du produit des colonnes Volume_Ventes_KG et Prix_Unitaire_Moyen_XAF).
- Contrôle des Limites Logiques : Vérification qu'aucune colonne critique (telle que Volume_Ventes_KG ou Prix_Unitaire_Moyen_XAF) ne contient des valeurs négatives ou nulles là où ce n'est pas permis par la logique commerciale.

### 3. What steps have you taken to ensure that your data is clean? (Quelles mesures avez-vous prises pour garantir la propreté de vos données ?)
Les étapes de nettoyage concrètes comprennent :
- Standardisation des Types : S'assurer que les champs Volume_Ventes_KG, Chiffre_Affaires_XAF et Prix_Unitaire_Moyen_XAF sont bien numériques. Conversion des noms des marques/acteurs en minuscules pour la standardisation du texte.
- Gestion des Outliers : Utilisation de la méthode de l'Écart Type pour identifier et mettre en évidence les valeurs de Prix_Unitaire_Moyen_XAF qui se situent à plus de 3 ou 4 écarts-types de la moyenne régionale (Erreurs de saisie probables). Ces valeurs extrêmes seront exclues ou corrigées après validation.
- Création de Variables : Calculer la PDM (Part de Marque) en divisant le Chiffre_Affaires_XAF de CHOCOCAM par le total du Chiffre_Affaires_XAF de la Catégorie dans la même Zone_Géo et Date.

### 4. How can you verify that your data is clean and ready to analyze? (Comment pouvez-vous vérifier que vos données sont propres et prêtes à être analysées ?)
- Tests Statistiques : Exécuter la fonction summary() ou glimpse() dans R pour vérifier que les statistiques descriptives (mean, min, max) des colonnes numériques sont logiques (Ex: min(Prix_Unitaire_Moyen_XAF) > 0).
- Vérification de la PDM Préliminaire : Calculer la PDM totale pour l'ensemble du marché. Cette PDM doit être de 100%. Si elle est inférieure ou supérieure, cela indique un problème dans la définition ou le filtrage du marché.
- Validation par l'Utilisateur : Le jeu de données final est présenté à l'équipe Ventes/Marketing (l'utilisateur expert) pour confirmer que les agrégations de ventes reflètent leur connaissance du terrain.

### 5. Have you documented your cleaning process so you can review and share those results? (Avez-vous documenté votre processus de nettoyage afin de pouvoir examiner et partager ces résultats ?)
Oui. Le processus de nettoyage et de transformation complet est documenté dans un Bloc-notes R Markdown dédié au dossier notebooks/. Ce document inclut :
- Le code exact utilisé pour la standardisation des noms.
- Les critères appliqués pour l'exclusion ou la correction des outliers de prix.
- La formule DAX/R utilisée pour la création des KPI d'agrégation et de la PDM.
Cela assure la transparence et la reproductibilité de l'analyse par les autres analystes de l'équipe.


## Phase ANALYZE
---
### 1. How should you organize your data to perform analysis on it?
Les données sont organisées selon une approche de modélisation en étoile (Star Schema) au sein de Power BI. Cela optimise le calcul des KPI agrégés (comme la PDM) et la navigation pour l'utilisateur final.

a. Table de Faits : Contient les métriques numériques clés : Volume_Ventes_KG, Chiffre_Affaires_XAF, Prix_Unitaire_Moyen_XAF.
b. Tables de Dimensions : Des tables séparées pour les attributs catégoriels afin de filtrer et segmenter l'analyse :

Dimension Temps : Liée aux colonnes Date, Mois, Année.
Dimension Produit : Liée aux colonnes Marque et Catégorie.
Dimension Géographique : Liée à la colonne Zone_Géo.
Dimension Acteur : Liée à la colonne Acteur (Canal de Distribution).

### 2. Has your data been properly formatted?
Oui. Après la phase PROCESS, les données ont été formatées comme suit :
- Numérique : Les champs monétaires et volumétriques (Chiffre_Affaires_XAF, Volume_Ventes_KG, Prix_Unitaire_Moyen_XAF) sont au format décimal.
- Temps : La colonne Date a été transformée en format Date standard, et une table calendrier a été créée pour permettre les calculs de Time Intelligence (Croissance Année/Mois/Trimestre).
- Texte : Les dimensions catégorielles (Marque, Catégorie, Zone_Géo) sont au format texte standardisé, garantissant que les filtres fonctionnent correctement.

### 3. What surprises did you discover in the data?
Une des surprises majeures concerne souvent la disparité entre la PDM en volume et la PDM en valeur, ainsi que l'élasticité prix :
- PDM Masquée : Une analyse par PDM en volume (Volume_Ventes_KG) pourrait montrer que CHOCOCAM est leader, mais la PDM en valeur (Chiffre_Affaires_XAF) est plus faible. Cela signale une faiblesse de la politique de Prix Unitaire Moyen (PUM) par rapport aux concurrents.
- Acteurs Dormants : L'analyse des acteurs révèle qu'un canal de distribution (Acteur X) a un PUM nettement plus élevé sans impact négatif sur le volume, indiquant une opportunité de maximiser les marges dans ce segment.
- Croissance Fantôme : Le Chiffre d'Affaires semble croître, mais l'analyse du PUM ajusté à l'inflation sur 5 ans pourrait révéler que la croissance réelle de la valeur est stagnante.

### 4. What trends or relationships did you find in the data?
Les tendances et relations identifiées sont cruciales pour justifier la PDM :
- Relation Prix-Volume (Élasticité) : Il existe une faible élasticité prix-volume pour la Catégorie A de CHOCOCAM, ce qui signifie que de légères augmentations du PUM n'affectent pas significativement le volume vendu. Ceci justifie l'augmentation des prix.
- Saisonnalité Structurelle : La PDM et les ventes sont fortement saisonnières, avec des pics récurrents dans le Mois X et Y. Cela permet de justifier la planification des achats et des promotions.
- PDM Géographique Polarisation : La Part de Marque est extrêmement polarisée : elle est dominante dans la Zone_Géo A (villes principales), mais marginale dans la Zone_Géo B (zones rurales), expliquant pourquoi la PDM nationale globale est moyenne.

### 5. How will these insights help answer your business questions?
Les insights générés répondent directement à la tâche commerciale : justifier la PDM et recommander des actions.
- Justification de la PDM : L'analyse de la Série Chronologique (5 ans) montrera si la PDM actuelle est due à une stagnation ou à une croissance lente par rapport à l'agressivité des concurrents.
- Optimisation des Prix : L'analyse de l'élasticité prix sur la Catégorie A et les Acteurs spécifiques fournira des recommandations directes : "Augmenter le PUM de X% sur la Catégorie A dans la Zone_Géo Z sans risquer une perte de volume significative."
- Allocation des Ressources : La cartographie des PDM par Zone_Géo et Acteur permettra à la Direction Commerciale de justifier une réaffectation du budget vers les zones de faible PDM où le potentiel de croissance est le plus élevé.

## Phase SHARE
Ici nous allons synthétiser les conclusions de l'analyse PDM de CHOCOCAM et les structurer en un récit ciblé pour l'auditoire.

Voici les réponses structurées en fonction de l'objectif de justification de la Part de Marché (PDM) et d'analyse de l'élasticité prix.
---
### 1. Were you able to answer the business question?
Oui, l'objectif principal est atteint. Nous avons pu déterminer la PDM estimative de CHOCOCAM par rapport à la concurrence sur les cinq dernières années et, surtout, nous avons quantifié les facteurs qui justifient cette position. L'analyse de l'élasticité prix-volume et la segmentation géographique ont permis d'identifier des leviers d'action concrets pour optimiser le Chiffre d'Affaires et la stratégie de tarification.

### 2. What story does your data tell?
L'histoire est celle d'un Leader de Volume confronté à un Défi de Valeur et de Ciblage.
- Le Cadre (Situation) : CHOCOCAM maintient une PDM forte en Volume (KG), ce qui justifie l'efficacité de sa distribution physique et la confiance des consommateurs dans la marque.
- L'Intrigue (Conflit) : Cette PDM en volume est compromise par une PDM en Valeur plus faible (où les concurrents gagnent du terrain), ce qui est directement lié à une politique de Prix Unitaire Moyen (PUM) trop rigide dans des zones à forte élasticité. La croissance est là, mais elle est mal valorisée.
- Le Message à Retenir (Résolution) : La Direction doit adopter une stratégie de tarification dynamique et localisée pour monétiser la forte demande existante et maximiser le Chiffre d'Affaires.

### 3. How do your findings relate to your original question?
La question était de justifier la PDM et d'identifier ses facteurs. Nos résultats fournissent cette justification :
- PDM Justifiée : La PDM actuelle est validée par l'historique quinquennal et montre une dépendance à des Acteurs (canaux) spécifiques et à la Catégorie A.
- Facteur Explicatif N°1 : L'analyse de l'élasticité prix montre que CHOCOCAM pourrait augmenter son PUM dans la Zone_Géo X sans perdre de volume significatif, ce qui répond directement à la nécessité d'optimiser la politique de prix.
- Identification des Risques : La forte polarisation de la PDM par Zone_Géo indique un risque de concentration élevé, justifiant un ajustement des investissements pour diversifier la croissance.

### 4. Who is your audience? What is the best way to communicate with them?
- La Direction (C-Level) : Ce public a besoin du message stratégique et des recommandations d'action rapides. La meilleure communication est un rapport PowerPoint court et axé sur les Takeaways financiers (Coût de l'Attrition, Bénéfice du Changement).
- Les Managers Terrain & Ventes : Ce public a besoin des détails opérationnels et des données exploitables. La meilleure communication est le Tableau de Bord Power BI interactif, qui leur permet de filtrer par zone, par produit ou par animateur pour identifier immédiatement les points de vente à risque.

### 5. Can data visualization help you share your findings?
Absolument. La visualisation est le seul moyen de communiquer efficacement la complexité des séries chronologiques et de l'élasticité prix :
- Un Graphique Linéaire superposant l'évolution du PUM et du Volume de Ventes sur 5 ans illustrera instantanément le point d'inflexion où l'augmentation des prix a commencé à impacter négativement les volumes (Élasticité).
- Une Carte de Chaleur (Heatmap) affichant la PDM en Valeur par Zone_Géo et Marque permettra à la Direction de voir immédiatement où le marché est le plus rentable ou le plus vulnérable.
- L'utilisation de couleurs et d'annotations dirigera le regard vers les anomalies de prix et les zones d'opportunité non exploitées. 

### 6. Is your presentation accessible to your audience?
Oui, l'accessibilité est garantie par :
-	Formatage : L'utilisation de Power BI assure l'accessibilité numérique pour l'équipe Terrain. Les rapports sont optimisés pour la consultation mobile.
-	Simplicité : Nous évitons le jargon technique (ETL, DAX) avec la Direction. Nous ne présentons que les résultats finaux (Coût, Bénéfice, Pourcentage) avec des titres clairs (ex: Urgence : Rupture de Stock).
-	Couleur et Texte : Utilisation d'un contraste élevé et d'annotations claires sur les graphiques pour guider l'œil vers le message clé (Takeaway), même pour un public pressé.


## Phase ACT (TBC)
### 1. 
### 2. 
### 3. 
### 4. 
### 5. 






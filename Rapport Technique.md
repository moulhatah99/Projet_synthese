# **Rapport Technique : Segmentation des clients en ligne pour améliorer les campagnes marketing**

## **1\. Introduction**

Dans le cadre de l'analyse des comportements d'achat des clients en ligne, ce projet vise à identifier des segments distincts de clients à l'aide de méthodes d'apprentissage non supervisé. L'objectif est de mieux comprendre les comportements d'achat et la fidélité des clients, ainsi que d'explorer des patterns régionaux, afin d'optimiser les campagnes marketing et d'adapter les stratégies de l'entreprise en fonction des besoins des différents groupes de clients.

### **Objectifs**

* Identifier des groupes distincts de clients à partir de leurs caractéristiques comportementales et démographiques.  
* Analyser la fidélité et les comportements d'achat des clients.  
* Explorer des patterns régionaux et segmenter les clients en fonction de leur région géographique.  
* Fournir des recommandations pour optimiser les campagnes marketing basées sur les segments identifiés.

## **2\. Méthodologie**

### **2.1. Préparation des données**

Le dataset utilisé dans ce projet provient des transactions des clients d'une plateforme de commerce en ligne.

https://www.kaggle.com/datasets/laleeth/customer-transactions-and-demographics?utm_source=chatgpt.com

Le jeu de données comprend diverses informations sur les clients telles que l'âge, le montant des achats, les évaluations de produits, le statut de fidélité, ainsi que des informations sur la localisation géographique et le mode de livraison.

Les étapes de préparation des données sont les suivantes :

1. **Chargement et exploration des données** : Le fichier CSV a été chargé dans un DataFrame Pandas pour l'exploration initiale.  
2. **Nettoyage des données** : Les valeurs manquantes ont été traitées par imputation avec la moyenne ou la modalité, et les colonnes catégorielles ont été converties en variables numériques par encodage (ex : `loyalty_status`, `payment_status`).  
3. **Standardisation des données** : Les variables numériques ont été standardisées à l'aide de `StandardScaler` pour garantir que toutes les caractéristiques aient une échelle similaire et ainsi améliorer la performance des algorithmes de clustering.

### **2.2. Sélection des variables pour le clustering**

Les variables utilisées pour l’analyse des clusters ont été sélectionnées en fonction de leur pertinence pour comprendre la fidélité et les comportements d'achat des clients. Les variables incluent :

* **purchase\_amount** : Montant des achats  
* **customer\_age** : Âge du client  
* **product\_rating** : Évaluation des produits par les clients  
* **loyalty\_status** : Statut de fidélité  
* **product\_category** : Catégorie de produit achetée  
* **shipping\_region** : Région géographique de livraison

### **2.3. Application du clustering (K-Means)**

L'algorithme de clustering K-Means a été choisi pour segmenter les clients en groupes distincts. Après avoir sélectionné un nombre de clusters (`n_clusters=4`), le modèle a été entraîné sur les données standardisées. Les étapes suivantes ont été effectuées :

1. **Initialisation du modèle K-Means** : L'algorithme a été initialisé avec un nombre de clusters égal à 4\.  
2. **Entraînement du modèle** : Le modèle a été entraîné sur les données standardisées pour prédire les groupes (clusters) auxquels chaque client appartient.  
3. **Analyse des centres des clusters** : Les centres des clusters ont été calculés pour comprendre les caractéristiques moyennes des clients dans chaque groupe.  
4. **Visualisation des résultats** : Des visualisations ont été créées pour afficher la segmentation des clients en fonction de variables clés telles que l'âge et le montant des achats.

### **2.4. Analyse des résultats**

Après l’application de K-Means, les clusters ont été analysés pour identifier les tendances et les caractéristiques distinctives de chaque groupe de clients.

#### **Visualisation avec un scatterplot**

La segmentation a été visualisée avec un graphique `scatterplot` utilisant `purchase_amount` et `customer_age`, où les différents clusters sont représentés par des couleurs distinctes.

#### **Réduction de la dimensionnalité (PCA)**

Afin d’améliorer la visualisation des clusters, une réduction de la dimensionnalité a été effectuée à l’aide de **PCA (Principal Component Analysis)**, permettant de réduire le nombre de dimensions à 2 et de visualiser les clusters dans un graphique en deux dimensions.

## **3\. Résultats**

### **3.1. Caractéristiques des clusters**

Les centres des clusters montrent des différences marquées dans les comportements des clients. Voici un aperçu des caractéristiques des clusters identifiés :

* **Cluster 1** : Clients jeunes avec de faibles achats. Ces clients sont probablement plus intéressés par des produits à faible coût par manque de moyens (encore étudiants).  
* **Cluster 2** : Clients plus âgés, avec des achats fréquents. Ils montrent une fidélité plus forte et sont plus enclins à effectuer des achats réguliers.  
* **Cluster 3** : Clients ayant un faible engagement, effectuant peu d'achats. Ils sont probablement à cibler pour des offres personnalisées visant à augmenter leur fidélité.  
* **Cluster 4** : Clients avec un fort pouvoir d'achat et un comportement d'achat régulier. Ces clients devraient être traités comme des clients VIP, avec des offres premium.

### **3.2. Visualisation des clusters**

Les graphiques PCA et scatterplots montrent bien la séparation des clusters sur les axes `customer_age` et `purchase_amount`. Les clients dans chaque cluster présentent des tendances distinctes, facilitant la prise de décision pour les campagnes marketing.

## **4\. Recommandations basées sur les clusters**

En fonction des caractéristiques des différents clusters, voici quelques recommandations pour optimiser les campagnes marketing et améliorer la fidélité des clients :

1. **Cibler les clients jeunes (Cluster 1\)** :  
   * Proposer des produits à prix abordables pour attirer les jeunes clients.  
   * Offrir des réductions ou des promotions pour encourager un plus grand nombre d’achats.  
2. **Fidéliser les clients plus âgés et fréquents (Cluster 2\)** :  
   * Offrir des programmes de fidélité pour récompenser leurs achats réguliers.  
   * Proposer des produits premium ou des services personnalisés.  
3. **Réactiver les clients avec un faible engagement (Cluster 3\)** :  
   * Lancer des campagnes de réengagement avec des offres spéciales pour inciter à un premier achat.  
   * Offrir des essais gratuits ou des remises pour encourager l’engagement.  
4. **Mettre en place des offres VIP pour les clients à fort pouvoir d'achat (Cluster 4\)** :  
   * Créer des programmes VIP exclusifs pour ces clients, avec des offres personnalisées.  
   * Proposer des ventes privées ou des invitations à des événements exclusifs pour renforcer leur fidélité.  
5. **Optimiser la logistique en fonction des régions (Shipping Region)** :  
   * Adapter les offres selon les régions pour mieux répondre aux attentes locales.  
   * Prioriser la livraison rapide dans les régions où la demande est plus forte.

## **5\. Conclusion**

Ce projet a permis de segmenter efficacement les clients en ligne à l'aide du K-Means et de fournir des recommandations pratiques pour améliorer les campagnes marketing. La segmentation offre une vue claire des différents types de clients, permettant ainsi d’adapter les stratégies de marketing aux besoins spécifiques de chaque groupe.

Les prochaines étapes incluent la mise en œuvre de ces recommandations et l’analyse continue des comportements des clients pour ajuster les stratégies marketing à l'évolution des tendances.

---

Ce rapport fournit une vue d'ensemble de ta méthodologie et de l'analyse réalisée. Il est bien sûr possible d'approfondir chaque section en fonction des résultats précis et des analyses supplémentaires que tu pourrais vouloir effectuer (par exemple, tester différents modèles de clustering ou explorer plus de variables).


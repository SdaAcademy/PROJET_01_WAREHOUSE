# PROJET 01 — SDA DATA WAREHOUSE
## Mission professionnelle : piloter la performance de l'entreprise

**Rôle :** Data Analyst Junior, équipe Data & BI de SDA Retail  
**Environnement :** PostgreSQL / Supabase — schéma `warehouse`  
**Outils :** DBeaver ou pgAdmin 4, SQL, Excel/Power BI au choix  
**Accès :** utiliser exclusivement les identifiants personnels communiqués par le formateur.

## 1. Mise en situation

La Direction Générale souhaite une lecture consolidée de l'activité. Les équipes Commerciale, Finance, RH, Marketing et Logistique produisent des indicateurs différents et parfois contradictoires. Vous rejoignez l'équipe Data pour fiabiliser les chiffres, analyser les tendances et préparer une revue de performance.

Vous ne devez pas créer une nouvelle base ni charger de données. Les données sont déjà disponibles dans le schéma `warehouse`. Votre travail consiste à comprendre le modèle, vérifier la qualité utile à l'analyse, répondre aux questions métier et communiquer les résultats.

## 2. Règles de travail

- Connectez-vous à PostgreSQL avec votre compte personnel.
- Travaillez dans le schéma `warehouse` et en lecture seule.
- N'exécutez aucune commande `INSERT`, `UPDATE`, `DELETE`, `DROP`, `TRUNCATE`, `CREATE` ou `ALTER`.
- Avant de calculer un KPI, écrivez sa définition métier et son grain.
- Chaque chiffre du rapport doit pouvoir être reproduit par une requête SQL.
- Distinguez les faits observés, les hypothèses et les recommandations.
- Ne publiez jamais de mot de passe ou de chaîne de connexion dans GitHub.

## 3. Démarrage obligatoire : explorer le modèle

1. Exécutez `sql/00_discovery.sql`.
2. Complétez `livrables/01_dictionnaire_donnees.md` avec les tables réellement présentes, leurs colonnes, leur rôle et leur grain.
3. Identifiez les tables de dimensions (`dim_*`) et de faits (`fact_*`).
4. Pour chaque table de faits, identifiez les clés, les mesures et les dimensions d'analyse.
5. Notez les limites du modèle : colonnes absentes, dates, doublons possibles, valeurs nulles ou conventions non documentées.

## 4. Missions

### Mission 01 — Cartographie et contrôle des données
**Contexte :** avant toute analyse, le responsable BI demande une fiche de compréhension du data warehouse.

À réaliser :
- recenser les tables du schéma `warehouse` ;
- compter les lignes de chaque table utile ;
- examiner les colonnes et les types ;
- mesurer les valeurs nulles sur les champs essentiels ;
- contrôler les clés candidates et les relations possibles ;
- documenter au moins 5 risques ou limites d'interprétation.

**Livrable :** dictionnaire de données + rapport de contrôle initial.

### Mission 02 — Performance commerciale
**Destinataire :** Direction commerciale.

Répondez avec des preuves SQL :
- quelle est l'évolution du chiffre d'affaires dans le temps ?
- quels produits contribuent le plus au chiffre d'affaires et au volume ?
- quels magasins ou zones contribuent le plus à la performance ?
- existe-t-il un écart entre classement en volume et classement en chiffre d'affaires ?
- quelle est la tendance mensuelle/trimestrielle et quelles périodes nécessitent une investigation ?

**À produire :** requêtes SQL commentées, tableau de KPI et 3 à 5 insights.

### Mission 03 — Clients et comportement d'achat
**Destinataire :** Responsable CRM.

- identifiez les clients les plus actifs ou à plus forte contribution, selon les champs réellement disponibles ;
- comparez les segments clients si une dimension de segment existe ;
- étudiez la concentration du chiffre d'affaires ;
- proposez une segmentation opérationnelle, sans prétendre prédire un comportement non observé ;
- formulez des actions CRM justifiées par les données.

**À produire :** analyse client, limites méthodologiques et recommandations.

### Mission 04 — Finance et paiements
**Destinataire :** Responsable financier.

- mesurez les montants de paiements selon les statuts et périodes disponibles ;
- recherchez les écarts possibles entre ventes et paiements, uniquement si les grains et clés permettent une comparaison valide ;
- signalez les paiements manquants, statuts inhabituels ou incohérences possibles ;
- distinguez le chiffre d'affaires commercial du montant effectivement encaissé.

**À produire :** note de contrôle financier et liste des contrôles complémentaires.

### Mission 05 — Marketing et efficacité des campagnes
**Destinataire :** Responsable marketing.

- comparez les campagnes selon les mesures réellement disponibles ;
- calculez les taux uniquement si numérateur et dénominateur sont clairement définis ;
- calculez le coût par résultat ou le ROAS seulement si les données de coût et de résultat sont compatibles ;
- identifiez les campagnes à approfondir et les limites de l'attribution.

**À produire :** tableau comparatif des campagnes et recommandations.

### Mission 06 — RH et opérations
**Destinataires :** responsables RH et Logistique.

Selon les tables disponibles :
- analysez les effectifs, la présence ou les salaires ;
- analysez les niveaux de stock, expéditions ou fournisseurs ;
- repérez les anomalies ou points d'attention ;
- évitez les classements individuels sensibles dans un rapport largement partagé.

**À produire :** un mini-diagnostic RH ou Logistique, avec KPI, contrôles et actions proposées.

### Mission 07 — Comité de Direction
Construisez une synthèse transverse qui répond à :
- quelles sont les 5 informations les plus importantes ?
- quels résultats sont solides et quels résultats nécessitent validation ?
- quelles sont les 3 décisions prioritaires proposées ?
- quelles données ou règles métier faut-il améliorer ?

**Livrables finaux :**
1. dictionnaire de données ;
2. dossier SQL organisé et commenté ;
3. rapport Data Quality ;
4. fichier d'analyse (Excel ou notebook, facultatif selon les outils disponibles) ;
5. dashboard Power BI ou Excel ;
6. Executive Summary d'une page ;
7. présentation de 5 à 8 diapositives.

## 5. Structure attendue des livrables

```text
livrables/
  01_dictionnaire_donnees.md
  02_rapport_data_quality.md
  03_kpi_et_definitions.md
  04_executive_summary.md
  05_recommandations.md
sql/
  00_discovery.sql
  01_data_quality.sql
  02_commercial_performance.sql
  03_customer_analysis.sql
  04_finance_payments.sql
  05_marketing_campaigns.sql
  06_hr_logistics.sql
```

## 6. Critères d'évaluation — 100 points

| Critère | Points |
|---|---:|
| Compréhension du modèle et dictionnaire | 15 |
| Contrôles Data Quality | 15 |
| SQL correct, lisible et reproductible | 25 |
| Définitions et exactitude des KPI | 15 |
| Insights et raisonnement métier | 15 |
| Visualisation, synthèse et communication | 10 |
| Git, organisation et sécurité | 5 |

## 7. Définition du travail professionnel

Un résultat n'est pas seulement un chiffre. Pour chaque KPI, documentez : nom, définition, formule, grain, filtres, période, table(s) source(s), limites et décision que ce KPI peut éclairer.

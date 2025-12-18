---
title: "Le paradoxe de Simpson : comprendre un piège statistique contre-intuitif"
date: 2025-12-01
draft: false
description: "Comprendre le paradoxe de Simpson à l’aide d’un exemple médical simple"
tags: ["data", "statistiques", "paradoxe", "analyse"]
categories: ["Blog"]
---
<img src="feature.png" alt="Segmentation clients par clustering" style="width: 70%; height: auto; display: block; margin: 0 auto 2rem auto;">


Le paradoxe de Simpson est l’un des phénomènes les plus déroutants des statistiques. Il survient lorsqu’une tendance observée dans plusieurs groupes distincts **s’inverse complètement** lorsque ces groupes sont combinés. <!--more-->Autrement dit, **ce qui semble vrai dans chaque sous-groupe peut devenir faux lorsqu’on analyse les données globalement**.

Ce phénomène a des implications majeures en médecine, en économie, en marketing ou en sciences sociales. Le comprendre est essentiel pour éviter des conclusions erronées dans l’analyse de données hétérogènes.

---

# 1. Un exemple médical simple

Imaginons un essai clinique portant sur **160 patients** (80 femmes et 80 hommes). Ces patients reçoivent soit un **médicament**, soit un **placebo**. L’efficacité du traitement est mesurée par le taux de guérison.

<!-- Cependant, la répartition des traitements n’est pas la même chez les hommes et chez les femmes, ce qui va provoquer l’effet paradoxal. -->

## Résultats chez les femmes

| Femmes     | Guéries | Non guéries | Total | Taux de guérison |
|------------|--------:|------------:|------:|-----------------:|
| Médicament | 4       | 16          | 20    | 20 %             |
| Placebo    | 18      | 42          | 60    | 30 %             |

👉 **Chez les femmes, le placebo obtient un meilleur résultat (30 % vs 20 %).**

## Résultats chez les hommes

| Hommes     | Guéris | Non guéris | Total | Taux de guérison |
|------------|-------:|-----------:|------:|-----------------:|
| Médicament | 36     | 24         | 60    | 60 %             |
| Placebo    | 14     | 6          | 20    | 70 %             |

👉 **Chez les hommes également, le placebo est supérieur (70 % vs 60 %).**

En analysant distinctement les deux groupes, la conclusion paraît claire : **le placebo fonctionne mieux**.

## Résultats globaux

| Ensemble    | Guéris | Non guéris | Total | Taux de guérison |
|-------------|-------:|-----------:|------:|-----------------:|
| Médicament  | 40     | 40         | 80    | 50 %             |
| Placebo     | 32     | 48         | 80    | 40 %             |

👉 **Mais lorsque l’on combine les deux groupes, le médicament devient plus efficace (50 % vs 40 %).**

**Comment un traitement peut-il être moins performant dans chaque groupe, mais meilleur au total ?**  
C’est exactement ce que met en lumière **le paradoxe de Simpson.**

---

# 2. Pourquoi la conclusion s’inverse ?

L’inversion provient d’une **variable confondante** : ici, le **sexe** des patients.

Dans notre étude :

Le médicament a été donné principalement aux **hommes** (qui guérissent naturellement mieux : 60-70%), tandis que le placebo a été donné principalement aux **femmes** (qui guérissent naturellement moins bien : 20-30%).

Ainsi, le médicament bénéficie d’une répartition favorable, ce qui **améliore artificiellement ses performances globales**.

Ce biais de composition illustre parfaitement le mécanisme du paradoxe de Simpson :  
> Une tendance peut s’inverser lorsque les proportions de chaque groupe sont différentes.

---

# 3. Des situations réelles où le paradoxe apparaît

Le paradoxe de Simpson n’est pas qu’un exercice théorique. Il apparaît régulièrement dans des analyses de données réelles.

### Médecine
Un traitement peut sembler plus ou moins efficace selon l’âge, le sexe ou le stade de la maladie. Sans stratification adéquate, les conclusions peuvent devenir trompeuses.

### Analyse marketing
Un taux de conversion global plus faible peut masquer de meilleurs résultats sur chaque canal (mobile, desktop, campagnes spécifiques).

### Ressources humaines
Un service peut avoir de bons résultats globaux tout en affichant de moins bons taux dans chaque équipe prise séparément.

### Affaire Berkeley (1973)
L’université semblait discriminer les femmes à l’admission. En réalité, celles-ci postulaient davantage à des départements très sélectifs. Département par département, elles étaient légèrement favorisées.

---

# 4. Comment éviter ce piège analytique ?

Pour se prémunir des conclusions erronées, plusieurs bonnes pratiques sont essentielles :

## 1. Rechercher les variables confondantes
Identifier les facteurs susceptibles d’influencer à la fois la **cause** et l’**effet**.

## 2. Analyser les données par sous-groupes
Les statistiques globales ne sont souvent qu’un **résumé**, parfois trompeur.

## 3. Utiliser les bons outils statistiques
Régressions multivariées, modèles ajustés ou randomisation permettent d’éviter le piège.

## 4. Vérifier la cohérence des groupes comparés
Se demander systématiquement :
- Les groupes sont-ils comparables ?
- Une variable non prise en compte peut-elle renverser l’interprétation ?

---

# 5. Mais alors, quelle analyse faut-il privilégier ?

Dans notre exemple, la réponse dépend de la question.

### Pour mesurer l’efficacité intrinsèque d’un traitement :
➡️ Analyser chaque groupe séparément.  
Ici, **le placebo est plus efficace dans chaque sous-groupe**.

### Pour prédire le résultat dans une population à composition similaire :
➡️ Regarder les données globales.  
Ici, **le médicament donne de meilleurs résultats au total**.

Dans un essai clinique, l’objectif est généralement de mesurer l’efficacité réelle d’un traitement. Il est donc crucial de contrôler ou d’équilibrer les variables confondantes.

---

# Conclusion

Le paradoxe de Simpson rappelle que **les données agrégées peuvent masquer ou inverser des tendances réelles**. Une analyse pertinente nécessite de comprendre le contexte, d’identifier les variables structurantes et de choisir le bon niveau d’interprétation.

### Points clés à retenir

- Les moyennes globales peuvent être trompeuses.  
- Les données doivent être analysées à la bonne échelle.  
- Les variables confondantes doivent être identifiées et contrôlées.  
- Une conclusion n’a de sens que dans **son contexte analytique**.

Avant de tirer une conclusion à partir de chiffres globaux, posez-vous toujours la question :  
> **“Existe-t-il une variable cachée qui pourrait expliquer cette tendance ?”**

Cette précaution simple peut éviter de nombreuses erreurs d’interprétation — même chez les analystes expérimentés.

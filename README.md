# Modélisation de la charge agrégée de sinistres

Évaluer le coût total aléatoire d’un portefeuille d’assurance en comparant trois méthodes indépendantes : simulation Monte-Carlo, récursion de Panjer et convolution théorique.

## Objectif

Ce projet répond à une question centrale en actuariat : **comment estimer de manière fiable la charge totale des sinistres lorsque leur fréquence et leur coût sont tous deux incertains ?**

Le portefeuille est modélisé par un modèle collectif Poisson–Exponentielle :

- nombre de sinistres : `N ~ Poisson(10)` ;
- coût individuel : `Xi ~ Exponentielle(1/100)` ;
- coût moyen d’un sinistre : 100 ;
- 10 000 simulations Monte-Carlo.

## Approche

Trois méthodes complémentaires sont mises en œuvre :

1. **Simulation Monte-Carlo**  
   Génération du nombre de sinistres, simulation des coûts individuels puis calcul de la charge totale.

2. **Récursion de Panjer**  
   Calcul numérique efficace de la distribution agrégée après discrétisation de la loi de coût.

3. **Convolution théorique Poisson–Gamma**  
   Utilisation de la loi conditionnelle de la somme des coûts pour disposer d’une référence analytique.

Les résultats sont ensuite comparés graphiquement et numériquement afin de contrôler les erreurs de simulation, de discrétisation et de troncature.

## Résultats clés

| Indicateur | Simulation | Théorie / Panjer |
|---|---:|---:|
| Espérance | 995,76 | 1 000,00 |
| Quantile à 5 % | 360,30 | 362,40 |
| VaR à 95 % | 1 788,22 | 1 818,80 |

L’écart sur l’espérance reste inférieur à 0,5 %. Les trois distributions se superposent presque entièrement, ce qui confirme la cohérence du modèle.

## Technologies

`R` · simulation Monte-Carlo · récursion de Panjer · lois composées · quantiles · Value at Risk · visualisation

## Ce que ce projet démontre

- traduction d’un problème métier en modèle probabiliste ;
- programmation de méthodes numériques ;
- comparaison de plusieurs approches plutôt que dépendance à un seul résultat ;
- interprétation d’indicateurs utiles au provisionnement et au capital économique ;
- communication claire d’un raisonnement actuariel.

## Limites et améliorations

Les données sont synthétiques et la loi exponentielle reste simplificatrice. Une suite naturelle serait de calibrer le modèle sur des données réelles, tester des distributions à queues plus lourdes et calculer une Expected Shortfall.

## Auteurs

Projet académique réalisé par **Benjamin BAILLET** et **Yannick DJEIGO**.

---


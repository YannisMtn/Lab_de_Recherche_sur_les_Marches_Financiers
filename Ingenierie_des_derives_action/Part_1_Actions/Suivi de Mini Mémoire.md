# Suivi de Mini-Mémoire :

> **Sujet :** Ingénierie des dérivés actions : De la théorie Mathématique à l'implémentation de stratégies de couverture.

---


## État d'Avancement Général
- [ ] **Partie 1 : Recherche sur les actions et le sous-jacent (Genèse du prix )** ![Progress](https://img.shields.io/badge/Status-En_Cours-orange)
- [ ] **Partie 2 : Mécanique et utilisation des options Modélisation Stochastique & Limites Empiriques** ![Progress](https://img.shields.io/badge/Status-En_Attente-lightgrey)
- [ ] **Partie 3 : Ingénierie Financière & Stratégies de Couverture** ![Progress](https://img.shields.io/badge/Status-En_Attente-lightgrey)

---

## Road-map Détaillée & Journal de Bord

### Étape 1 : De l'Information Financière à l'Évaluation 
*Objectif : Transformer les flux réels en valeur théorique (DCF, Gordon-Shapiro).*

#### Phase 1 : Mécanismes Fondamentaux (Matière Première)
- [x] **Chapitre 2 : Les flux de trésorerie** (Free Cash Flows)
- [x] **Chapitre 3 : Les résultats** (EBITDA/EBIT vs Trésorerie)
- [ ] **Chapitre 4 : Actif économique & Ressources** ![Current](https://img.shields.io/badge/FOCUS-ACTUEL-blue)
    * *Note : Travail sur l'équation fondamentale : Actif Éco = Capitaux Propres + Dette Nette.*
- [ ] **Chapitre 5 : Tableau de flux** (Pont résultat/endettement)

#### Phase 2 : Diagnostic Financier & Projections
- [ ] Analyse des marges et effet ciseau (Chap. 10-11)
- [ ] Dynamique du BFR et Capex (Chap. 12)
- [ ] Rentabilité économique vs Rentabilité des capitaux propres (Chap. 14)

#### Phase 3 : Modèles de Valorisation
- [ ] Calcul du CMPC / WACC (Chap. 28-33)
- [ ] Modèle de Gordon-Shapiro & Multiples (PER, EV/EBITDA)

---

### Étape 2 : Du Prix Théorique au Prix de Marché
*Objectif : Expliquer l'écart entre valeur intrinsèque et prix boursier.*
- [ ] **Efficience des marchés** (Random Walk)
- [ ] **Microstructure** (Carnets d'ordres, Bid-Ask spread via O'Hara)
- [ ] **Finance Comportementale** (Biais cognitifs et bulles spéculatives)

---

### Étape 3 : La Transition Mathématique (Stochastique)
*Objectif : Modéliser l'incertitude par le mouvement brownien.*
- [ ] **Mouvement Brownien Géométrique (GBM)**
    * Équation : $$dS_t = \mu S_t dt + \sigma S_t dW_t$$
- [ ] **Calcul d'Itô** (Règles de dérivation stochastique)
- [ ] **Loi Log-normale** (Justification de la non-négativité des prix)

---

### Étape 4 : Critique Empirique & Modèles Avancés
*Objectif : Confrontation du modèle aux réalités du marché (Krachs, Volatilité).*
- [ ] **Analyse des queues épaisses** (Leptokurticité & Skewness)
- [ ] **Clusters de volatilité** (Introduction aux modèles ARCH/GARCH)
- [ ] **Sauts et Volatilité Stochastique** (Modèle de Heston)

---

### Étape 5 : Conclusion & Besoin de Couverture
*Objectif : Justifier l'usage des dérivés.*
- [ ] **Stratégies Delta-Neutres** (Réplication et annulation du risque)
- [ ] **Grecques** (Delta, Gamma, Vega) comme outils de pilotage de la volatilité.

---

## Bibliographie Sélective
| Ouvrage | Auteurs | Concepts Clés |
| :--- | :--- | :--- |
| *Finance d'entreprise* | Vernimmen et al. | Analyse fondamentale, DCF, Structure du capital |
| *Valuation* | McKinsey & Co. | Valeur intrinsèque, ROIC, Croissance |
| *Capital Market Finance* | P. Poncet & R. Portait | Gordon-Shapiro, GBM, Itô, Black-Scholes |
| *Market Microstructure Theory* | Maureen O'Hara | Formation des prix, Liquidité |

---


*Ce sont des anticipations d'avancement dans le but de construire la justification théorique et empirique du fait qu'une action est un actif risqué dont le prix est stochastique, ce qui rend par la suite les options essentielles*

*Dernière mise à jour : 17 avril 2026*

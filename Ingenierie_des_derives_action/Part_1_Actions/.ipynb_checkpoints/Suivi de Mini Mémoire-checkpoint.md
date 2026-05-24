# Suivi de Mini-Mémoire :

> **Sujet :** Ingénierie des dérivés actions : De la théorie mathématique à l'implémentation de stratégies de couverture.

---

## État d'Avancement Général

- [ ] **Partie 1 : Recherche sur les actions et le sous-jacent (Genèse du prix)** ![Progress](https://img.shields.io/badge/Status-En_Cours-orange)
- [ ] **Partie 2 : Mécanique et utilisation des options — Modélisation stochastique & limites empiriques** ![Progress](https://img.shields.io/badge/Status-En_Attente-lightgrey)
- [ ] **Partie 3 : Ingénierie financière & stratégies de couverture** ![Progress](https://img.shields.io/badge/Status-En_Attente-lightgrey)

---

## Note de méthode (lecture du journal)

Le travail a en réalité été mené dans un premier temps sur les premiers chapitres du vernimmen pour comprendre les termes employés et partagés dans les états financiers, puis je procède par la méthode **top-down** : départ du **DCF et de la méthode des multiples**, puis désassemblage de chaque paramètre en remontant à sa source dans le Vernimmen.

L'organisation retenue est **hybride** : entrée par le DCF (la formule cible), puis, pour chaque paramètre de la formule, le bloc de chapitres qui le fonde.

La rédaction de la Partie 1 suit **deux passes** :

1. **Passe A — Récit économique (sans appareil mathématique).** Ébauche linéaire : l'entreprise → les états financiers et l'information qu'ils transmettent → la valorisation (DCF, multiples) → la valeur intrinsèque de l'action.
2. **Passe B — Approfondissement mathématique.** Reprise de chaque brique pour exposer sa nature (ensemble d'appartenance, discret/continu, suite/série/produit vectoriel) et sa source primaire.

---

## Road-map Détaillée & Journal de Bord

### Étape 1 : De l'Information Financière à l'Évaluation
*Objectif : transformer les flux réels en valeur théorique, puis isoler la valeur intrinsèque de l'action.*

---

#### Point d'entrée — États financiers.

- [x] **Chapitre 2 : Les flux de trésorerie** (cycles d'exploitation/investissement ; ressources financières)
- [x] **Chapitre 3 : Les résultats** (§1 génération de richesse ; §2 présentations du compte de résultat — EBITDA/EBIT vs trésorerie)
- [x] **Chapitre 4 : L'actif économique et les ressources** (§2 lecture économique du bilan)
    * *Équation fondamentale : Actif économique = Capitaux propres + Dette nette.*
- [x] **Chapitre 5 : Du résultat à la variation de l'endettement net** (§2-3 tableau de flux de trésorerie)
- [x] **Flux à retenir pour la valorisation** (**Ch. 30 §3** « Les flux de trésorerie à retenir » — définition précise des FCF projetés du DCF)
    * *Nature : suite (FCF_t)_{t=1..n} ∈ ℝⁿ, déterministe en espérance.*


---

#### Bloc A — La valeur

Le DCF est l'objet de départ. 

**Capitaux propres = Valeur de l'actif éco − Dette nette**, et **Valeur intrinsèque par action = Capitaux propres / nombre d'actions**.

- [x] **DCF** comme point de départ (Vernimmen **Ch. 33 §2** « L'évaluation par actualisation des flux » ; McKinsey, *Valuation*)
- [x] **Multiples** comme second ancrage (Vernimmen **Ch. 33 §3** & **Ch. 24 §2** « Les multiples » ; PER, EV/EBITDA)
- [x] **Encadrement DCF ∩ multiples** (Vernimmen **Ch. 33 §5** « Comparaison des valorisations », **§6** primes et décotes) → réduction du risque de modèle
    * *Nature mathématique de la formule : somme finie actualisée (produit scalaire ⟨FCF, facteurs d'actualisation⟩) + terme de valeur terminale (série géométrique).*

---

#### Bloc B — Socle mathématique de l'actualisation (le « (1+CMPC)⁻ᵗ »)
- [ ] **Capitalisation, actualisation, VAN** (**Ch. 17** « Valeur et taux d'intérêt » : §1 capitalisation, §2 actualisation, §3 VAN, §4 déterminants)
    * *C'est ici qu'on prouve la structure de **suite/série actualisée** : support temporel discret t ∈ {1,…,n}, facteurs (1+k)⁻ᵗ.*
- [ ] **Mathématiques financières & taux actuariel** (**Ch. 18**, notamment §5 « Un peu plus de mathématiques financières »)
    * *Convergence de la série géométrique, lien forme finie ↔ forme fermée (cas Gordon-Shapiro).*

---



#### Bloc C — Diagnostic & dynamique des flux (marges, BFR, Capex, levier)
*Ce qui fait varier les FCF dans le temps — la « matière première » du numérateur.*
- [x] **Introduction au diagnostic financier** (**Ch. 9**)
- [x] **Analyse des marges** (**Ch. 10** « marges : structure » ; **Ch. 11** « marges : risques » — §1 effet point mort / effet ciseau)
- [x] **BFR & investissements** (**Ch. 12** : §1-3 BFR, **§4 « L'analyse des investissements »** — composante Capex au stade diagnostic)
- [x] **Analyse du financement** (**Ch. 13**)
- [x] **Rentabilité comptable & effet de levier** (**Ch. 14** : §1 rentabilité, **§2 effet de levier**, §3 intérêt et limites — ROCE vs ROE)
- [x] **Conclusion du diagnostic** (**Ch. 15** : §2 création de valeur)

---

#### Bloc D — Le dénominateur : le coût du capital (CMPC) et ses composantes
*Désassemblage du CMPC en remontant la chaîne du risque.*
- [x] **Risque d'un titre & coefficient β** (**Ch. 19** : §3 outils de mesure rentabilité/risque, §4 risque de marché vs spécifique, **§5 Le coefficient β**)
    * *β estimé par **régression linéaire des rendements** ; recoupement avec β = Cov(Rᵢ,R_m)/Var(R_m). Outils : statsmodels (inférence) + numpy.*
- [x] **Risque et portefeuille** (**Ch. 20** : §1 risque d'un portefeuille, diversification — matrice variance-covariance)
- [x] **MEDAF / rentabilité exigée** (**Ch. 21** : §1 MEDAF, §2 droite de marché, **§3 Les limites du MEDAF**, §4 multifacteurs, §5 fractales)
    * *⚠ Signaler les limites du MEDAF (§3) **dès l'usage** : hypothèses reprises et critiquées à l'Étape 4.*
- [x] **Coût du capital / CMPC (WACC)** (**Ch. 31** : §2 calcul du coût du capital, §3 applications)

---

#### Bloc E — Valeur terminale, création de valeur & cohérence d'ensemble
*Les chapitres « sous le 33 » qui prolongent le DCF.*
- [x] **Mesures de création de valeur** (**Ch. 29** : §2 VAN, §3 profit économique/EVA, §4 critères boursiers, §5 critères comptables — ROIC)
- [x] **Choix d'investissement** (**Ch. 30** : §1 VAN/TRI)
- [x] **Mesures mathématiques du risque** (**Ch. 32 §2**)
- [ ] **Valeur de l'actif économique & structure financière** (**Ch. 34 §1** — passage actif éco → capitaux propres)

---

#### Bloc F — De la valeur d'entreprise à la valeur de l'action
- [x] **L'action : notions de base & analyse de la valeur** (**Ch. 24** : §1 notions de base, §4 plan type d'analyse de la valeur, §5 ajustement technique des données par action)
- [x] **Gordon-Shapiro** (formule : Gordon, 1962 ; traitement mathématique : Poncet & Portait ; pratique DDM : Vernimmen Ch. 24)
    * *Série géométrique ∑ D₁(1+g)^{t-1}/(1+k)^t, condition de convergence k > g, forme fermée V = D₁/(k − g) ; sensibilité ∂V/∂g = D₁/(k−g)².*
- [x] **Capitaux propres / nombre d'actions → valeur intrinsèque par action**

---

### Fin de Passe A - Procéder à la rédaction du récit economique  ![Current](https://img.shields.io/badge/FOCUS-ACTUEL-blue)

---

### Procéder aux recherches en profondeur mathématiques sur les éléments retenus dans la rédaction de la Passe A pour l'approfondissement mathématique

---

### Cas pratique (charnière Étape 1 → Étape 2)
*Objectif : matérialiser l'écart valeur intrinsèque / prix de marché par un chiffre.*
- [ ] Sélection d'une entreprise où l'écart est visible et explicable (croissance survalorisée ou value décotée)
- [ ] Implémentation DCF + multiples (Python / Excel) → fourchette de valeur intrinsèque
- [ ] Comparaison à la capitalisation boursière observée → **l'écart obtenu devient l'objet d'étude de l'Étape 2**
- [ ] Graphiques de **sensibilité statique** (V en fonction de g, de CMPC ; heatmap g × CMPC) — exploration via ipywidgets/Excel, livrable = figures statiques

---

### Étape 2 : Du Prix Théorique au Prix de Marché
*Objectif : expliquer l'écart entre valeur intrinsèque et prix boursier.*
- [ ] **Efficience des marchés** (Vernimmen **Ch. 16 §5-6** ; Fama, 1970 — trois formes ; Samuelson, 1965) → fondement du random walk
- [ ] **Asymétrie d'information** (Akerlof, 1970 ; Grossman-Stiglitz, 1980)
- [ ] **Finance comportementale** (Kahneman & Tversky, 1979 ; Shleifer, 2000 — bulles, écart durable prix/valeur)
- [ ] **Microstructure** (O'Hara, 1995 — bid-ask, liquidité)
    * *Mention brève ici (frictions de court terme, source d'écart distincte) ; traitement approfondi reporté en Partie 3 (coûts de transaction & faisabilité du hedging).*

---

### Étape 3 : La Transition Mathématique (Stochastique)
*Objectif : modéliser l'incertitude par le mouvement brownien.*
- [ ] **Maillon de raccord** : random walk discret sur log-rendements → limite continue (Donsker) → mouvement brownien
- [ ] **Du prix au processus** : ce n'est pas « l'action » mais le **prix (Sₜ)ₜ≥₀** qui est un *processus stochastique* (chaque Sₜ est une variable aléatoire)
- [ ] **Mouvement Brownien Géométrique (GBM)** — on modélise le **rendement** dSₜ/Sₜ, non dSₜ :
    $$dS_t = \mu S_t\, dt + \sigma S_t\, dW_t$$
- [ ] **Calcul d'Itô** (lemme d'Itô appliqué à log Sₜ)
- [ ] **Loi log-normale & non-négativité** — ordre : rendement → Itô → log Sₜ gaussien → Sₜ log-normal → positivité
    * *Réserve : μ = drift sous mesure **historique** ; bascule risque-neutre (μ → r) gardée pour la Partie 2.*
    * *Sources : Poncet & Portait (Brownian motion, SDE, Itô).*

---

### Étape 4 : Critique Empirique & Modèles Avancés
*Objectif : confronter le modèle aux réalités du marché. Niveau Partie 1 : introduire le besoin via les faits stylisés, sans calibration exhaustive.*
- [ ] **Queues épaisses** (leptokurtisme & asymétrie ; Mandelbrot, 1963 ; Cont, 2001)
- [ ] **Clusters de volatilité** (ARCH/GARCH ; Engle, 1982 ; Bollerslev, 1986)
- [ ] **Sauts & volatilité stochastique** (Heston, 1993)
- [ ] **Rappel critique du MEDAF** (boucle vers Bloc D / Ch. 21 §3 : variance finie et rationalité contredites)

---

### Étape 5 : Conclusion & Besoin de Couverture
*Objectif : justifier l'usage des dérivés.*
- [ ] **Stratégies delta-neutres** (réplication et annulation du risque)
- [ ] **Grecques** (Delta, Gamma, Vega) comme outils de pilotage de la volatilité
- [ ] **Appui Vernimmen** : Ch. 25 « L'option » (§4 déterminants de la valeur, §5 méthodes d'évaluation, §6 gestion d'une position) ; Ch. 36 §2 « apport de la théorie des options à la valorisation »
- [ ] **Charnière vers Parties 2 & 3**

---

## Bibliographie Sélective

| Ouvrage | Auteurs | Concepts clés | Repères |
| :--- | :--- | :--- | :--- |
| *Finance d'entreprise* (22ᵉ éd., 2024) | Quiry, Le Fur, Vernimmen | Flux, diagnostic, β, MEDAF, CMPC, action, valorisation | voir tableau ci-dessous |
| *Valuation* | McKinsey & Co. | Valeur intrinsèque, ROIC, croissance, DCF | — |
| *Capital Market Finance* | Poncet, Portait, Toder | Gordon-Shapiro, GBM, Itô, Black-Scholes, notation vectorielle/matricielle | — |
| *Market Microstructure Theory* | O'Hara | Formation des prix, liquidité, bid-ask | — |

### Repères de chapitres Vernimmen (vérifiés section par section, éd. 2024)

| Notion (paramètre DCF) | Chapitre & section |
| :--- | :--- |
| Actualisation / VAN | **Ch. 17** §1-4 |
| Maths financières / taux actuariel | **Ch. 18** §5 |
| Flux de trésorerie (FCF) | **Ch. 2** ; **Ch. 3** §2 ; **Ch. 5** §2-3 |
| FCF projetés à retenir | **Ch. 30** §3 |
| Actif éco = CP + Dette nette | **Ch. 4** §2 ; **Ch. 34** §1 |
| Marges / effet ciseau | **Ch. 10** ; **Ch. 11** §1 |
| BFR & Capex (diagnostic) | **Ch. 12** §1-3 ; **§4** investissements |
| Effet de levier (ROCE vs ROE) | **Ch. 14** §2-3 |
| Coefficient β | **Ch. 19** §5 |
| Portefeuille / diversification | **Ch. 20** §1 |
| MEDAF & ses limites | **Ch. 21** §1-2, **§3 limites** |
| CMPC / WACC | **Ch. 31** §2 |
| Création de valeur / EVA / ROIC | **Ch. 29** §3-5 |
| Mesures mathématiques du risque | **Ch. 32** §2 |
| DCF (pratique) | **Ch. 33** §2 |
| Multiples / PER | **Ch. 33** §3 ; **Ch. 24** §2 |
| Comparaison des valorisations (encadrement) | **Ch. 33** §5-6 |
| L'action (valeur, données par action) | **Ch. 24** §1, §4-5 |
| Marchés efficients | **Ch. 16** §5-6 |
| L'option (Grecques, évaluation) | **Ch. 25** §4-6 |

*Sources complémentaires (Étapes 2-4) : Fama (1970), Samuelson (1965), Akerlof (1970), Grossman-Stiglitz (1980), Kahneman & Tversky (1979), Shleifer (2000), Bachelier (1900), Mandelbrot (1963), Cont (2001), Engle (1982), Bollerslev (1986), Heston (1993), Donsker.*

---

*Ce document anticipe l'avancement dans le but de construire la justification théorique et empirique du fait qu'une action est un actif risqué dont le prix est stochastique, ce qui rend par la suite les options essentielles.*

*Dernière mise à jour : 24 mai 2026*

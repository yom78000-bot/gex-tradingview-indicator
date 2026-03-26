# GEX Walls Indicator - TradingView

Indicateur TradingView universel affichant les niveaux de Gamma Exposure (GEX) pour SPY, QQQ, AAPL et autres symboles.

## 🚀 Caractéristiques

- **Multi-symboles** : Détection automatique du symbole du graphique
- **Multi-expirations** : 0DTE (0j), 1st week (~7j), 2nd week (~14j), 1st month (~30j), all
- **Mise à jour automatique** : Calculs GEX toutes les 5 minutes pendant les heures de marché
- **6 niveaux GEX** : Top 3 Call Walls (résistances) + Top 3 Put Walls (supports)
- **Gamma Flip (Zero Gamma)** : Niveau de bascule entre gamma positif et négatif
- **Zone de stabilité** : Visualisation de la zone entre Call Wall #1 et Put Wall #1
- **Paramètres personnalisables** : Couleurs, labels, extension des lignes, choix de l'expiration

## 📊 Symboles supportés

- **SPY** - S&P 500 ETF
- **QQQ** - Nasdaq 100 ETF
- **AAPL** - Apple Inc.
- **AMZN** - Amazon.com Inc.
- **DIA** - Dow Jones Industrial Average ETF
- **IBIT** - iShares Bitcoin Trust ETF

## 🔧 Installation

1. Ouvrir [TradingView.com](https://www.tradingview.com)
2. Ouvrir **Pine Editor** (en bas de l'écran)
3. Copier le contenu de [`gex_walls_indicator.pine`](gex_walls_indicator.pine)
4. Coller dans Pine Editor
5. Cliquer sur **"Add to Chart"**

## 📖 Utilisation

L'indicateur détecte automatiquement le symbole du graphique :
- Sur un graphique **SPY**, affiche les GEX Walls SPY
- Sur un graphique **QQQ**, affiche les GEX Walls QQQ (si disponible)
- Sur un graphique non supporté, affiche un message d'avertissement

### Interprétation

- **Call Walls (rouge)** : Niveaux de résistance créés par le Gamma Exposure positif
  - Prix au-dessus → Pression baissière potentielle
- **Put Walls (vert)** : Niveaux de support créés par le Gamma Exposure négatif
  - Prix en-dessous → Pression haussière potentielle
- **Gamma Flip (orange pointillé)** : Niveau de gamma zéro (Zero Gamma Level)
  - Calculé comme la moyenne entre Call Wall #1 et Put Wall #1
  - Prix au-dessus du Gamma Flip → Dealers sont short gamma (volatilité amplifiée)
  - Prix en-dessous du Gamma Flip → Dealers sont long gamma (volatilité amortie)
  - Point critique où le gamma des market makers passe de positif à négatif
- **Zone de stabilité (gris)** : Zone entre Call Wall #1 et Put Wall #1
  - Prix dans la zone → Marché équilibré

### Paramètres disponibles

**Expiration** :
- **0DTE (0d)** : Expiration du jour même (0 jours)
- **1st week (7d)** : Première expiration hebdomadaire (~7 jours)
- **2nd week (14d)** : Deuxième expiration hebdomadaire (~14 jours)
- **1st month (30d)** : Première expiration mensuelle (~30 jours)
- **all** : Affiche toutes les expirations (défaut : 1st week)

**Affichage** :
- Afficher/masquer Call Walls
- Afficher/masquer Put Walls
- Afficher/masquer Labels
- Extension des lignes (none/right/both)

**Couleurs** :
- Call Wall #1/2/3 (défaut : rouge avec transparence croissante)
- Put Wall #1/2/3 (défaut : vert avec transparence croissante)

## 📅 Mise à jour

Les données GEX sont mises à jour :
- **Fréquence** : Toutes les 5 minutes pendant heures de marché (9h30-16h EST)
- **Source** : Calcul automatique via Yahoo Finance Options Data
- **Dernière mise à jour** : Voir le commentaire en haut du fichier `.pine`

Pour bénéficier des mises à jour, remplacer le code dans Pine Editor par la dernière version de ce repository.

## ⚙️ Fonctionnement technique

1. **Calcul GEX** : Backend Python analyse les données d'options Yahoo Finance
2. **Détection changements** : Webhook Flask compare les snapshots MySQL
3. **Génération PineScript** : Script Python génère le code PineScript universel
4. **Commit GitHub** : Push automatique vers ce repository
5. **Notification Telegram** : Alerte utilisateur des mises à jour

## 📊 Exemple de données (SPY - 2026-03-25)

- **Prix actuel** : $656.78
- **Call Wall #1** : $660.00 (GEX: 19.7M)
- **Call Wall #2** : $666.00 (GEX: 6.5M)
- **Call Wall #3** : $659.00 (GEX: 6.1M)
- **🔶 GAMMA FLIP** : $657.50 (Zero Gamma Level)
- **Put Wall #1** : $655.00 (GEX: -94.2M) ⚠️ Support majeur
- **Put Wall #2** : $650.00 (GEX: -57.9M)
- **Put Wall #3** : $645.00 (GEX: -11.6M)

## 📚 Ressources

- **Documentation Gamma Exposure** : [SpotGamma](https://spotgamma.com/education/)
- **TradingView Pine Script** : [Documentation officielle](https://www.tradingview.com/pine-script-docs/)
- **Métadonnées** : Voir [`metadata.json`](metadata.json) pour les données brutes

## ⚠️ Avertissement

Cet indicateur est fourni à titre éducatif uniquement. Les données GEX sont basées sur des calculs théoriques et peuvent contenir des erreurs. Ne doit pas être utilisé comme unique base de décision d'investissement.

## 📜 Licence

MIT License - Utilisation libre avec attribution

---

**Généré automatiquement** par le système GEX Auto-Update
**Dernière mise à jour** : 2026-03-26 13:45 UTC

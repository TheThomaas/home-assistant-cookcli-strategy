# CookCLI Recipes Strategy pour Home Assistant

Stratégie de tableau de bord Home Assistant qui génère automatiquement **une page par recette** à partir des recettes exposées par l'intégration [ha-cookcli](https://git.thethomaas.net/TheThomaas/ha-cookcli).

Chaque page de recette affiche les **ingrédients** et les **étapes de préparation**, offrant une navigation fluide depuis un tableau de bord dédié à vos recettes de cuisine.

## ✨ Fonctionnalités

- 🗂️ **Génération automatique** d'une page par recette
- 📋 Affichage des **ingrédients** de chaque recette
- 👨‍🍳 Affichage des **étapes** de préparation
- 🧭 Navigation facilitée entre les recettes via la carte [ha-cookcli-card](https://git.thethomaas.net/TheThomaas/ha-cookcli-card)
- 🎨 Intégration native aux tableaux de bord Home Assistant (YAML généré dynamiquement)

## 🧩 Architecture

Cette stratégie fait partie d'un ensemble de trois composants qui fonctionnent ensemble :

| Composant | Rôle | Dépôt |
|---|---|---|
| **Intégration** | Se connecte au serveur CookCLI et expose les recettes à Home Assistant | [ha-cookcli](https://git.thethomaas.net/TheThomaas/ha-cookcli) |
| **Stratégie de tableau de bord** | Crée automatiquement une page par recette (ingrédients + étapes) | *ce dépôt* |
| **Carte personnalisée** | Liste toutes les recettes et permet de naviguer vers le détail d'une recette | [ha-cookcli-card](https://git.thethomaas.net/TheThomaas/ha-cookcli-card) |

## 📦 Installation

### Prérequis

- Une instance **Home Assistant** fonctionnelle (version récente recommandée)
- L'intégration **[ha-cookcli](https://git.thethomaas.net/TheThomaas/ha-cookcli)** installée et configurée
- La carte **[ha-cookcli-card](https://git.thethomaas.net/TheThomaas/ha-cookcli-card)** installée (pour la navigation)
- **[HACS](https://hacs.xyz/)** installé (recommandé)

### Installation via HACS

1. Ouvrez **HACS** dans Home Assistant.
2. Allez dans **Tableaux de bord** → menu (⋮) → **Dépôts personnalisés**.
3. Ajoutez l'URL du dépôt :
   ```
   https://git.thethomaas.net/TheThomaas/ha-cookcli-strategy
   ```
   Catégorie : **Dashboard** (ou **Lovelace**)
4. Recherchez **CookCLI Strategy** dans HACS et installez-le.
5. **Videz le cache du navigateur** ou rechargez les ressources Lovelace.

### Installation manuelle

1. Téléchargez ou clonez ce dépôt.
2. Copiez le fichier `dist/cookcli-recipe-strategy.js` dans votre répertoire `config/www/`.
3. Ajoutez la ressource dans **Paramètres** → **Tableaux de bord** → **Ressources** :
   ```yaml
   url: /local/cookcli-recipe-strategy.js
   type: module
   ```
4. Rechargez les ressources Lovelace.

## ⚙️ Configuration

### Création d'un tableau de bord avec la stratégie

1. Allez dans **Paramètres** → **Tableaux de bord**.
2. Cliquez sur **+ Ajouter un tableau de bord**.
3. Choisissez **Nouveau tableau de bord à partir d'une stratégie** (ou équivalent selon votre version de HA).
4. Sélectionnez la stratégie **CookCLI Recipe**.
5. Validez : le tableau de bord est généré automatiquement avec une page par recette.

### Exemple de configuration YAML

Si vous préférez définir le tableau de bord en YAML :

```yaml
strategy:
  type: custom:cookcli-recipe
  title: Mes recettes
```

> Adaptez les options selon la version de la stratégie. Consultez le fichier `dist/cookcli-recipe-strategy.js` pour la liste exacte des paramètres supportés.

## 🚀 Utilisation

Une fois le tableau de bord créé :

1. La **page d'accueil** du tableau de bord liste les recettes (via la carte `cookcli-card`).
2. Cliquer sur une recette **navigue vers sa page de détail** générée par la stratégie.
3. Chaque page de détail présente :
   - les **ingrédients** nécessaires,
   - les **étapes** de préparation dans l'ordre.

## 📄 Licence

Ce projet est distribué sous licence présente dans le fichier [LICENSE](./LICENSE) du dépôt.

## 🔗 Liens

- **Intégration** : https://git.thethomaas.net/TheThomaas/ha-cookcli
- **Stratégie** : https://git.thethomaas.net/TheThomaas/ha-cookcli-strategy
- **Carte** : https://git.thethomaas.net/TheThomaas/ha-cookcli-card
- **CookCLI** : https://github.com/cooklang/CookCLI
- **Cooklang** : https://cooklang.org/

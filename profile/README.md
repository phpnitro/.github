# PhpNitro

**Un framework PHP pour construire de vraies applications Android natives.**

PhpNitro permet à PHP de décrire l'interface, d'effectuer le layout et de produire les commandes de dessin qui sont rendues sur un véritable `android.graphics.Canvas` via `NativeCanvasView`.

Il ne s'agit pas d'une application web emballée dans une WebView : pas de HTML, pas de CSS et pas de JavaScript nécessaires pour le rendu de l'interface.

## Architecture

- **PHP** porte la logique de l'application, l'arbre de widgets, le layout et les commandes de rendu.
- **`phpnitro/ui`** fournit les widgets, le layout, les animations, les gestes et les API d'appareil exposées au framework.
- **`android-engine`** est le moteur Android natif écrit en Kotlin. Il rejoue les commandes PHP sur un vrai Canvas Android au moyen de `NativeCanvasView`.
- Le moteur Android est une dépendance publiée via **JitPack** et référencée par les projets PhpNitro ; il n'est pas copié dans chaque application.
- Les composants PHP sont distribués séparément avec **Composer**, afin que chaque application ne récupère que les packages dont elle a besoin.

## Démarrer

```bash
composer require phpnitro/ui
phpx new mon-app
cd mon-app && composer install && phpx serve
```

## Packages

Les packages PhpNitro s'installent séparément via Composer.

### Rendu

| Package | Description |
|---|---|
| [`phpnitro/ui`](https://github.com/phpnitro/ui) | Widgets, layout, commandes Canvas, animations, gestes et API d'appareil |
| [`android-engine`](https://github.com/phpnitro/android-engine) | Moteur Kotlin/Android qui rend les commandes sur un vrai `android.graphics.Canvas` |

### Données

| Package | Description |
|---|---|
| [`phpnitro/database`](https://github.com/phpnitro/database) | Connexion Doctrine DBAL et outil de migrations |
| [`phpnitro/preferences`](https://github.com/phpnitro/preferences) | Stockage clé-valeur persistant |
| [`phpnitro/offline`](https://github.com/phpnitro/offline) | File d'attente de mutations hors ligne, rejouées à la reconnexion |
| [`phpnitro/state`](https://github.com/phpnitro/state) | API typée au-dessus de `$_SESSION` pour l'état partagé entre écrans |
| [`phpnitro/countries`](https://github.com/phpnitro/countries) | Jeu de données hors ligne des pays et villes |

### Intégrations

| Package | Description |
|---|---|
| [`phpnitro/firebase`](https://github.com/phpnitro/firebase) | Client REST Firebase Auth et Cloud Functions |
| [`phpnitro/supabase`](https://github.com/phpnitro/supabase) | Client REST PostgREST/GoTrue |
| [`phpnitro/socialauth`](https://github.com/phpnitro/socialauth) | Connexion OAuth2 pour GitHub, Facebook, Microsoft et Apple |
| [`phpnitro/cloudinary`](https://github.com/phpnitro/cloudinary) | Upload, transformation et suppression d'images via REST |
| [`phpnitro/payments`](https://github.com/phpnitro/payments) | Intégrations de moyens de paiement, dont FeexPay |
| [`phpnitro/geocoding`](https://github.com/phpnitro/geocoding) | Géocodage direct et inverse avec OpenStreetMap Nominatim |

### Utilitaires

| Package | Description |
|---|---|
| [`phpnitro/math`](https://github.com/phpnitro/math) | Statistiques, arithmétique décimale exacte et conversions d'unités |
| [`phpnitro/date`](https://github.com/phpnitro/date) | Arithmétique de dates et temps relatif |
| [`phpnitro/format`](https://github.com/phpnitro/format) | Formatage et opérations compatibles avec les grapheme clusters |
| [`phpnitro/validation`](https://github.com/phpnitro/validation) | Validation de données par règles |
| [`phpnitro/uuid`](https://github.com/phpnitro/uuid) | Génération d'UUID v4/v7 |
| [`phpnitro/crypto`](https://github.com/phpnitro/crypto) | Hash, HMAC et jetons aléatoires |
| [`phpnitro/mime`](https://github.com/phpnitro/mime) | Détection de type MIME |
| [`phpnitro/retry`](https://github.com/phpnitro/retry) | Réessai avec backoff exponentiel |
| [`phpnitro/jwt`](https://github.com/phpnitro/jwt) | Décodage de JWT |
| [`phpnitro/i18n`](https://github.com/phpnitro/i18n) | Traduction et gestion des locales |
| [`phpnitro/analytics`](https://github.com/phpnitro/analytics) | Suivi léger des événements |

## Technologies

Le projet combine principalement **PHP**, **Kotlin**, **Swift**, **Rust**, **Python** et **C#** selon les composants et outils concernés. Le cœur de l'expérience applicative reste toutefois le couple **PHP + moteur Android natif Kotlin**.

## État du projet

PhpNitro est en développement actif et reste pré-1.0. L'architecture actuelle repose sur des packages Composer indépendants et un moteur Android natif distribué séparément via JitPack.

Consultez les dépôts de l'organisation pour suivre les composants, les exemples et l'évolution du framework.

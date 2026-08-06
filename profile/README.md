# PhpNitro

**Un framework PHP qui compile vers de vraies apps Android natives.** PHP fait le layout et peint directement sur un vrai `android.graphics.Canvas` — pas de WebView, pas de HTML/CSS/JS dans le rendu. PHP tourne comme le vrai runtime embarqué sur l'appareil, pas juste un langage de templating au moment du build.

## Comment ça marche

- Un arbre de widgets PHP (`Container`, `Flex`, `Text`, `Button`...) fait le layout et produit des commandes de dessin JSON.
- Un moteur de rendu Kotlin ([`android-engine`](https://github.com/phpnitro/android-engine)) les rejoue avec de vraies primitives Canvas Android — aucune WebView impliquée.
- Chaque interaction déclenche un aller-retour HTTP vers le process PHP embarqué sur l'appareil lui-même. Pas de serveur distant requis.

## Démarrer

```bash
composer require phpnitro/ui
phpx new mon-app
cd mon-app && composer install && phpx serve
```

## Packages

Chaque package s'installe séparément via Composer, comme sur pub.dev — rien n'est imposé d'avance.

### Rendu

| Package | Description |
|---|---|
| [`phpnitro/ui`](https://github.com/phpnitro/ui) | Le moteur de rendu natif lui-même — widgets, layout, commandes Canvas, animations, gestes, et les classes d'API device (caméra, capteurs, presse-papiers...) |
| [`android-engine`](https://github.com/phpnitro/android-engine) | Le moteur Kotlin qui rejoue les commandes de dessin sur un vrai `android.graphics.Canvas` |

### Données

| Package | Description |
|---|---|
| [`phpnitro/database`](https://github.com/phpnitro/database) | Connexion Doctrine DBAL + outil de migrations |
| [`phpnitro/preferences`](https://github.com/phpnitro/preferences) | Stockage clé-valeur persistant, appuyé sur `phpnitro/database` |
| [`phpnitro/offline`](https://github.com/phpnitro/offline) | File d'attente de mutations hors-ligne, rejouées à la reconnexion |
| [`phpnitro/state`](https://github.com/phpnitro/state) | API typée au-dessus de `$_SESSION` pour l'état partagé entre écrans |
| [`phpnitro/countries`](https://github.com/phpnitro/countries) | Jeu de données pays/villes hors-ligne |

### Intégrations

| Package | Description |
|---|---|
| [`phpnitro/firebase`](https://github.com/phpnitro/firebase) | Client REST Firebase Auth + Cloud Functions, sans SDK |
| [`phpnitro/supabase`](https://github.com/phpnitro/supabase) | Client REST PostgREST/GoTrue, sans SDK |
| [`phpnitro/socialauth`](https://github.com/phpnitro/socialauth) | Connexion OAuth2 (GitHub, Facebook, Microsoft, Apple) |
| [`phpnitro/cloudinary`](https://github.com/phpnitro/cloudinary) | Upload/transformation/suppression d'images via REST |
| [`phpnitro/payments`](https://github.com/phpnitro/payments) | Intégrations de moyens de paiement (Feexpay) |
| [`phpnitro/geocoding`](https://github.com/phpnitro/geocoding) | Géocodage direct/inverse via OpenStreetMap Nominatim, sans clé API |

### Utilitaires

| Package | Description |
|---|---|
| [`phpnitro/math`](https://github.com/phpnitro/math) | Aides numériques, statistiques, arithmétique décimale exacte, conversions d'unités |
| [`phpnitro/date`](https://github.com/phpnitro/date) | Arithmétique de dates et temps relatif lisible |
| [`phpnitro/format`](https://github.com/phpnitro/format) | Formatage + opérations conscientes des grapheme clusters |
| [`phpnitro/validation`](https://github.com/phpnitro/validation) | Validation de données par règles |
| [`phpnitro/uuid`](https://github.com/phpnitro/uuid) | Génération d'UUID v4/v7 (RFC 4122), sans dépendance |
| [`phpnitro/crypto`](https://github.com/phpnitro/crypto) | Hash, HMAC, jetons aléatoires |
| [`phpnitro/mime`](https://github.com/phpnitro/mime) | Détection de type MIME |
| [`phpnitro/retry`](https://github.com/phpnitro/retry) | Réessai avec backoff exponentiel |
| [`phpnitro/jwt`](https://github.com/phpnitro/jwt) | Décodage de JWT (sans vérification de signature) |
| [`phpnitro/i18n`](https://github.com/phpnitro/i18n) | Traduction/locale, pilotée par la locale système de l'appareil |
| [`phpnitro/analytics`](https://github.com/phpnitro/analytics) | Suivi d'événements léger, appuyé sur `phpnitro/database` |

## État du projet

En développement actif, pré-1.0. L'architecture est stable et testée (suite PHPUnit + tests golden-file pour le pipeline de rendu + CI), mais le framework n'a pas encore été utilisé par des développeurs externes — considère-le comme un travail sérieux et fonctionnel, pas encore comme un produit éprouvé à grande échelle.

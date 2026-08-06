# PhpNitro

**Un framework PHP qui compile vers de vraies apps Android natives.** PHP fait le layout et peint directement sur un vrai `android.graphics.Canvas` — pas de WebView, pas de HTML/CSS/JS dans le rendu. PHP tourne comme le vrai runtime embarqué sur l'appareil, pas juste un langage de templating au moment du build.

## Comment ça marche

- Un arbre de widgets PHP (`Container`, `Flex`, `Text`, `Button`...) fait le layout et produit des commandes de dessin JSON.
- Un moteur de rendu Kotlin (`NativeCanvasView`) les rejoue avec de vraies primitives Canvas Android — aucune WebView impliquée.
- Chaque interaction déclenche un aller-retour HTTP vers le process PHP embarqué sur l'appareil lui-même. Pas de serveur distant requis.

## Packages

Chaque package s'installe séparément via Composer, comme sur pub.dev — rien n'est imposé d'avance :

`phpnitro/ui` · `phpnitro/database` · `phpnitro/firebase` · `phpnitro/countries` · `phpnitro/preferences` · `phpnitro/payments` · `phpnitro/socialauth` · `phpnitro/math` · `phpnitro/date` · `phpnitro/cloudinary` · `phpnitro/i18n` · `phpnitro/state` · `phpnitro/analytics` · `phpnitro/format` · `phpnitro/validation` · `phpnitro/uuid` · `phpnitro/crypto` · `phpnitro/mime` · `phpnitro/retry` · `phpnitro/jwt` · `phpnitro/geocoding` · `phpnitro/supabase` · `phpnitro/offline`

Le moteur natif Android lui-même : [`phpnitro/android-engine`](https://github.com/phpnitro/android-engine).

## Démarrer

```bash
composer require phpnitro/ui
phpx new mon-app
cd mon-app && composer install && phpx serve
```

## État du projet

En développement actif, pré-1.0. L'architecture est stable et testée (suite PHPUnit + tests golden-file pour le pipeline de rendu + CI), mais le framework n'a pas encore été utilisé par des développeurs externes — considère-le comme un travail sérieux et fonctionnel, pas encore comme un produit éprouvé à grande échelle.

# V2.8.0 — Fiabilité et retours plus clairs

- Retours explicites pour les cas hors ligne, réseau inaccessible, délai dépassé et réponse serveur illisible.
- Aucun réenvoi automatique d’un contrôle : l’interface attend la confirmation du serveur.
- Chargements concurrents des lecteurs ZXing et jsQR dédupliqués.
- L’image temporaire de lecture photo est libérée même si l’analyse échoue.
- L’état réseau conserve le contexte du résultat affiché.
- Pendant l’enregistrement, les boutons de résultat sont désactivés ensemble et réactivés en cas d’erreur.
- Les données serveur continuent d’être échappées avant insertion dans le HTML.

## Limites
Le test Playwright n’a pas pu démarrer dans cet environnement : Chromium bloque la navigation locale (ERR_BLOCKED_BY_ADMINISTRATOR). Les essais physiques Android, la torche et les écritures réelles dans la base de test restent à effectuer. Les bibliothèques sont encore chargées à la demande depuis des CDN avec secours.

L’endpoint API, l’authentification et le Worker Cloudflare restent inchangés.

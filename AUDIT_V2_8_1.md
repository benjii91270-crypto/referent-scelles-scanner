# Audit V2.8.1 — Séparation des rôles

## Changement d’interface
- Authentification nominative après autorisation de l’appareil.
- Contrôle physique masqué et refusé côté navigateur pour les sessions non administrateur.
- Mouvement obligatoire par session : le nom doit correspondre à l’utilisateur connecté et le motif est requis ; destination facultative.
- Retour en stock réservé à l’administrateur et protégé par confirmation physique.

## Validation locale
- JavaScript inline syntaxiquement valide.
- Identifiants DOM statiques uniques.
- Assertions de présence des appels de session, de l’argument motif et du test isAdmin réalisées.

## Limite de sécurité critique
Ces contrôles dans le HTML ne sont pas, seuls, une frontière de sécurité. L’Apps Script précédemment inspecté appelait le contrôle via une session non-administrateur (adminRequired=false) et le Worker ne permettait pas encore de faire remonter motif. Le patch serveur séparé met à jour ces points. Il faut le déployer de façon coordonnée sur une copie de test et vérifier que le déploiement réellement utilisé est à jour. La production ne doit pas être considérée sécurisée avant les essais directs API avec un compte enquêteur.

## Non exécuté
- Écriture réelle Google Drive.
- Déploiement Worker Cloudflare réel.
- Test complet sur téléphone Android.
- Test navigateur automatisé : Chromium était bloqué dans l’environnement de création.

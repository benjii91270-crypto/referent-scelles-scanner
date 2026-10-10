# V2.8.1 — Droits nominatives et déplacements

## Règle des rôles
- Administrateur connecté : accès aux quatre résultats de contrôle physique et au retour en stock après confirmation physique.
- Enquêteur connecté : pas de commandes de contrôle physique ; seule action métier disponible sur un scellé en stock : le prendre en charge et le faire passer en mouvement.
- Nom d’enquêteur tiré de la session serveur et non modifiable dans le formulaire.
- Motif de déplacement obligatoire ; destination facultative.
- Le détail du mouvement affiche l’acteur, le motif, la destination et la date.

## Sécurité
L’interface applique les rôles, mais la validation réelle repose sur le patch Apps Script/Worker fourni séparément. Ne pas déployer cette interface seule en production : un ancien backend qui autorise le contrôle à tout compte connecté n’est pas suffisant.

## Périmètre inchangé
Les valeurs de contrôle, l’endpoint API, l’authentification appareil, le moteur QR et le scanner QR sécurisé existant sont conservés. Le Worker/API ne sont pas modifiés par ce fichier HTML seul.

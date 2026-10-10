RÉFÉRENT SCELLÉS — SCANNER QR TERRAIN
Version candidate : V2.8.0
Statut : branche de préproduction à valider, non fusionnée dans main.

INSTALLATION ET PRUDENCE
1. Garder la production actuelle en service tant que la préproduction n’est pas validée.
2. Publier cette branche sur une URL HTTPS de préproduction.
3. Remplacer uniquement index.html pour tester le scanner statique.
4. Ne pas redéployer ou modifier le Worker Cloudflare au titre de cette mise à jour.
5. Tester sur le téléphone terrain avant la fusion.

V2.7 — INTERFACE TERRAIN SIMPLIFIÉE
- Actions principales : Torche, Changer de caméra, Activer/Reprendre la lecture.
- Mode série, zoom, arrêt caméra, son et vibration déplacés dans « Réglages complémentaires ».
- Résumé prioritaire : numéro d’entrée, désignation, procédure et emplacement attendu.
- Catégorie, taille et enquêteur dans un volet repliable.
- Quatre résultats de contrôle conservés et valeurs envoyées à l’API inchangées.

V2.8 — FIABILITÉ
- Messages plus explicites hors ligne, en cas de délai dépassé ou de réponse illisible.
- Aucun renvoi automatique d’un contrôle après une erreur réseau.
- Chargements concurrents de ZXing et jsQR dédupliqués.
- Image temporaire libérée même si l’analyse par photo échoue.
- Boutons de résultat verrouillés durant l’enregistrement, puis réactivés si celui-ci échoue.
- Retour d’état réseau plus clair.

VALIDATION OBLIGATOIRE AVANT FUSION
- Vérifier les caméras avant/arrière et la torche physique.
- Tester QR valide et QR invalide.
- Tester les quatre résultats de contrôle.
- Faire plusieurs scans consécutifs en mode série sans redémarrer le flux vidéo.
- Tester mode classique, pause/reprise, retour en arrière-plan et reprise.
- Tester réseau lent/coupé, scan par photo et confirmation réelle d’écriture en base de test.

LIMITES CONNUES
Les tests Node et simulations ne remplacent pas un essai sur téléphone. Le test Playwright n’a pas pu démarrer dans cet environnement car Chromium bloque la navigation locale avec ERR_BLOCKED_BY_ADMINISTRATOR. Aucune écriture réelle dans la base de production ni validation physique de la torche n’a été réalisée. ZXing et jsQR restent chargés à la demande depuis des CDN, avec URL de secours.

SÉCURITÉ / COMPATIBILITÉ
L’endpoint API, la clé locale du jeton d’appareil et les valeurs de résultat sont conservés. Le Worker Cloudflare, l’authentification côté serveur, manifest.webmanifest et sw.js ne sont pas modifiés.

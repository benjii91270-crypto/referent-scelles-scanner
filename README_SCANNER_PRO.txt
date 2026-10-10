RÉFÉRENT SCELLÉS — SCANNER QR TERRAIN
Version candidate : V2.8.1 — rôles administrateur/enquêteur
Statut : branche de préproduction à valider, non fusionnée.

RÈGLES FONCTIONNELLES
- Un téléphone autorisé ne constitue pas une session nominative. Après l’autorisation de l’appareil, l’utilisateur doit choisir son compte Référent Scellés et s’authentifier.
- Administrateur connecté : peut effectuer les contrôles physiques (conforme, absent, emplacement non conforme, intégrité à vérifier) et confirmer le retour en stock après confirmation physique.
- Enquêteur connecté : ne peut pas effectuer les contrôles physiques. Il peut uniquement prendre en charge un scellé en stock et le passer EN MOUVEMENT. Le nom est tiré de la session nominative et le motif est obligatoire ; destination facultative.
- Le contrôle des droits doit être validé côté serveur et non seulement dans l’interface.

V2.7/V2.8
- Interface terrain simplifiée, emplacement attendu mis en évidence, informations secondaires repliables.
- Mode série rapide, caméra/torche, reprise en cas d’erreur réseau, lecteur QR natif facultatif avec repli ZXing.

V2.8.1 — DROITS NOMINATIFS
- Connexion par session avec challenge et mot de passe ; session mémorisée au maximum 6 heures et possibilité de changer d’utilisateur.
- Contrôles physiques uniquement si la session serveur indique isAdmin=true.
- Formulaire de mouvement avec nom provenant de la session, motif obligatoire et destination facultative.
- Historique du mouvement affiche acteur, motif, destination et date.

INSTALLATION — IMPORTANT
Le dépôt du scanner n’héberge que l’interface statique. Le Worker Cloudflare et Apps Script sont des services distincts.
1. Sauvegarder le déploiement actuel de l’interface, le Worker Cloudflare et le projet Apps Script.
2. Installer d’abord le patch serveur contenu dans le fichier Referent_Scelles_Droits_Mouvement_Patch.zip sur une copie de test : Apps Script + Worker doivent être cohérents ensemble.
3. Le patch doit faire exiger une session administrateur pour l’API de contrôle et vérifier côté serveur que le nom du demandeur du mouvement correspond à la session. Il ajoute aussi le champ motif au relais Worker.
4. Publier cette branche sur une URL HTTPS de préproduction seulement.
5. Tester avec au moins un compte administrateur et un compte enquêteur : l’enquêteur doit être refusé côté serveur pour toute action de contrôle même s’il appelle directement l’API.
6. Tester un déplacement avec motif vide (refusé), un déplacement complet, un contrôle admin, un essai de contrôle enquêteur (refusé), un retour admin confirmé et un retour admin non confirmé (refusé).
7. Ne pas fusionner/déployer avant d’avoir validé ces scénarios avec des données fictives.

SÉCURITÉ / COMPATIBILITÉ
L’endpoint API et la clé locale du jeton d’appareil sont conservés. Le Worker ne doit pas exposer son secret partagé côté navigateur. Le présent changement ne doit pas être considéré sécurisé en production tant que le patch backend n’est pas installé sur les services réellement utilisés.

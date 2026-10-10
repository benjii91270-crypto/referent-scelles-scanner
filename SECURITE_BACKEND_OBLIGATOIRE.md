# Sécurité backend requise — V2.8.1

Cette version dépend d’un patch séparé livré sous la forme Referent_Scelles_Droits_Mouvement_Patch.zip.

Il faut déployer les deux côtés :
- Apps Script Code.gs : contrôle physique exigeant une session administrateur côté serveur ; prise en charge en mouvement exigeant une session valide, une identité égale au nom de la session et un motif non vide.
- Worker Cloudflare worker.js : relais du champ motif dans movement-start.

Le secret partagé reste côté Worker, jamais dans le HTML. Le nom envoyé par le client ne remplace pas l’identité de la session ; Apps Script doit faire la comparaison.

Ne fusionne/publie pas en production si le patch backend n’a pas d’abord été validé sur une copie de test. Un simple masquage des boutons ne suffit pas.

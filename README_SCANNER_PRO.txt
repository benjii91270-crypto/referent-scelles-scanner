SCANNER PRO EXTERNE — RÉFÉRENT SCELLÉS V2.4

Ce dossier doit être hébergé sur une URL HTTPS publique (GitHub Pages, Cloudflare Pages, Netlify, serveur HTTPS, etc.).
La caméra ne fonctionne pas depuis file:// et le navigateur doit autoriser getUserMedia.

ENDPOINT APPS SCRIPT INTÉGRÉ
https://script.google.com/macros/s/AKfycbyqtYW1tqfWFyz80AIPZCLJngdX-skcVYMdl2-C3TPfy9RGCNm-qPFi71qIbpa1xq440g/exec

APRÈS HÉBERGEMENT
1. Copie l’URL publique du dossier scanner, par exemple :
   https://votre-compte.github.io/referent-scelles/scanner/
2. Dans Apps Script, ouvre l’éditeur et exécute une fois :
   setPublicScannerUrl('https://votre-compte.github.io/referent-scelles/scanner/')
   (ou utilise une petite interface d’administration si elle est ajoutée plus tard).
3. Déploie une nouvelle version de la Web App Apps Script en conservant la même URL /exec.
4. Réimprime les fiches seulement pour les QR qui avaient déjà été imprimés si tu veux qu’ils pointent directement vers le scanner externe.
   Les anciens QR restent compatibles : Apps Script peut les rediriger vers le scanner externe une fois l’URL configurée.

PARCOURS
QR du téléphone -> Scanner Pro externe -> fiche du scellé -> contrôle -> Scanner le suivant -> caméra continue.

MOTEUR
ZXing Browser 0.2.1 (QR continu dans le navigateur).

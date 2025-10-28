# Sécurité

- Signale toute vulnérabilité via les issues privées ou email security@<domaine>.
- Ne publie **aucun secret** (clefs, .env, tokens) dans les PRs.
- Packages tiers doivent être scannés (Trivy, npm audit).
- Les PRs modifiant l’auth, l’ACL, ou les données sensibles exigent 2 reviewers.

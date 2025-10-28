# Contribuer

## Workflow
- Fork / branche `feat/...` ou `fix/...`
- Commits au format Conventional Commits
- PR avec description, tests, et mise à jour de docs si nécessaire

## Qualité
- Lint + tests doivent passer localement (`pnpm lint`, `pnpm test`)
- Ajoute des tests unitaires sur le code critique
- Documente les breaking changes dans le CHANGELOG

## Sécurité
- Pas de credentials en clair
- Utiliser secrets GitHub pour la CI

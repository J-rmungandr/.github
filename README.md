# 🧩 Burrito .github

> Dépôt central de **configuration GitHub** pour l’organisation [**@J-rmungandr**](https://github.com/J-rmungandr).  
> Contient les **templates d’issues**, **labels partagés**, **workflows CI/CD réutilisables** et **règles de gouvernance** communes à tous les projets **Burrito**.

---

## 🧭 À propos

Ce dépôt standardise et automatise la gestion de l’écosystème **Burrito**, afin que tous les projets partagent :
- Une **structure de CI/CD commune**  
- Des **labels d’issues cohérents**  
- Des **règles d’équipe (CODEOWNERS, CONTRIBUTING)**  
- Des **templates GitHub uniformes**  
- Des **workflows réutilisables** pour Node.js, Terraform, React Native, etc.  

> 🏗️ L’objectif : industrialiser le cycle de développement tout en gardant la cohérence et la qualité entre les projets.

---

## 📦 Structure du dépôt

```bash
.github/
 ├─ workflows/              # Workflows CI/CD réutilisables
 │   ├─ reusable-node-ci.yml
 │   ├─ reusable-react-ci.yml
 │   ├─ reusable-terraform-ci.yml
 │   ├─ labels-seed.yml
 │   └─ ...
 ├─ ISSUE_TEMPLATE/         # Templates GitHub pour issues
 │   ├─ bug_report.yml
 │   ├─ feature_request.yml
 │   ├─ rfc.yml
 │   └─ config.yml
 ├─ PULL_REQUEST_TEMPLATE/  # Templates pour les PR
 │   └─ default.md
 ├─ CODEOWNERS              # Définition des responsables par zone
 ├─ CONTRIBUTING.md         # Règles de contribution
 ├─ labels.yml              # Liste des labels standardisés
 ├─ FUNDING.yml             # Liens de sponsoring / support
 └─ README.md               # Ce fichier
```

---

## ⚙️ Workflows réutilisables

Les workflows définis ici peuvent être invoqués depuis n’importe quel dépôt de l’organisation :

### 🟦 Node / API

```yml
jobs:
  node:
    uses: J-rmungandr/.github/.github/workflows/reusable-node-ci.yml@main
    with:
      node_version: "20"
```

### 🟩 React / React Native

```yml
jobs:
  react:
    uses: J-rmungandr/.github/.github/workflows/reusable-react-ci.yml@main
    with:
      node_version: "20"
```

### 🟧 Terraform / Infra

```yml
jobs:
  terraform:
    uses: J-rmungandr/.github/.github/workflows/reusable-terraform-ci.yml@main
    with:
      working_directory: "./environments/prod"
```

---

## 🧾 Standardisation des labels

Tous les labels sont centralisés dans le fichier [labels.yml](./labels.yml)  
Ils peuvent être synchronisés automatiquement via le workflow [labels-seed.yml](./workflows/labels-seed.yml).

### 📘 Catégories de labels

| Catégorie | Exemple | Description |
|---------|---------|---------|
|Zone|`area:mobile`, `area:api`, `area:infra`, `area:design`|Domaine concerné|
|Type|`type:feature`, `type:bug`, `type:tech-debt`, `type:rfc`|Nature du ticket|
|Priorité|`P0`, `P1`, `P2`|Niveau d’urgence|
|Status|`status:in-progress`, `status:blocked`, `status:done`|État du travai|
|Meta|`good first issue`, `needs review`, `discussion`|Contexte ou aide à la contribution|

### ⚙️ Synchronisation manuelle

Synchronisation des labels sur tous les dépôts :

> Dans GitHub Actions → Workflows → “Seed Labels” → Run Workflow

---

## 🧱 Templates GitHub

### 🪲 Issue : Bug

[/.github/ISSUE_TEMPLATE/bug_report.yml](./ISSUE_TEMPLATE/bug_report.yml)
> Pour signaler un dysfonctionnement.

### ✨ Issue : Feature

[/.github/ISSUE_TEMPLATE/feature_request.yml](./ISSUE_TEMPLATE/feature_request.yml)
> Pour proposer une nouvelle fonctionnalité.

### 🧠 Issue : RFC

[/.github/ISSUE_TEMPLATE/rfc.yml](./ISSUE_TEMPLATE/rfc.yml)
> Pour proposer une évolution technique ou une refonte.

### 🔄 Pull Request Template

[/.github/PULL_REQUEST_TEMPLATE/default.md](./PULL_REQUEST_TEMPLATE/default.md)
> Fournit une checklist standardisée pour chaque PR :

- [ ] Description claire
- [ ] Tests / Lint / Build OK
- [ ] Documentation mise à jour
- [ ] Reviewer assigné

---

## 🧩 CODEOWNERS

Le fichier [CODEOWNERS](./CODEOWNERS) attribue automatiquement un reviewer selon la zone de code modifiée.  
Exemple :

```graphql
# Mobile
burrito-app-mobile/   @Hadock404

# API
burrito-api-gateway/  @Hadock404

# Infra
burrito-infra/        @Hadock404

# Design / Docs
burrito-design/       @Hadock404
burrito-docs/         @Hadock404
```

---

## 🧰 CONTRIBUTING.md

Ce document définit :
- Les conventions de commits (`feat:`, `fix:`, `chore:`, etc.)
- Les règles de branche (`main`, `feat/...`, `fix/...`)

Les étapes avant merge :
- Tests unitaires
- Lint
- Documentation à jour
- Review obligatoire

---

## 🔄 CI/CD globale

Les workflows de ce dépôt assurent :

- ✅ Lint du code
- 🧪 Tests unitaires
- 🧱 Build de production
- ☁️ Déploiement automatique (Cloud Run, Cloudflare, etc.)
- 🔒 Vérification de sécurité (Dependabot, npm audit)

---

## 🔐 Permissions & Sécurité

- Les GitHub Actions disposent de permissions en lecture/écriture (seulement sur les dépôts ciblés).
- Les secrets sont injectés depuis GitHub Environments (`dev`, `staging`, `prod`).
- Aucun secret sensible n’est stocké directement dans les fichiers YAML.
- Les workflows utilisent des GCP Service Accounts pour l’auth cloud.

## 📊 Gouvernance & Gestion de version

- Versioning sémantique appliqué sur tous les projets
Milestones partagés entre dépôts :
- MVP-v0.1 → prototype fonctionnel
- Beta-v0.2 → ajout du social / UX final
- GA-v1.0 → release publique
###
- Roadmap consolidée dans [burrito-docs](https://github.com/J-rmungandr/burrito-docs)

---

## 🧩 Intégration dans les autres projets

| Projet | Intégration |
|---------|---------|
|[burrito-app-mobile](https://github.com/J-rmungandr/burrito-app-mobile)|Utilise `reusable-react-ci.yml`|
|[burrito-api-gateway](https://github.com/J-rmungandr/burrito-api-gateway)|Utilise `reusable-node-ci.yml`|
|[burrito-infra](https://github.com/J-rmungandr/burrito-infra)|Utilise `reusable-terraform-ci.yml`|
|[burrito-design](https://github.com/J-rmungandr/burrito-design)|Reçoit les labels et templates communs|
|[burrito-shared](https://github.com/J-rmungandr/burrito-shared)|Utilise le pipeline Node CI|
|[burrito-web-admin](https://github.com/J-rmungandr/burrito-web-admin)|Reçoit les labels + PR template|

## 💬 Contribution

Ce dépôt est ouvert aux contributions internes :

- Ajout de nouveaux workflows réutilisables
- Amélioration des templates
- Évolution du modèle de labels ou des conventions

Checklist PR :

- [ ] YAML validé (`act` localement ou CI)
- [ ] Documentation mise à jour dans le README
- [ ] Tests sur dépôt de test (sandbox)
- [ ] Lint OK

## 👨‍🍳 Auteur & Contact

Maintainer : [@Hadock404](https://github.com/HaDock404)  
Organisation : [@J-rmungandr](https://github.com/J-rmungandr)

--- 

## 🧾 Licence

This project is licensed under the CC BY-NC-ND 4.0 License - see the [LICENSE](./LICENSE) file for details.
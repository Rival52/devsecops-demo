# 🚀 Pipeline DevSecOps & Jeu Tic Tac Toe

Ce projet montre comment mettre en place un pipeline **DevSecOps** complet et inclut un **jeu Tic Tac Toe** fonctionnel.

---

## 📜 Diagramme ASCII du pipeline DevSecOps

[ Developer ]
│
├── Push code to GitHub
│
[ GitHub Actions CI ]
│
├── (1) Lint + Tests + Type Check
├── (2) SAST Scan (CodeQL)
├── (3) Build Docker Image
├── (4) Scan de l'image (Trivy)
│ └── Échec si vulnérabilités HIGH/CRITICAL
├── (5) Push de l'image vers le registre
├── (6) Mise à jour des manifests Kubernetes
│
[ GitOps Repo ]
│
└── (7) ArgoCD détecte les changements
└── Déploiement sur le cluster Kubernetes


---

## 🔍 Étapes détaillées du pipeline

### 1. Push sur GitHub
- Chaque commit sur `main` déclenche automatiquement le pipeline via GitHub Actions.

### 2. Tests & Analyse statique
- **Linting** avec ESLint
- **Tests unitaires** (Vitest ou Jest)
- **Analyse SAST** avec CodeQL

### 3. Build de l'image Docker
- Multi-stage build pour réduire la taille et améliorer la sécurité.
- Suppression des dépendances inutiles.

### 4. Scan de sécurité de l'image
- **Trivy** analyse l’image pour trouver des CVEs (OS et dépendances applicatives).
- Si des vulnérabilités **HIGH** ou **CRITICAL** sont détectées → build échoué.

### 5. Push de l’image
- L’image Docker est poussée dans un registre (Docker Hub ou GHCR).

### 6. Mise à jour des manifests Kubernetes
- Le tag de l’image est remplacé dans `deployment.yaml` via un script automatisé.

### 7. Déploiement via ArgoCD
- ArgoCD détecte le changement dans le repo des manifests et met à jour le cluster Kubernetes.

---

## 🛡️ Sécurité intégrée

- **Shift-left security** : détection précoce des failles.
- **Analyse statique** (SAST) et dynamique (DAST possible).
- **Scans d’images** pour éviter les vulnérabilités connues.
- **RBAC Kubernetes** pour restreindre les accès.
- **Gestion des secrets** via GitHub Secrets ou Vault.

---

## ⚙️ Outils utilisés

- **GitHub Actions** – CI/CD
- **Docker** – Build & containerisation
- **Trivy** – Scan de sécurité
- **CodeQL** – Analyse statique
- **ArgoCD** – GitOps & déploiement Kubernetes
- **Kubernetes** – Orchestration

---

## 📂 Structure du projet DevSecOps

devsecops-demo/
├── Dockerfile
├── kubernetes/
│ ├── deployment.yaml
│ ├── service.yaml
│ └── ...
├── src/
├── package.json
├── vite.config.ts
├── tsconfig.json
├── README.md


---

# 🎮 Tic Tac Toe – Implémentation DevSecOps

![Capture d'écran](https://github.com/user-attachments/assets/7ed79f9c-9144-4870-accd-500085a15592)

![Image du jeu](https://github.com/user-attachments/assets/5b2813a5-f493-4665-8964-77359b5be93a)

## Fonctionnalités

- 🎮 Jeu Tic Tac Toe entièrement fonctionnel
- 📊 Suivi des scores pour X, O et les matchs nuls
- 📜 Historique des parties avec horodatage
- 🏆 Mise en évidence des combinaisons gagnantes
- 🔄 Réinitialisation du jeu et des statistiques
- 📱 Design responsive pour tous les appareils

## Technologies utilisées

- React 18
- TypeScript
- Tailwind CSS
- Lucide React pour les icônes

## Structure du projet Tic Tac Toe

src/
├── components/
│ ├── Board.tsx # Composant du plateau de jeu
│ ├── Square.tsx # Composant de chaque case
│ ├── ScoreBoard.tsx # Suivi des scores
│ └── GameHistory.tsx # Historique des parties
├── utils/
│ └── gameLogic.ts # Logique du jeu
├── App.tsx # Composant principal
└── main.tsx # Point d'entrée



## Logique du jeu

1. X commence, suivi de O
2. Le premier joueur à aligner 3 marques (horizontal, vertical ou diagonal) gagne
3. Si toutes les 9 cases sont remplies et qu'aucun joueur n'a 3 marques alignées → match nul
4. Les combinaisons gagnantes sont mises en évidence
5. Les statistiques de jeu sont suivies et affichées

## Démarrage

### Prérequis

- Node.js (v14 ou supérieur)
- npm ou yarn

### Installation

1. Cloner le dépôt :
```bash
git clone https://github.com/yourusername/devsecops-demo.git
cd devsecops-demo
```
Installer les dépendances :
```
npm install
# ou
yarn
```


Démarrer le serveur de développement :
```
npm run dev
# ou
yarn dev
```


Ouvrir le navigateur à l'adresse http://localhost:5173

Build pour la production

Pour créer une version de production :
```
npm run build
# ou
yarn build
```

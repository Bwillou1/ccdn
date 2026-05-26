# Manuel de Déploiement Décentralisé - CCDN

Ce guide explique comment héberger la plateforme **CCDN** de manière incensurable et autonome en utilisant des technologies décentralisées.

---

## 1. Hébergement sur IPFS (InterPlanetary File System)

Puisque CCDN est composée exclusivement de fichiers statiques (`index.html`, `style.css`, `app.js`), elle est nativement compatible avec IPFS.

### Option A : Déploiement via Fleek (Automatisé & Recommandé)
[Fleek](https://fleek.co/) permet de lier un dépôt Git (GitHub/GitLab) et de déployer automatiquement sur IPFS à chaque commit.
1. Connectez-vous sur Fleek.
2. Liez le dépôt contenant ce dossier.
3. Configurez le build :
   * **Framework :** Other (Statique)
   * **Build Command :** *laisser vide*
   * **Publish Directory :** `./`
4. Fleek génèrera automatiquement un hash IPFS (CID) unique et mettra à jour l'accès.

### Option B : Déploiement Manuel en Ligne de Commande (CLI IPFS)
Si vous souhaitez héberger le site directement depuis votre propre machine de manière souveraine :
1. Installez IPFS :
   ```bash
   brew install ipfs
   ipfs init
   ```
2. Démarrez le démon IPFS :
   ```bash
   ipfs daemon
   ```
3. Ajoutez le dossier à IPFS :
   ```bash
   ipfs add -r /chemin/vers/TOKEN_STOP
   ```
4. Vous obtiendrez un CID (Content Identifier) de dossier, par exemple :
   `QmXoypizjW3WknFixtndV37ip71m3FPHkuLFnN8N5nzw53`
5. Le site est désormais accessible via n'importe quelle passerelle publique IPFS, par exemple :
   `https://ipfs.io/ipfs/QmXoypizjW3WknFixtndV37ip71m3FPHkuLFnN8N5nzw53/`

---

## 2. Configuration d'un nom de domaine incensurable (ENS - Ethereum Name Service)

Pour éviter qu'un registrar DNS classique (comme GoDaddy ou Gandi) puisse bloquer le domaine sous la pression de tiers :
1. Enregistrez un nom de domaine `.eth` sur [app.ens.domains](https://app.ens.domains/) (ex: `ccdn.eth`).
2. Dans la section **Content** de l'enregistrement de votre nom ENS, entrez le hash IPFS généré à l'étape précédente :
   `ipfs://QmXoypizjW3WknFixtndV37ip71m3FPHkuLFnN8N5nzw53`
3. Les utilisateurs disposant de navigateurs compatibles (Brave, Opera) ou d'extensions comme MetaMask pourront accéder directement au site en tapant `ccdn.eth`.
4. Pour les navigateurs classiques, le site sera résolu via `ccdn.eth.limo` ou `ccdn.eth.link`.

---

## 3. Gestion Décentralisée de la Collecte

Dans un modèle standard, les données soumises transitent par des serveurs. Pour CCDN :
1. **Dossier local :** Le formulaire génère un paquet de preuve JSON crypté de bout en bout. L'utilisateur peut simplement télécharger ce fichier et l'envoyer manuellement par messagerie sécurisée (Signal, ProtonMail) aux avocats désignés.
2. **P2P OrbitDB :** Pour synchroniser les bases de données directement de navigateur à navigateur sans passer par un serveur tiers, l'application peut se connecter à un réseau OrbitDB de confiance. Les hashs et métadonnées y sont stockés de manière distribuée et immuable.

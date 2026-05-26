# 🛡️ Coalition Citoyenne de Défense Numérique (CCDN)

La **CCDN** est une plateforme web décentralisée, internationale et ultra-sécurisée conçue pour aider les citoyens à documenter et signaler les modifications contractuelles unilatérales imposées par les géants technologiques (notamment le forçage vers les services et l'entraînement d'IA Gemini par Google).

Ce site sert de portail d'éducation et de hub d'action directe pour déposer des plaintes officielles sur **econsumer.gov** en s'appuyant sur des bases juridiques solides.

---

## 📖 Sommaire
1. [Fonctionnalités](#-fonctionnalités)
2. [Bases Juridiques par Juridiction](#-bases-juridiques-par-juridiction)
3. [Structure du Projet](#-structure-du-projet)
4. [Configuration & Personnalisation](#-configuration--personnalisation)
5. [Déploiement Décentralisé & Incensurable](#-déploiement-décentralisé--incensurable)
6. [Sécurité & Confidentialité (Ultra-Sec)](#-sécurité--confidentialité-ultra-sec)

---

## ✨ Fonctionnalités
* 🌐 **Traduction dans plus de 100 langues** : Intégration d'un module de traduction universel côté client, respectueux du thème sombre.
* ⚖️ **Jurisdictions Internationales** : Modèles juridiques sur mesure adaptés au Québec/Canada, à l'Union Européenne, aux États-Unis, au Royaume-Uni et à l'Australie.
* 📋 **Modèles de Copie Rapide** : Données corporatives cibles (Google LLC, Google Ireland Ltd) et descriptions des préjudices copiables en un clic pour saisie directe sur **econsumer.gov**.
* 🕸️ **Conçu pour la Décentralisation** : Fichiers 100 % statiques sans base de données centrale, hébergeables sur IPFS/ENS.

---

## ⚖️ Bases Juridiques par Juridiction

### 1. Canada (Québec)
* **Loi sur la protection du consommateur (LPC), art. 11.3** : Interdit la modification unilatérale d'un élément essentiel du contrat à moins de fournir un avis écrit de 30 jours permettant au consommateur de résilier sans frais. Le blocage ou la dégradation d'un service (Drive, Gmail) suite au refus des conditions Gemini est illégal.
* **Code civil du Québec, art. 1437** : Annule toute clause abusive ou créant un déséquilibre significatif dans un contrat d'adhésion.
* **LPC, art. 19** : Rend nulles les clauses de renonciation aux actions collectives.

### 2. Union Européenne (UE)
* **RGPD, art. 7(4) (Conditionnalité du consentement)** : Le consentement ne peut être libre si l'accès à un service de base (email, stockage) est lié à l'acceptation de traitements de données non nécessaires (entraînement d'IA).
* **Directive 93/13/CEE (Clauses contractuelles abusives)** : Répute abusive toute clause permettant au professionnel de modifier unilatéralement les termes du contrat sans motif valable spécifié.

### 3. États-Unis (USA)
* **FTC Act, Section 5 (15 U.S.C. § 45)** : Interdit les pratiques déloyales ou trompeuses. Les modifications unilatérales et rétroactives des politiques de données sans consentement actif (opt-in) sont considérées comme frauduleuses (Jurisprudence *FTC v. Gateway Learning Corp.*).
* **California CCPA/CPRA** : Droit de s'opposer à la vente ou au partage des données personnelles à des fins de profilage/IA, sans subir de dégradation de service.

---

## 📁 Structure du Projet
```
├── index.html                  # Interface utilisateur unifiée (Manifeste + Modèles)
├── style.css                   # Styles premium en thème sombre et glassmorphism
├── app.js                      # Interactivité légère du client (onglets)
├── deploy.py                   # Script Python d'automatisation de déploiement (sécurisé)
├── .gitignore                  # Exclusion des scripts de clés/tokens sensibles
└── DECENTRALIZED_DEPLOYMENT.md # Manuel d'hébergement sur IPFS / ENS
```

---

## ⚙️ Configuration & Personnalisation

### Exécuter localement
Pour tester ou modifier la plateforme sur votre machine :
1. Lancez un serveur web statique léger :
   ```bash
   python3 -m http.server 8000
   ```
2. Ouvrez votre navigateur sur `http://localhost:8000`.

### Personnaliser les Textes de Plaintes
Les modèles de plaintes copiables se situent dans la balise `<script>` à la fin de [index.html](index.html) au sein de l'objet `legalData` :
```javascript
const legalData = {
  qc: {
    entity: "Adresse de Google Canada Corp...",
    title: "Titre de l'action...",
    text: "Votre texte juridique béton..."
  },
  // ...
};
```

---

## 🕸️ Déploiement Décentralisé & Incensurable

### GitHub Pages (Ce dépôt)
Le site est hébergé par défaut via GitHub Pages. Le déploiement est automatique à chaque push sur la branche `main` à l'adresse :
`https://bwillou1.github.io/ccdn/`

### IPFS & Fleek (Anti-Censure)
1. Liez ce dépôt sur [Fleek.co](https://fleek.co).
2. Configurez le déploiement statique automatique.
3. Obtenez un hash IPFS (CID) pour accéder au site de manière distribuée.

### Résolution de nom de domaine via ENS (Ethereum Name Service)
1. Enregistrez un nom `.eth` (ex: `ccdn.eth`) sur le protocole ENS.
2. Pointez l'enregistrement **Content** vers le hash IPFS : `ipfs://[VOTRE_HASH_CID]`.
3. Le site devient accessible via les navigateurs Web3 ou par les passerelles DNS publiques comme `ccdn.eth.limo`.

---

## 🔒 Sécurité & Confidentialité (Ultra-Sec)

La plateforme intègre des politiques de sécurité strictes directement dans le code source de l'en-tête HTML (`index.html`) :

1. **Content Security Policy (CSP)** :
   ```html
   <meta http-equiv="Content-Security-Policy" content="default-src 'self' ...">
   ```
   * Empêche l'exécution de scripts tiers malveillants (XSS).
   * Interdit le détournement de clic (Clickjacking) en bloquant l'affichage du site dans des cadres tiers.
2. **Referrer Policy (`no-referrer`)** : Empêche la transmission de l'adresse de votre site ou d'informations de session lors du clic sur des liens externes (ex: econsumer.gov).
3. **Permissions Policy** : Coupe l'accès aux capteurs physiques (caméra, microphone, géolocalisation) pour garantir l'anonymat absolu des visiteurs.

# 🔐 Audit de coffre-fort

Un outil d'audit de sécurité pour votre coffre-fort **Bitwarden**, inspiré du rapport de santé des mots de passe premium — mais **100 % local, gratuit et open source**.

Aucune donnée ne quitte jamais votre navigateur : pas de serveur, pas d'API, pas de tracking.

![100% local](https://img.shields.io/badge/données-100%25%20locales-3fc98a)
![Aucune dépendance](https://img.shields.io/badge/dépendances-aucune-4f7cff)
![Licence MIT](https://img.shields.io/badge/licence-MIT-8b90a3)

---

## ✨ Fonctionnalités

- **Score global du coffre-fort** — une jauge synthétique de 0 à 100 basée sur les mots de passe faibles, dupliqués et réutilisés
- **Détection des mots de passe dupliqués** — regroupe automatiquement les comptes qui partagent le même mot de passe
- **Détection des mots de passe faibles** — calcul d'entropie réelle (longueur × diversité de caractères) + liste de mots de passe trop communs
- **Détection des identifiants réutilisés** — repère les logins/emails utilisés sur plusieurs comptes
- **Recherche par mot de passe** — colle un mot de passe et retrouve instantanément tous les comptes qui l'utilisent
- **Âge des mots de passe** — affiche depuis combien de temps chaque élément n'a pas été modifié
- **Suivi de progression** — cochez les comptes corrigés au fur et à mesure, avec une barre de progression sauvegardée localement
- **Interface sombre** inspirée du design de Bitwarden

## 🚀 Utilisation

1. Dans Bitwarden : **Paramètres → Outils d'export → Exporter le coffre**, au format **JSON** (non chiffré)
2. Ouvrez `audit-coffre-fort.html` en le double-cliquant (aucune installation, aucun serveur requis)
3. Glissez-déposez le fichier JSON exporté dans la zone prévue, ou cliquez pour le sélectionner
4. Parcourez le rapport et corrigez les comptes à risque

> ⚠️ Une fois l'analyse terminée, pensez à supprimer le fichier JSON exporté : il contient tous vos mots de passe en clair.

## 🔒 Confidentialité

Ce projet est un **fichier HTML unique**, sans build, sans framework, sans dépendance externe autre que les polices Google Fonts (chargées via CDN, uniquement pour l'affichage).

- Aucune requête réseau n'est effectuée avec vos données
- Aucun cookie, aucun tracker
- La seule donnée persistée est la liste des comptes que vous avez cochés comme « corrigés », stockée dans le `localStorage` de votre navigateur — jamais transmise nulle part

Vous pouvez vérifier ceci vous-même : ouvrez le code source, il n'y a aucun `fetch` ni `XMLHttpRequest` vers un serveur tiers.

## 🧮 Comment le score est calculé

Le score global (0-100) est une moyenne pondérée basée sur trois facteurs, rapportés au nombre total de comptes :

- **50 %** — proportion de mots de passe faibles ou communs
- **35 %** — proportion de comptes utilisant un mot de passe dupliqué
- **15 %** — proportion de comptes utilisant un identifiant réutilisé

Un score de 100 signifie qu'aucun problème n'a été détecté.

## 🛠️ Stack technique

- HTML / CSS / JavaScript vanilla — aucun framework, aucune étape de build
- Police [Space Grotesk](https://fonts.google.com/specimen/Space+Grotesk), [Inter](https://fonts.google.com/specimen/Inter) et [JetBrains Mono](https://fonts.google.com/specimen/JetBrains+Mono)

## 📋 Limitations connues

- L'export Bitwarden doit être au format **JSON non chiffré** (le format CSV n'est pas supporté)
- L'« âge » affiché correspond à la date de dernière modification de la fiche dans Bitwarden (`revisionDate`), qui peut avoir été mise à jour pour une raison autre que le changement du mot de passe
- La progression des corrections est liée au navigateur utilisé : elle n'est pas synchronisée entre appareils

## 🤝 Contribuer

Les suggestions et pull requests sont bienvenues. Quelques idées d'améliorations possibles :

- Détection de mots de passe similaires (pas seulement identiques)
- Export du rapport en PDF/CSV
- Filtrage par dossier Bitwarden
- Marquage de comptes comme « critiques » pour les prioriser

## 📄 Licence

MIT — libre d'utilisation, de modification et de distribution.

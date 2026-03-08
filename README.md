# Signalement municipal — PWA

Application web **PWA** permettant aux citoyens de signaler des anomalies (dégradations, casse, etc.) à leur commune de manière **anonyme**, et aux agents municipaux de traiter et suivre ces signalements. Conçue pour un usage multi-communes (SaaS) avec gestion des quotas et rôles.

**Démo :** [signalement.psweb.fr](https://signalement.psweb.fr)

---

## Contexte

Projet full-stack réalisé sur la base d’un cahier des charges (signalement citoyen, interface agent, super-admin, RGPD, accessibilité). L’application est déployée en production (Docker, PostgreSQL, reverse proxy HTTPS).

---

## Stack technique

| Couche | Technologies |
|--------|--------------|
| **Frontend** | Next.js 16.1 (App Router), React, TypeScript, Tailwind CSS |
| **PWA** | Manifest, Service Worker, installation sur mobile, usage offline partiel |
| **Backend** | Next.js API Routes, Prisma (ORM), PostgreSQL |
| **Auth** | JWT (cookie httpOnly), rôles (Agent, Responsable, Super Admin), 2FA (TOTP) |
| **Carte** | Leaflet, OpenStreetMap |
| **Qualité** | Vitest (tests unitaires), Playwright (E2E), ESLint, CI GitHub Actions |
| **Déploiement** | Docker (app + Nginx + PostgreSQL), stack isolée |

L’ensemble du produit est développé en **TypeScript**, avec une **charte graphique** stricte (couleurs, typo, breakpoints) et une attention à l’**accessibilité** (WCAG 2.1 AA, contraste, sémantique).

---

## Fonctionnalités principales

### Côté citoyen
- Choix de la commune puis **dépôt de signalement** (description, adresse ou géolocalisation, photos).
- **Token anonyme** pour suivre l’état du signalement sans créer de compte.
- Interface responsive et **installable** (PWA).
- Respect **RGPD** : pas de données personnelles obligatoires ; purge des photos après résolution.

### Côté agent / responsable
- Tableau de bord des signalements (à traiter, en cours, résolus).
- Affectation, catégories, réglages par commune (bandeau, logo, couleurs).
- Module **SAV / remontée de bugs** depuis l’interface.
- Double authentification (2FA) possible.

### Super Admin
- Gestion **multi-communes** : création, activation, quotas (signalements/mois, photos, stockage).
- Gestion des utilisateurs (agents, responsables) par commune.
- Vue globale des signalements, options (rapports, domaine personnalisé, etc.).
- Logs et audit des actions sensibles.

### Qualité et bonnes pratiques
- **Tests** : unitaires (logique métier, auth, charte) et E2E (parcours citoyen, formulaire).
- **CI** : à chaque push/PR, exécution de type-check, lint, tests et build.
- **Architecture** : multi-tenant (isolation par commune), modèle rôles/permissions, quotas et abonnements (Standard / Premium) gérés en base.

---

*Projet démonstration — PS-Web Solutions.*

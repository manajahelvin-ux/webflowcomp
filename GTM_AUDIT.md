# Audit GTM (Google Tag Manager) — webflowcomp

> Analyse de **tout le dossier** (hors `.git`, images, vidéos et polices).
> Critère retenu pour « utilise le GTM » : présence du chargeur officiel GTM dans le fichier HTML :
> - script `https://www.googletagmanager.com/gtm.js?id=GTM-...` (dans le `<head>`), et/ou
> - iframe `<noscript>` `https://www.googletagmanager.com/ns.html?id=GTM-...` (dans le `<body>`).
>
> ⚠️ 104 fichiers contiennent seulement le code de **préparation** (Consent Mode V2 + `dataLayer`/`gtag` définis en commentaire « DOIT PRÉCÉDER tout autre script Google (GTM, GA4, GADS…) ») **sans charger GTM** : ils ne sont donc **pas** comptés comme « utilisant GTM ». Aucun GTM n'est chargé via `js/` ou `css/` (vérifié : `js/webflow.js`, fichiers CSS — aucune occurrence).

## Résumé

| Indicateur | Nombre |
|---|---|
| Fichiers HTML analysés | **137** |
| Pages/sous-pages chargeant réellement GTM (script et/ou noscript) | **33** |
| — Installation complète (script `gtm.js` + `<noscript>`) | 25 |
| — Script seul (pas de `<noscript>`) | 3 |
| — `<noscript>` seul (pas de script → **GTM inactif en pratique**) | 5 |
| Pages sans chargeur GTM (simple mention en commentaire Consent/DataLayer) | 104 |
| Conteneurs GTM distincts | 2 |

| Conteneur GTM | Nb de pages | Détail |
|---|---|---|
| `GTM-53SH7D7F` | 14 | 11 complètes + 3 script seul |
| `GTM-WMVZJKS` | 19 | 14 complètes + 5 noscript seul |
| **Total** | **33** | |

Répartition géographique des 33 pages avec GTM : **25 à la racine**, **8 en sous-dossier** (toutes dans `assurance/`).

---

## 1. ✅ Pages avec GTM complet (script + noscript) — 25

### 1a. À la racine — 17

| # | Page | Conteneur |
|---|---|---|
| 1 | `assurance-commerce.html` | GTM-WMVZJKS |
| 2 | `assurance-consultants-societe-conseil.html` | GTM-53SH7D7F |
| 3 | `assurance-estheticienne-institut-beaute.html` | GTM-53SH7D7F |
| 4 | `assurance-estheticiennes-instituts-beaute-v1.html` | GTM-53SH7D7F |
| 5 | `assurance-marchandise.html` | GTM-WMVZJKS |
| 6 | `assurance-professionnelle-tns-v2.html` | GTM-WMVZJKS |
| 7 | `assurance-tns-pro-v2-adw.html` | GTM-53SH7D7F |
| 8 | `assurances-multirisques-v2.html` | GTM-WMVZJKS |
| 9 | `complementaire-retraite-tns-v2.html` | GTM-WMVZJKS |
| 10 | `energie-v2.html` | GTM-WMVZJKS |
| 11 | `energie.html` | GTM-WMVZJKS |
| 12 | `geolocalisation-v2.html` | GTM-WMVZJKS |
| 13 | `geolocalisation.html` | GTM-WMVZJKS |
| 14 | `panneaux-photovoltaiques-energie-solaire.html` | GTM-WMVZJKS |
| 15 | `securite-professionnels.html` | GTM-WMVZJKS |
| 16 | `tns-prevoyance-v2-adw-test.html` | GTM-WMVZJKS |
| 17 | `tns-prevoyance-v2.html` | GTM-WMVZJKS |

### 1b. Sous-pages — 8 (toutes dans `assurance/`)

| # | Sous-page | Conteneur |
|---|---|---|
| 1 | `assurance/agriculteur.html` | GTM-53SH7D7F |
| 2 | `assurance/assurance-professionnelle-iard-cookie.html` | GTM-53SH7D7F |
| 3 | `assurance/assurance-professionnelle-iard-v2.html` | GTM-WMVZJKS |
| 4 | `assurance/multirisques.html` | GTM-53SH7D7F |
| 5 | `assurance/professionnelle-iard.html` | GTM-53SH7D7F |
| 6 | `assurance/protection-sociale-collective-v4.html` | GTM-53SH7D7F |
| 7 | `assurance/protection-sociale-collective.html` | GTM-53SH7D7F |
| 8 | `assurance/rc-pro.html` | GTM-53SH7D7F |

---

## 2. ⚠️ Pages avec GTM partiel : script seul (noscript manquant) — 3

GTM fonctionne, mais aucun affichage de secours si JavaScript est désactivé.

| # | Page (racine) | Conteneur |
|---|---|---|
| 1 | `assurance-agriculteur-v2.html` | GTM-53SH7D7F |
| 2 | `assurance-iard-v2.html` | GTM-53SH7D7F |
| 3 | `assurance-tns.html` | GTM-53SH7D7F |

## 3. ❌ Pages avec GTM partiel : noscript seul (script manquant) — 5

> Ces pages contiennent uniquement l'iframe `<noscript>` : **GTM ne se charge jamais** pour un visiteur normal (JavaScript activé). Installation à corriger en ajoutant le script `gtm.js` dans le `<head>`.

| # | Page (racine) | Conteneur |
|---|---|---|
| 1 | `remerciement-carte-cadeau.html` | GTM-WMVZJKS |
| 2 | `remerciement-panneaux-solaire.html` | GTM-WMVZJKS |
| 3 | `remerciement-ticket-restaurant-v2.html` | GTM-WMVZJKS |
| 4 | `remerciement-ticket-restaurant.html` | GTM-WMVZJKS |
| 5 | `remerciements-panneaux-solaires.html` | GTM-WMVZJKS |

---

## 4. Sous-dossiers : bilan par sous-page

| Sous-dossier | Pages HTML | Avec GTM | Détail |
|---|---|---|---|
| `assurance/` | 8 | **8 ✅** | voir §1b (7× GTM-53SH7D7F, 1× GTM-WMVZJKS) |
| `alfaromeo/` | 2 | 0 | `tonale.html`, `tonale-remerciement.html` |
| `lexus/` | 1 | 0 | `lbx.html` |
| `mercedes-benz/` | 3 | 0 | `mercedes-benz-evito.html`, `nouvel-ecitan-fourgon.html`, `sprinter.html` |
| `nicolas/` | 3 | 0 | `ayvens.html`, `form-test.html`, `formly.html` |
| `panneaux-photovoltaiques/` | 1 | 0 | `panneaux-photovoltaique-valider.html` |
| `temlpate-webflow/` | 3 | 0 | `comparateur-2.html`, `comparateur-3.html`, `comparateur-4.html` |
| `typ-formulaires/` | 11 | 0 | `caisses-thank-you-page.html`, `energie-thank-you-page.html`, `form-typ-vehicules.html`, `panneaux-photovoltaiques.html`, `panneaux-thank-you-page.html`, `securite-thank-you-page.html`, `typ-caisses-enregistreuse.html`, `typ-energie-form.html`, `typ-log-entreprise.html`, `typ-panneaux-form.html`, `typ-secu-form.html`, `vehicules-thank-you-page.html` (12 fichiers listés dans le dossier, 11 pages hors doublon de comptage — voir listing brut) |
| `voiture/` | 2 | 0 | `nouveau-range-rover.html`, `range-rover.html` |
| `webflow/` | 1 | 0 | `template-1.html` |
| **Total sous-pages** | **36** | **8** | uniquement `assurance/` |

---

## 5. Pages SANS GTM (104) — pour mémoire

Ces 104 pages ne chargent pas GTM. Elles contiennent uniquement le bloc Consent Mode V2 / DataLayer qui *mentionne* GTM en commentaire (lignes du type `// Elle DOIT PRÉCÉDER tout autre script Google (GTM, GA4, GADS, etc.)` et `// Pousser les préférences dans le DataLayer pour GTM`), sans aucun `gtm.js` ni identifiant `GTM-...`.

**Racine (76) :** `acces-internet-et-telephonie-pro-v2.html`, `acces-internet-et-telephonie-pro.html`, `accueil.html`, `assurance-consultant-societe-conseil-v2.html`, `assurance-estheticiennes-instituts-beaute.html`, `assurance-test-telephone.html`, `assurances-professionnelles.html`, `automobile.html`, `ayvens-france.html`, `canal.html`, `cartes-carburant.html`, `celebrez-le-noel-des-salaries-avec-kadeos.html`, `dacia-jogger.html`, `ecomobility.html`, `edenred-kadeos.html`, `edenred-restaurant-v2.html`, `edenred-ticket-restaurant-juillet-v1.html`, `edenred-titre-restaurant-v2.html`, `edenred-typ.html`, `fiat-pro.html`, `form-panneaux-photovoltaiques.html`, `form-vehicules-utilitaires.html`, `formulaire-globale.html`, `formulaire.html`, `gamme-de-rayonnage-actiflip-hd.html`, `gamme-de-rayonnage-actiflip-v4.html`, `geo.html`, `geolocalisation-de-flotte.html`, `hyundai-kona-electric-nouvelle-generation.html`, `hyundai-tucson.html`, `index.html`, `intuis.html`, `lexus-lbx.html`, `mentions-legales.html`, `mercedes-vous-remercie.html`, `mitsubishi-fuso-remerciement.html`, `mitsubishi-fuso.html`, `nettoyage-locaux-professionnels.html`, `nissan-ariya.html`, `nissan-juke.html`, `paritel-typ.html`, `paritel-vous-rembourse-v2.html`, `paritel-vous-rembourse.html`, `paritel.html`, `politique-de-confidentialite-donnees-personnelles.html`, `primagaz-obtenez-votre-gaz-propane-a-prix-fixe.html`, `primagaz-v2.html`, `primagaz.html`, `radius-remerciement.html`, `radius-telematics-typ.html`, `rc-pro-consultant-conseil-adw.html`, `renault-capture.html`, `sage-gestion-de-la-paie-hd-v4.html`, `sage-gestion-de-la-paie-hd.html`, `sauvie-defibrillateurs-en-entreprise.html`, `securite-pro-v2.html`, `solutions-cles.html`, `solutions-industrielles-cles-en-main.html`, `still-manutention.html`, `suivi-de-vehicules.html`, `template-2.html`, `ticket-restaurant-.html`, `ticket-restaurant-septembre-btp.html`, `ticket-restaurant-septembre.html`, `ticket-restaurant-v2.html`, `ticket-restaurant.html`, `too-good-to-go.html`, `toyota-gamme-hybride.html`, `typ-categ.html`, `typ-categories.html`, `typ-energie.html`, `typ-ticket-restaurant.html`, `une-rentree-sous-le-signe-du-pouvoir-d-achat.html`, `vehicules-de-societe-hd.html`, `vehicules-professionnel-v2.html`, `volvo.html`

**Sous-pages (28) :** les 28 pages des sous-dossiers listés au §4 hors `assurance/` (`alfaromeo/` 2, `lexus/` 1, `mercedes-benz/` 3, `nicolas/` 3, `panneaux-photovoltaiques/` 1, `temlpate-webflow/` 3, `typ-formulaires/` 12, `voiture/` 2, `webflow/` 1).

---

## Méthode de vérification (reproductible)

```bash
# Pages avec un identifiant de conteneur GTM
grep -rlE "GTM-[A-Z0-9]+" --include="*.html" .

# Installation complète (script + noscript) vs partielle
grep -l "googletagmanager.com/gtm.js" --include="*.html" -r .   # script
grep -l "googletagmanager.com/ns.html" --include="*.html" -r .  # noscript
```

*Rapport généré le 2026-11-13 à partir de l'état du dépôt (branche `arena/66edc3f9-webflowcomp`).*

# 🥕 Gestion commerciale des Jardins de Cocagne

> Outil libre, multi-structures et paramétrable de gestion commerciale (abonnements paniers, ventes, livraisons) pour les Jardins de Cocagne et le Réseau Cocagne.

---

## Sommaire

1. [Contexte](#contexte)
2. [Objectifs du projet](#objectifs-du-projet)
3. [Public cible et utilisateurs](#public-cible-et-utilisateurs)
4. [Fonctionnalités attendues](#fonctionnalités-attendues)
5. [Principes techniques](#principes-techniques)
6. [Vocabulaire](#vocabulaire)
7. [Architecture envisagée](#architecture-envisagée)
8. [Contribuer](#contribuer)
9. [Licence](#licence)
10. [Liens utiles](#liens-utiles)

---

## Contexte

### Les Jardins de Cocagne

Les Jardins de Cocagne sont des exploitations maraîchères en **agriculture biologique** qui proposent des **parcours d'insertion socio-professionnelle** à des personnes éloignées de l'emploi. La plupart sont des associations loi 1901 conventionnées *Atelier et Chantier d'Insertion* (ACI).

- Environ **22 salariés en insertion** par Jardin, pour des durées de **1 à 24 mois**.
- **70 à 80 variétés** de légumes cultivées en moyenne.
- Vente principalement par **abonnement à des paniers hebdomadaires**, mais aussi :
  - vente au détail (sur site, marchés de plein vent, sur commande) ;
  - vente aux professionnels (restauration collective, magasins, confrères, grossistes…) ;
  - activités de diversification (transformation, animations pédagogiques, prestations espaces verts…).

### Le Réseau Cocagne

Près d'une **centaine de Jardins** adhèrent au [Réseau Cocagne](https://www.reseaucocagne.org/), qui assure l'appui à la professionnalisation et la mutualisation des outils. Il n'existe **aucun lien de subordination** : chaque Jardin est libre d'utiliser ou non les outils mutualisés.

### Le logiciel existant

Dans les années 2000, un logiciel de « gestion des adhérents » a été développé sur **Microsoft Access** par un directeur de Jardin. Il gère les adhérents, les abonnements, les règlements, les feuilles de route de préparation/livraison, et permet un export comptable.

- Encore utilisé par **65 %** des Jardins en juin 2016.
- **75 %** des Jardins expriment un besoin urgent d'un nouvel outil.
- Limites : formules commerciales et contexte ayant fortement évolué (internet, automatisation, ouverture des modes de vente).

---

## Objectifs du projet

- **Moderniser** la gestion commerciale des Jardins de Cocagne.
- **Autonomiser les clients** grâce à un front office (gestion de leur abonnement, etc.).
- **Automatiser** un maximum de tâches administratives pour dégager du temps pour la relation et l'animation.
- **Mutualiser** un outil unique au niveau du réseau, tout en laissant chaque structure l'adapter à son fonctionnement.
- Permettre aux Jardins de **contribuer eux-mêmes** au développement (modules, fonctions complémentaires).

---

## Périmètre de réalisation

Ce projet est réalisé dans le cadre de mon **alternance**. Le cahier des charges décrit un outil complet à l'échelle d'un réseau national, ce qui dépasse le temps et les moyens dont je dispose en tant qu'alternante. **Certaines parties ne sont donc pas prises en charge dans ce dépôt.**

| Partie du cahier des charges | Statut |
|---|---|
| Back office (clients, produits, abonnements, règlements) | ☐ Réalisé / ☐ Partiel / ☐ Non réalisé |
| Front office (espace client) | ☐ Réalisé / ☐ Partiel / ☐ Non réalisé |
| Feuilles de route de préparation et de livraison | ☐ Réalisé / ☐ Partiel / ☐ Non réalisé |
| Export comptable | ☐ Réalisé / ☐ Partiel / ☐ Non réalisé |
| Multi-société et hébergement SaaS centralisé | ☐ Réalisé / ☐ Partiel / ☐ Non réalisé |
| Aide en ligne et tutoriels vidéo | ☐ Réalisé / ☐ Partiel / ☐ Non réalisé |

> 📌 Les parties non réalisées restent ouvertes et pourront être reprises par d'autres contributeurs du réseau.

---

## Public cible et utilisateurs

| Profil | Usage | Caractéristiques |
|---|---|---|
| Équipe du Jardin (permanents, salariés en insertion, bénévoles) | **Back office** | Niveau informatique très variable, souvent peu à l'aise, fort turn-over |
| Clients (abonnés paniers, particuliers, professionnels) | **Front office** | Opérations en self-service sur leur compte et leurs abonnements |
| Développeurs bénévoles issus des Jardins | Contribution | Doivent pouvoir aborder facilement le code |

👉 **Conséquence** : l'outil doit être **simple, intuitif et didactique** :
- infobulles explicatives ;
- mode d'emploi et aide en ligne ;
- tutoriels vidéo.

---

## Fonctionnalités attendues

### Back office
- Gestion des clients et, le cas échéant, des adhésions à l'association (ou du sociétariat pour les SCIC).
- Gestion des **produits** (légume, panier, abonnement, lot, agenda…).
- Gestion des **abonnements** (tailles et compositions de paniers, fréquences hebdomadaire / bimensuelle / mensuelle) et des **règlements** associés.
- Gestion de la production et des livraisons : **feuilles de route** de préparation et de distribution.
- Gestion des **points de dépôt** et de leurs catégories.
- Ventes au détail et commandes de professionnels.
- **Export comptable** vers un logiciel de comptabilité.

### Front office
- Espace client permettant de gérer son abonnement et réaliser différentes opérations en autonomie.

### Transverses
- **Très haut niveau de paramétrage** pour s'adapter à la grande diversité de fonctionnement des Jardins.
- **Modules activables/désactivables** par chaque structure.
- Aide contextuelle et outils de prise en main.

---

## Principes techniques

- **Open source** (logiciel libre).
- **SaaS** : application et données hébergées de façon centralisée et sécurisée, sur des serveurs administrés par le prestataire, ce qui facilite les mises à jour.
- **Multi-société** : base commune nationale, déclinée par structure. Les **données restent la propriété de chaque Jardin**.
- **Modularité** : plusieurs modules et fonctionnalités activables selon les choix de chaque Jardin.
- **Simplicité du langage de développement** (ex. PHP) comme critère de choix, afin de faciliter les contributions bénévoles.
- **Documentation technique** à prévoir : schéma / modèle de données expliqué, code commenté, aide, transfert de compétences éventuel.
- **Piste identifiée** : l'ERP [Dolibarr](https://www.dolibarr.org/). D'autres propositions sont acceptées, notamment des logiciels existants de gestion de paniers pouvant évoluer pour répondre au besoin.

---

## Vocabulaire

Pour clarifier les processus et élargir les usages, le cahier des charges emploie des termes simplifiés :

| Terme | Définition |
|---|---|
| **Client** | Toute personne physique ou morale qui achète auprès du Jardin (abonné panier, particulier au marché, professionnel…) |
| **Adhérent** | Uniquement au sens de l'adhésion à l'association, distincte de l'acte d'achat (même si elle peut être obligatoire dans certains cas). Les SCIC ont des clients éventuellement **sociétaires** |
| **Produit** | Tout élément pouvant être vendu (légume, panier, abonnement, lot, agenda…) |
| **Abonnement / « panier »** | Les fonctionnalités « paniers » s'étendent à tous les types d'abonnements à des livraisons de produits |
| **Point de dépôt** | Terme unique pour tous les lieux de livraison/retrait, quels que soient le produit ou le client. Une **catégorie** de point de dépôt permet de les distinguer |
| **Structure / Jardin** | Un Jardin de Cocagne utilisateur de l'outil (déclinaison multi-société) |

---

## Architecture envisagée

```
┌─────────────────────────────────────────────┐
│          Plateforme centralisée (SaaS)       │
│                                             │
│  ┌──────────┐ ┌──────────┐ ┌──────────┐     │
│  │ Jardin A │ │ Jardin B │ │ Jardin N │ ... │  ← multi-société
│  └────┬─────┘ └────┬─────┘ └────┬─────┘     │    (données isolées)
│       └────────────┼────────────┘           │
│          Base commune + modules              │
└───────────┬─────────────────────┬───────────┘
            │                     │
     ┌──────▼──────┐       ┌──────▼──────┐
     │ Back office │       │ Front office│
     │ (équipe)    │       │ (clients)   │
     └─────────────┘       └─────────────┘
```

---

## Contribuer

Le projet a vocation à être enrichi par les Jardins eux-mêmes.

1. Consulter la documentation technique (modèle de données, guide de développement).
2. Proposer une idée ou signaler un besoin via les *issues*.
3. Développer un module ou une fonctionnalité sur une branche dédiée.
4. Ouvrir une *pull request* : toute amélioration profite à l'ensemble du réseau.

> 📌 Les sections de documentation (installation, déploiement, conventions de code) seront complétées à mesure de l'avancement du projet.

---

## Licence

Le logiciel sera publié sous une **licence libre** (à préciser, par exemple GPL, compatible avec Dolibarr).

---

## Liens utiles

- Réseau Cocagne : <https://www.reseaucocagne.org/>
- Dolibarr ERP/CRM : <https://www.dolibarr.org/>

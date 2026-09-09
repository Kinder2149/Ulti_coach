# Mission 2a — Figer la saison dans Notion : le plan

> À valider par Kinder avant lancement. Une fois validé, ce fichier est la
> référence d'exécution : on avance étape par étape, on coche, on ne dévie pas.

---

## 1. Objectif

Rassembler **au même endroit** tout ce qui existe aujourd'hui en trois formats
séparés (Notion partiel, un Google Doc, 63 pages papier), de façon
**parcourable, filtrable et réutilisable**, pour que :

- Kinder retrouve une séance en 10 secondes et voie la progression d'un thème
  dans le temps ;
- l'archive se **complète d'elle-même** les saisons suivantes ;
- le support générique coachs (Mission 2b) puisse en être extrait sans refaire
  le travail.

**Deux niveaux de saisie, les deux demandés :**

| Niveau | Contenu |
|---|---|
| **Ossature** | **Thème · Niveau · Rang dans la progression** · Phase · Lexique du jour · noms des exos · contrainte du match · **scan en pièce jointe** |
| **Intégral** | + le détail de chaque exercice, les CR, les V+/V−, les systèmes de points, les notes de marge |

L'intégral se relit **scan à l'appui** : Kinder corrige mes erreurs de lecture.

---

## 2. Audit de l'existant

| Source | État |
|---|---|
| **Notion — banque d'exercices** | **109 exercices**. Taguée sur 7 axes. 3 templates de page. Vivante. |
| **Notion — base « Training »** | **Existe déjà. Abandonnée depuis octobre 2024.** 21 entrées (≈18 séances + 3 pages de plan/bilan). Plusieurs sont des **coquilles vides** (tableaux non remplis). Taxonomie déjà en place : 11 thèmes, 5 étiquettes de groupe. |
| **Google Doc de saison** | Chronologie Sept→Juin + base stratégique + vocabulaire. Contient aussi un playbook compétition et des **données nominatives de joueurs → exclus**. |
| **PDF `2025 Training.pdf`** | 63 pages scannées, sans couche texte. ≈40 séances + ≈14 pages de théorie + ≈5 fiches de jeux. **La quasi-totalité n'est pas dans Notion.** |

**Décision : on reprend la base « Training », on ne recrée pas.**
Règle projet : modifier l'existant avant de créer.

---

## 3. Le modèle — 4 bases

```
        ┌──────────────────────────────┐
        │  CONTENU  (Thèmes + Phases)  │  ← le générique, hiérarchique
        └───┬──────────┬───────────┬───┘
            │ parent   │           │
            ▼          ▼           ▼
        (Phases)   EXERCICES    LEXIQUE
            ▲          ▲           ▲
            │          │           │
        ┌───┴──────────┴───────────┴───┐
        │  SÉANCES  (les instances)    │  ← ce qui s'est vraiment passé
        └──────────────────────────────┘
```

### 3.1 — Base **CONTENU** *(à créer)*

Thèmes **et** phases dans une seule base auto-référencée : le découpage est
récursif chez Kinder (Le Cut → 6 phases → « cut 1 » → 3 types d'appels).

| Propriété | Type | Valeurs |
|---|---|---|
| Nom | title | |
| Type | select | Thème · Phase · Sous-phase |
| Parent | relation (self) | |
| Sous-éléments | relation (self, inverse) | |
| Ordre | number | position dans le parent |
| Mois de référence | select | Septembre → Juin |
| Face de jeu | select | Attaque · Défense · Transverse |
| Objectif | text | en une phrase |
| Exercices | relation → Exercices | **au niveau Phase, pas Thème** |
| Lexique | relation → Lexique | |
| Séances | relation ← Séances | (auto) |

**Corps de page** : PPA (info / décision / action) · critères de réussite ·
cue moteur s'il existe · variables + / − typiques · miroir défensif ·
`[À COMPLÉTER] erreurs classiques`.

### 3.2 — Base **SÉANCES** *(base « Training » reprise)*

| Propriété | Type | Note |
|---|---|---|
| Nom | title | convention §6 |
| **Thème** | relation → Contenu | la clé de tri principale — *à créer* |
| **Niveau** | select | **Débutant · Hétérogène · Confirmé** — remplace le nom du club — *à créer* |
| **Rang** | number | **position dans la progression Thème × Niveau** (1, 2, 3…) — *à créer* |
| Phase visée | relation → Contenu | *à créer* |
| Étiquettes | multi-select | **existe** — conservée telle quelle, non affichée dans les vues |
| Thèmes | multi-select | **existe** — conservé pour ne pas casser les 18 entrées |
| Date | date | **existe** — **facultative**, conservée quand elle est lisible, jamais reconstituée |
| Lexique du jour | relation → Lexique | *à créer* |
| Exercices | relation → Exercices | *à créer* |
| Source | text | `Notion` ou `PDF p.XX` — *à créer* |
| Saisie | select | Ossature · Intégral · **À valider Kinder** — *à créer* |

**Pas de chronologie par date.** L'archive s'organise en **progressions** :
`Thème × Niveau`, des séances numérotées de 1 à N. C'est ce qui la rend
réutilisable d'une saison à l'autre.
Les dates lisibles sur les feuilles servent **à établir l'ordre**, puis ne sont
plus la clé d'entrée. Aucune date n'est reconstituée ni devinée.

**Pas de nom de club.** Les groupes sont traduits en **niveau de public** —
c'est ce qui rend l'archive générique et lisible par n'importe quel coach :

| Groupe d'origine (feuilles) | Niveau dans l'archive |
|---|---|
| ENS | **Débutant** |
| Gones | **Hétérogène** (niveau moyen, écarts importants) |
| Fenotte · Gones Mixte · coaching équipe | **Confirmé** — *confirmé par Kinder* |

> Cette table de correspondance ne sert qu'à la saisie. **Les noms de clubs
> n'apparaissent nulle part dans Notion.**

Le vocabulaire reste proche de l'axe `Niveau` de la banque d'exercices
(Débutant / Confirmé / Tous niveaux), sans le calquer : « Hétérogène » est le
mot de Kinder et il parle davantage à un coach que « Tous niveaux ».

**Corps de page** — la trame réelle, identique pour toutes :
`THÈME · LEXIQUE · ÉCHAUFFEMENT · EXO 1 (CR / V+ / V−) · EXO 2 (CR / V+ / V−) · MATCH À THÈME` + notes de marge + **scans**.

> **Pas de propriété `Scan`.** Elle avait été créée en E1 puis **supprimée** :
> les scans vivent dans le **corps** de chaque page, une propriété vide qui ne se
> remplirait jamais n'aurait été que du bruit.

### 3.3 — Base **EXERCICES** *(existante — on enrichit)*

Ajouts : `Phases` (relation → Contenu) · `Séances` (relation ← Séances) ·
`Effectif min` / `Effectif max` (number) · `Durée` (number).
Ne **rien** casser des 7 axes existants ni des 3 templates.

### 3.4 — Base **LEXIQUE** *(à créer)*

| Propriété | Type |
|---|---|
| Terme | title |
| Définition | text (1 ligne, dite comme sur le terrain) |
| Catégorie | select : Attaque · Défense · Transverse · Play · Cue moteur |
| Mot imagé | checkbox |
| Introduit dans | relation → Contenu |
| Séances | relation ← Séances |

---

## 3 bis. Identifiants Notion (E1 réalisé)

| Base | Data source ID | Page |
|---|---|---|
| 🧭 Contenu — Thèmes & Phases | `023055ea-eac9-42dd-9e0c-79c5e4eddb49` | b4da524f0ed14ae1ad8bbe8d9c0725c0 |
| 🗣️ Lexique — Vocabulaire commun | `e4e371e9-140e-4263-814c-542d94c7f8e5` | 9da991a0a23a44d49d6e3336fc49f691 |
| Training (Séances) | `2c9bf6a5-ae94-471a-b652-04175d586400` | c71bdb1efdcd4750a426a2ef4bd7569b |
| 🏃 Banque d'exercices | `05666cc3-ea31-497b-b51d-181feb3cbcda` | 4c7153b24e4440108939d5b49f09dea4 |

**Relations câblées :**
`Contenu.Parent ↔ Contenu.Sous-éléments` (auto-référence) ·
`Contenu.Exercices ↔ Exercices.Phases` ·
`Contenu.Lexique ↔ Lexique.Introduit dans` ·
`Séances.Thème ↔ Contenu.Séances du thème` ·
`Séances.Phase visée ↔ Contenu.Séances de la phase` ·
`Séances.Lexique du jour ↔ Lexique.Séances` ·
`Séances.Exercices ↔ Exercices.Séances`

> La propriété `Scan` créée en E1 a été **supprimée** après E6 (voir §3.2).

## 4. Le référentiel CONTENU — **créé (E2)**

**49 entrées** : 10 thèmes · 24 phases · 15 sous-phases (dont 6 plays et la Clam).

**4 phases sans parent, à rattacher par Kinder** : Libérer l'espace · Le jeu long ·
La passe en courbe · La passe en mouvement. Elles apparaissent comme thèmes de
séance dans les feuilles mais ne figurent pas dans la chronologie de saison —
je ne les ai pas rattachées au hasard.

### Détail

#### Thèmes (10, du Google Doc)

| # | Thème | Mois | Face |
|---|---|---|---|
| 1 | Le Cut | Septembre | Attaque |
| 2 | Continuité et prise de décision | Octobre | Attaque |
| 3 | Défense — les bases | Novembre | Défense |
| 4 | Passer devant l'attaque | Décembre | Défense |
| 5 | Défense de zone | Janvier | Défense |
| 6 | Techniques d'attaque | Février | Attaque |
| 7 | Défense individuelle — perfectionnement | Mars | Défense |
| 8 | Défense de zone — perfectionnement | Avril | Défense |
| 9 | Attaque collective — perfectionnement | Mai | Attaque |
| 10 | Travail d'équipe | Juin | Transverse |

### Phases identifiées (première passe — à compléter en cours de route)

**Le Cut** (7) : Le stack → La prise d'info → Le cut 1 → Le changement de
direction → Le cut 2 → La zone de réception → Le recyclage
*Sous-phases du cut 1* : Le Classique · Mettre sur les talons (la Bise) · L'Opportuniste

**Continuité** (5) : Le timing · Le swing · Le recentrage · La passe qui
déclenche · La communication

**Défense — bases** (4) : La position de base (à plat) · Le découpage
5 sec avant / le compte / 5 sec après · Le triangle de vision · La force
(ouvert / fermé)

**Passer devant** (2) : Le pied de pivot défensif · Couper la trajectoire

**Défense de zone** (4) : Le 1er rideau (les chiens) · Le 2e rideau (le phare) ·
Le deep · Le switch

**Attaque de zone** (3) : Le swing des lanceurs · Les pistons · Le crash

*Transverse* : Libérer l'espace · Le jeu long · La passe en courbe · La passe en
mouvement · Le pied de pivot offensif

### Plays *(type = Phase, parent = Techniques d'attaque)*
Praline · Petit Train · Toupie · Rocco · Émeraude · Cavalier · Split Stack
→ **hors périmètre de la formation coachs**, mais dans l'archive.

---

## 5. Le LEXIQUE — **créé (E3)**

**42 termes**, chacun relié à la phase où il est introduit.
Répartition : 18 Attaque · 14 Défense · 4 Transverse · 5 Cue moteur · 1 Play.
**24 sont des mots imagés** — critère coché sur la fiche.

### Termes repris

Déjà extraits et définis dans [METHODE_KINDER.md](METHODE_KINDER.md) §E :
PPA · Appel · Restack/Recyclage · Temps zéro · La passe qui déclenche l'appel ·
Départ à (−1) · Fermé/Ouvert · Swing · Contre-swing · Cavalier · Patate chaude ·
Recentrage · Bise à Mathilde · Courbe qui s'épouse · Poche du fond · Grigri ·
Triangle de vision · Pouvoir du Freeze · Position de crabe · Grand goéland ·
Porte placard · Pied de pivot défensif · Déplacement en banane · Switch ·
Les chiens · Le phare · Disque = lumière · Pistons · Crash ·
No in / No out / No dump / No break · Stack = zone de repos + prise d'info ·
Cut du rugbyman · Compte à 10 · Priorité H/M

**+ le cue moteur** « J'arrive, petit pas, je plante, je tourne et pousse ! »

---

## 6. Conventions

**Nommage des séances** : `Thème — n°X — Phase travaillée (Niveau)`
> ex. `Le Cut — n°4 — Le temps zéro (Débutant)`
Les 18 séances déjà présentes seront **renommées** à cette convention.

**Niveaux** : `Débutant` · `Hétérogène` · `Confirmé`. Les noms de clubs
n'apparaissent nulle part dans l'archive.

**Ordre** : établi à partir des dates lisibles et de la logique de progression,
puis stocké dans `Rang`. Quand l'ordre est incertain, `Saisie = À valider Kinder`.

**Ce que je ne sais pas lire** : les abréviations manuscrites illisibles sont
retranscrites entre crochets `[?]` — jamais devinées, jamais inventées.

**Exclusions fermes** : aucune donnée nominative de joueur, aucune composition
d'équipe, aucun effectif de compétition. Ils restent dans le Google Doc privé.

---

## 7. Inventaire des 63 pages

**Légende** : `S` séance · `T` fiche théorique · `J` fiche de jeu ·
`↳` suite de la page précédente

| p. | Nature | Contenu | Date (tri) | Niveau |
|---|---|---|---|---|
| 1 | J | Master Mind | — | — |
| 2 | J | Les Petits Chevaux | — | — |
| 3 | J | Échauffement — prépa physique intégrée (5 ateliers) | — | — |
| 4 | J | Pense-bête échauffement (3 phases) | — | — |
| 5 | **S** | Défense sur le porteur + Clam — **Débutant/Expert** | 18/01/24 | Hétérogène |
| 6 | T ↳ | La Clam — théorie | | |
| 7 | **S** | Défense porteur + Clam + Iron Man — *note météo* | 25/01/24 | Hétérogène |
| 8 | ↳ | Situation de match | | |
| 9 | ↳ | Exercice n°2 / La Clam (p2 du 18/01) | 18/01/24 | Hétérogène |
| 10 | **S** | Défense sur le stack — Triangulation, la force, Exo1 *Ressenti* | ? | ? |
| 11 | ↳ | Exo2 mise en situation · Exo1.2 Ressenti (+) | | |
| 12 | T | Défense orientée | — | — |
| 13 | T | Force Side — schémas | — | — |
| 14 | **S** | Fenotte Training — objectifs, idées | ? | Confirmé ? |
| 15 | ↳ | Recentrage / Long de ligne + **Tips** | | |
| 16 | **S** | Fenotte — Demo Boiss, recentrage, Conti de Royan, match 2v2 | ? | Confirmé ? |
| 17 | ↳ | Bloqué long de ligne, Cavalier, match à thème | | |
| 18 | **S** | Back — Handler/Middle/Mixte, wall | 20/03/25 | Confirmé ? |
| 19 | **T+S** | **LE CUT — changement de direction, théorie complète** | ? | Hétérogène |
| 20 | **T** | **3 types d'appels** — Classique / Talons / Opportunistes | — | — |
| 21 | **S** | La continuité — comprendre le timing | 02/05/24 | Hétérogène |
| 22 | ↳ | Rotation des postes, exos de passes | | |
| 23 | **S** | Échauffement plots couleur, Exos Bases | 05/09/24 | Hétérogène |
| 24 | **S** | Mouvement des joueurs — Sapin, Situation | 08/04/25 | Débutant |
| 25 | **S** | La passe en mouvement — Conti Royan, Flèches | 08/10/24 | Débutant |
| 26 | **S** | **Nb de présents → circuit d'ateliers / de contraintes** | 18/03/25 | Débutant |
| 27 | **S** | Circuit, minimum 2 par poste | 06/05/25 | Débutant |
| 28 | **S** | Parlons Force = Ouvert / Fermé | 15/10/24 | Débutant |
| 29 | T | Split Stack | — | — |
| 30 | T | Toupies (4 phases) | — | — |
| 31 | T | Cavalier | — | — |
| 32 | T | Émeraude | — | — |
| 33 | **S** | Bac à sable — déplacement dans l'espace, **adaptation par plots** | 25/03/25 | Débutant |
| 34 | **S** | Middle PPA / Handler / Def / Tactique — **Pouvoir du Freeze** | 09/02/26 | Confirmé ? |
| 35 | **S** | Zones de formes différentes, communication déf | 19/01/26 | Hétérogène |
| 36 | **S** | Le jeu long (attaque + défense) | 05/01/26 | Hétérogène |
| 37 | T | Défense — carte mentale Nov-Déc | — | Hétérogène |
| 38 | **S** | Passer devant la défense — pied de pivot défensif | 08/12/25 | Hétérogène |
| 39 | **S** | Défense orientée | 24/11 (25) | Hétérogène |
| 40 | **S** | Défense individuelle — à plat | 17/11 (25) | Hétérogène |
| 41 | **S** | Base défense — à plat | 10/11 (25) | Hétérogène |
| 42 | **S** | Expliquer la défense, état basique — *une bonne déf* | 03/11 (25) | Hétérogène |
| 43 | ↳ | Exo1 −5 sec avant · Exo2 5 sec après | | |
| 44 | **S** | La passe en courbe | 13/10 (25) | Hétérogène |
| 45 | **S** | Le Cut — gain de temps, forme de cut | 06/10 (25) | Hétérogène |
| 46 | **S** | Continuité / Swing / Communication | 02/10 (25) | Hétérogène |
| 47 | ↳ | Recentrage handler + **séance 30/10** | 30/10 (25) | Hétérogène |
| 48 | **S** | Continuité / prise de décision | 29/09 (25) | Hétérogène |
| 49 | **S** | Prise d'info pour cutter | 25/09 (25) | Hétérogène |
| 50 | **S** | Le cut — **temps zéro** | 22/09 (25) | Hétérogène |
| 51 | **S** | Le cut — Exo1 l'information, Exo2 le cut | 18/09 (25) | Hétérogène |
| 52 | **S** | Le cut | 15/09 (25) | Hétérogène |
| 53 | **S** | Le cut *(2e feuille même date — à vérifier)* | 15/09 (25) | Hétérogène |
| 54 | **S** | Le cut — prise d'infos | 11/09 (25) | Hétérogène |
| 55 | ↳ | Passe à 10 spécial + match à thème | | |
| 56 | **S** | Le cut / prise de décision — Flèches, L'Arbre, **auto-positionnement** | 01/09 (25) | Hétérogène |
| 57 | **S** | Libérer l'espace — L'Arbre | 12/11 (25) | Débutant |
| 58 | **S** | Le Stack (recyclage) | 05/11/25 | Débutant |
| 59 | **S** | Stack to cut — **5 formes de bon cut** | 08/10 (24) | Débutant |
| 60 | **S** | Le Stack | 01/10 (24) | Débutant |
| 61 | **S** | La passe en mouvement | 24/09 (24) | Débutant |
| 62 | ↳ | Prise d'information — Exos 1 et 2 | | |
| 63 | **S** | Base passe + démarquation | 11/09 (24) | Débutant |

**Décompte : ≈40 séances · 14 pages de théorie · 5 fiches de jeux · 9 pages de suite.**

> La colonne *Date* de ce tableau ne sert qu'à **ordonner** les séances dans leur
> thème. Elle n'est pas reprise comme clé dans Notion.

---

## 8. Le déroulé — 7 étapes

| # | Étape | Livrable | Validation |
|---|---|---|---|
| **E1** ✅ | Créer les bases **Contenu** et **Lexique** · ajouter les propriétés manquantes à **Séances** et **Exercices** · câbler les relations | Structure vide et cohérente | Kinder ouvre Notion et valide la structure **avant** tout remplissage |
| **E2** ✅ | Peupler **Contenu** : 10 thèmes + ≈30 phases + les plays | Le référentiel générique | Kinder valide le découpage en phases |
| **E3** ✅ | Peupler **Lexique** : ≈35 termes définis | Le glossaire du club | Kinder corrige les définitions — ce sont **ses** mots |
| **E4** ✅ | **Ossature** des ≈40 séances + upload des scans + renommage des 18 existantes | Archive parcourable et filtrable | Kinder vérifie dates et thèmes |
| **E5** ✅ | **Intégral**, par lots chronologiques de ~8 séances | Le détail complet | **Kinder relit chaque lot, scan à côté** |
| **E6** ✅ | Relier Exercices ↔ Phases · créer les exercices du répertoire absents des 109 | Le lien qui n'existe nulle part | Kinder valide les rattachements |
| **E7** | Passe finale : trous, `[?]`, incohérences | Liste des points ouverts | Kinder tranche |

**Ordre voulu** : ossature **complète d'abord** (E4), intégral ensuite (E5).
Raison : Kinder voit la vue d'ensemble et corrige les dates/thèmes **tôt**,
avant qu'on ait investi 40 saisies détaillées sur une structure fausse.

**Rythme** : une étape à la fois, testée avant la suivante.
E5 avance **par lots**, jamais d'un bloc.

---

## 8 bis. Bilan E4 + E5 — **fait**

**39 séances** dans la base Training, toutes en **ossature + intégral + scan**,
toutes marquées `Saisie = À valider Kinder`.

| Progression | Séances |
|---|---|
| Le Cut — Hétérogène | 8 |
| Le Cut — Débutant | 6 |
| Continuité — Hétérogène | 5 |
| Continuité — Débutant | 1 |
| Continuité — Confirmé | 2 |
| Défense — Hétérogène | 5 |
| Défense — Débutant | 1 |
| Défense de zone — Hétérogène | 4 |
| Passer devant — Hétérogène | 1 |
| Défense individuelle — Débutant | 2 |
| Attaque collective — Débutant | 2 |
| Techniques d'attaque — Confirmé | 2 |

**4 séances existantes complétées** au lieu d'être dupliquées : les deux séances
Clam de janvier 2024, la Continuité du 02/05/2024 et les Bases du 05/09/2024.
Leur contenu d'origine est conservé sous la retranscription.

**La carte mentale de défense (p.37)** est allée dans la page du **thème**
« Défense — les bases », pas en séance : c'est un document de cadrage.

**Non traité — ce ne sont pas des séances :**
- 9 pages de **théorie pure** : défense orientée (p.12), force side (p.13),
  le cut (p.19), les 3 types d'appels (p.20), split stack (p.29), toupies (p.30),
  cavalier (p.31), émeraude (p.32), la clam (p.6).
  → leur contenu est **déjà versé dans les phases correspondantes** de la base Contenu.
- 4 **fiches de jeux** : Master Mind (p.1), Les Petits Chevaux (p.2),
  prépa physique intégrée (p.3), pense-bête échauffement (p.4).
  → à verser dans la banque d'exercices en **E6**.

## 8 ter. Bilan E6 — **fait**

**~40 rattachements exercice ↔ phase** et **13 exercices créés**.

Créés (absents de la banque, présents dans les séances) :
Master Mind · Les Petits Chevaux · Morpion · Demo BOISS · La Boussole ·
Le T en relais · Jeu des 4 zones · Frisbee lumière · Ressenti (suivi de cut) ·
La Clam (jeu de chat par zones) · Le Cavalier · La Fleur ·
Duel attaque / défense annoncé.

Chacun porte la fiche au format Kinder et la mention
« fiche reconstruite depuis les notes manuscrites — à compléter ».

### ⚠️ Découverte à trancher par Kinder : la banque est en doublon

**Presque chaque exercice existe en deux exemplaires.** Un jeu porte la propriété
`Type d'exercice` renseignée, l'autre `Éléments Travaillés`. Exemples :
*A babord, Praline, Iron Man, Passe à 10, Conti de Royan, Torero, Toupi, Roco,
Spain, Diago, Iso, Fou, La Q, Braise, Le Train, Attaque des Handler,
Zone Carré, Touche tes pieds* et la quasi-totalité des étirements.

Sur **109 entrées**, il y a vraisemblablement **~55 exercices réels**.

**Je n'ai rien supprimé** — c'est destructif et c'est sa décision.
J'ai **rattaché les deux exemplaires** à la phase : ils apparaissent donc côte à
côte dans chaque phase, ce qui rend les doublons visibles et facilite l'arbitrage.

**Piste de nettoyage** (à valider) : garder l'exemplaire dont la page a du
contenu, reporter les tags manquants dessus, archiver l'autre.

### Autres constats

- **La Flèche existe en 3 versions** : *Fléche*, *La flèche*, *La flèche— Cut*
- **Le nom exact est « Conti de Royan »**, pas « Rayan » — corrigé dans les
  fichiers du projet
- **Plays présents dans la banque mais absents du référentiel** : Spain, Diago,
  Iso, Fou, La Q, Braise, Attaque des Handler, Torero → à ajouter en sous-phases
  si Kinder les utilise encore
- **L'Émeraude et le Split Stack** n'ont pas d'exercice correspondant dans la banque

## 9. Points à trancher avant E1

**Les questions de datation sont annulées** — l'archive s'organise par
progression de thème, pas par date. Ne restent que deux points :

1. ~~Progression par thème ou par thème × groupe ?~~ **Tranché** :
   progression `Thème × Niveau`, sans nom de club.
2. **Les 18 séances déjà dans Notion** (2023-2024) : certaines correspondent-elles
   à des feuilles du classeur ? Si oui on **fusionne**, on ne duplique pas.
   Je fais le rapprochement par thème et contenu au début de E4 et je te
   soumets la liste des correspondances suspectées.

## 10. Risques identifiés

| Risque | Parade |
|---|---|
| **Doublons** entre Notion existant et scans | E4 commence par un rapprochement thème/contenu, soumis à Kinder avant toute création |
| **Mes erreurs de lecture** du manuscrit | Scan attaché à chaque séance · `[?]` sur l'illisible · relecture Kinder par lots |
| **Casser la banque d'exercices** (109 pages, 3 templates) | On **ajoute** des propriétés, on n'en modifie ni n'en supprime aucune |
| **Taille des scans** (22 Mo au total) | Upload page par page ; limites de pièce jointe Notion à vérifier en E1 |
| **Sur-structuration** — 4 bases c'est déjà beaucoup | Aucune 5e base. Les plays sont des phases, pas une base |
| **Chantier sans fin** sur Exercices ↔ Phases | E6 ne traite que les phases des thèmes réellement documentés |

---

## 11. Ce que la 2a produit pour la suite

La Mission 2b (support générique coachs, Artifact web) **s'extrait de cette base**
sans retravail : les thèmes et phases donnent le plan, le lexique donne le
glossaire, le répertoire d'exercices donne l'annexe. Et la formation
(Mission 1) projette cette même page.

# Deck Anki « UPC Annales DFGSM »

Annales de médecine sous forme de cartes Anki.\
Guide d'utilisation et de contribution.

## Avancement

- G2 S1 : en cours
  - Cardiologie
  - Pneumologie
  - Imagerie
  - BCBGM
  - BCT
  - PIR
  - Sémiologie
  - Pharmacologie
- G2 S2 : none
- G3 S1 : none
- G3 S2 : none

## Présentation

Ce deck regroupe des **annales** de DFGSM sous forme de cartes Anki pour se préparer aux examens. Il est **collaboratif en lecture** : tout le monde peut l'utiliser librement ; les modifications sont centralisées sur ce dépôt (voir [Contribuer](#contribuer)).

## Installation

1. Installer Anki (version récente, 23.10 ou plus) depuis [apps.ankiweb.net](https://apps.ankiweb.net).
2. Télécharger le fichier `UPC_Annales_DFGSM.apkg` depuis ce dépôt.
3. Double-cliquer sur le fichier, ou `Fichier > Importer` dans Anki.
4. Pour mettre à jour : réimporter la nouvelle version. Anki met à jour les notes existantes sans réinitialiser votre progression.

Le fichier `UPC_Exemple.apkg` est un deck de **référence** : il contient un exemplaire de chaque type de note (voir [Types de notes](#types-de-notes)). Il n'est utile que pour contribuer ou pour créer vos propres cartes avec les mêmes conventions.

## Types de notes

Tous les types de notes portent le préfixe `UPC` et sont présents en un seul exemplaire dans le deck `UPC Exemple`. Cela garantit des conventions identiques partout. Si un nouveau type de note devient nécessaire ou si des modifications doivent être apporter, merci de le notifier (voir [Contribuer](#contribuer)).

| Type | Usage | Champs |
|---|---|---|
| `UPC Annale` | QRM d'annale (type principal du deck) | `Header`, `P1`–`P5`, `Back Extra` |
| `UPC Basic` | Question / réponse simple | `Front`, `Back` |
| `UPC Cloze` | Texte à trous | `Text`, `Header`, `Back Extra` |
| `UPC Replacement` | Le texte au recto est remplacé au verso | `Header`, `Front`, `Replace_Front`, `Back Extra` |
| `UPC Reversible` | Carte dans les deux sens (ex: mot / définition) | `Forward`, `Reverse` |
| `UPC Image` | Schéma à remplir (occlusion d'image) | `Mask`, `Image`, `Header`, `Back Extra`, `Comments` |

## Le type `UPC Annale` (QRM)

### Structure d'une note

Une note correspond à **une question de QRM**.

| Champ | Contenu |
|---|---|
| `Header` | Thème de la question (ex. « la pyruvate déshydrogénase (PDH) »). |
| `P1` … `P5` | Les propositions de la question (si un champ reste vide, il ne sera pas affiché). |
| `Back Extra` | Source de la question et explication de la correction (affiché au verso). |

### Code couleur : vrai ou faux

La **vérité** de chaque affirmation est codée par la couleur d'une balise `<font>` qui entoure le texte de la proposition :

| Affirmation | Couleur | Balise |
|---|---|---|
| Vraie | 🟢 `#9dff1b` | `<font color="#9dff1b">…</font>` |
| Fausse | 🔴 `#ff445d` | `<font color="#ff445d">…</font>` |

Exemple de champ `P1` (affirmation vraie) :

```html
<font color="#9dff1b">L'ADP est un activateur allostérique de la PDH.</font>
```

> [!WARNING]
> Le template détecte une affirmation vraie en cherchant le code `9dff1b` dans le champ. Il faut donc **toujours** utiliser exactement `<font color="#9dff1b">` et `<font color="#ff445d">`. Les couleurs collées depuis un autre éditeur (par ex. `<span style="color: rgb(157, 255, 27)">`) ne sont pas reconnues : l'affirmation serait comptée comme fausse.

## Colorer rapidement les affirmations (greffon recommandé)

Pour écrire les affirmations `P1`–`P5` sans manipuler le HTML à la main, le deck est construit avec un [greffon de raccourcis de couleurs](https://ankiweb.net/shared/info/2491935955) : on sélectionne le texte dans l'éditeur, puis on appuie sur le raccourci de la couleur voulue.

Pour l'installer : `Outils > Greffons > Obtenir des greffons…`, puis coller le code `2491935955`.

Voici la configuration utilisée (`Outils > Greffons > sélectionner le greffon > Configuration`) :

```json
{
  "keys": [
    ["#9dff1b", "alt+&"],
    ["#ff445d", "alt+é"],
    ["#aaaaaa", "alt+\""],
    ["#ffaa00", "alt+'"],
    ["#00aaff", "alt+("]
  ]
}
```

| Raccourci | Couleur | Usage |
|---|---|---|
| `Alt` + `&` | 🟢 `#9dff1b` | Couleur verte = affirmation **vraie** |
| `Alt` + `é` | 🔴 `#ff445d` | Couleur rouge = affirmation **fausse** |
| `Alt` + `"` | ⚪ `#aaaaaa` | Couleur grise |
| `Alt` + `'` | 🟠 `#ffaa00` | Couleur orange |
| `Alt` + `(` | 🔵 `#00aaff` | Couleur bleue |

> [!NOTE]
> Ces raccourcis correspondent aux touches `1` à `5` de la rangée du haut d'un clavier **AZERTY** (sans Maj). Sur un clavier QWERTY, remplacez-les par `alt+1` à `alt+5`.

Seules les deux premières couleurs ont un sens pour le deck (voir [Code couleur](#code-couleur--vrai-ou-faux)).

### Fonctionnement d'une carte

**Recto.** Le thème et les propositions s'affichent avec une case à cocher. L'ordre des propositions est **mélangé aléatoirement** à chaque passage, pour ne pas apprendre par position. Il faut cocher toutes les propositions que vous pensez vraies.

**Verso.** Les mêmes propositions s'affichent dans le même ordre, avec vos cases, la correction colorée et un **score** calculé selon le barème QRM usuel (nombre d'erreurs = propositions mal cochées ou mal laissées vides) :

| 0 erreur | 1 erreur | 2 erreurs | 3 erreurs ou plus |
|:---:|:---:|:---:|:---:|
| 1 pt | 0,5 pt | 0,2 pt | 0 pt |

Le score est affiché à titre indicatif. Il ne note pas la carte à votre place : choisissez ensuite vous-même le bouton Anki (*Encore*, *Difficile*, *Correct*, *Facile*) selon votre ressenti.

## Tags

Les tags servent à filtrer et à chercher dans le navigateur de cartes d'Anki. Chaque question d'annale porte :

1. **la matière**
2. **l'année** de l'annale ainsi que la session
3. **le niveau de fiabilité de la correction**
4. **le semestre** correspondant

| Tag | Signification |
|---|---|
| `BCBGM`, `Imagerie`, `Pharmacologie`, `Cardiologie`... | Matière. Un sous-tag peut préciser le chapitre (ex. `BCBGM::Cycle_1`). |
| `Annale::G2::S1` | DFGSM2, Semestre 1. |
| `Annale::2023/2024::Session_1` | Année universitaire de l'annale d'origine ainsi que la session. |
| `Annale::Q_Prof` | Question issue d'un cours magistrale ou d'une séance de révision des enseignants. |
| `Annale::Q_ED` | Question issue d'un enseignement dirigé (ED). |
| `Annale::Q_TEAM` | Question issue d'un questionnaire créé par la TEAM de l'ACRP de l'UPC. |
| `Annale::correction::none` | Correction **incertaine** : à vérifier. |
| `Annale::correction::IA` | Correction déterminée par une IA, pas encore relue par un humain. |
| `Annale::correction::valid` | Correction **vérifiée par un humain** (professeur ou étudiant). |

Une carte `none` ou `IA` peut contenir une erreur : ne la prenez pas pour argent comptant, surtout à l'approche de l'examen.\

> [!TIPS]
> Dans le navigateur d'Anki, la recherche `tag:Annale::correction::valid` n'affiche que les cartes vérifiées, et `-tag:Annale::correction::valid` celles qui restent à relire.

## Source et explications (`Back Extra`)

Chaque question d'annale indique **sa source** dans le champ `Back Extra` (origine, session, numéro de la question), éventuellement suivie d'une courte justification de la correction. Exemple :

```text
Annale 2023/2024, session 1 – QCM Q2.
- C'est la pyruvate carboxylase qui transforme le Pyruvate en Oxaloacétate, pas la PDH.
```

## Contribuer

Le deck est maintenu par une seule personne afin de garder des conventions cohérentes. Vous pouvez néanmoins aider :

- **signaler une erreur de correction** en ouvrant une *issue* sur GitHub, avec la matière, l'année et la session, le numéro de la question et, si possible, la source de la bonne réponse (corrigé officiel, enseignant) ;
- **proposer la validation** d'une correction `IA` ou `none` pour la passer en `valid` ;
- **signaler une faute de frappe** ou un problème d'affichage.
- **demander un ajout** comme une question d'annale qui a été oubliée.

Les modifications sont intégrées par le mainteneur, puis une nouvelle version du fichier `.apkg` est publiée.

### Règles pour les cartes ajoutées

1. Utiliser uniquement les types de notes `UPC` (voir [Types de notes](#types-de-notes)).
2. Respecter le code couleur `#9dff1b` / `#ff445d` dans les champs `P1`–`P5`.
3. Renseigner les trois tags : matière, année/session, niveau de correction.
4. Renseigner la source dans `Back Extra`.
5. Une note = une question ; ne pas dupliquer une question déjà présente.

## Limites connues

- Certaines corrections ont été produites par IA ou restent incertaines (tags `IA` et `none`) ; elles sont à vérifier.
- Le deck suppose un Anki récent ; les anciennes versions peuvent mal gérer le template des QRM.
# Deck Anki « UPC Annales DFGSM »

Les annales de médecine (DFGSM) transformées en cartes Anki : tu coches les propositions que tu crois vraies, la carte te corrige et te donne ton score.

## Avancement

| Matière | G2 S1 | G2 S2 | G3 S1 | G3 S2 |
|---|:---:|:---:|:---:|:---:|
| BCBGM | 🟨 | ⬜ | ⬜ | ⬜ |
| BCT | 🟨 | ⬜ | ⬜ | ⬜ |
| Imagerie | 🟨 | ⬜ | ⬜ | ⬜ |
| Sémiologie | 🟨 | ⬜ | ⬜ | ⬜ |
| Cardiologie | 🟨 | ⬜ | ⬜ | ⬜ |
| Pharmacologie | 🟨 | ⬜ | ⬜ | ⬜ |
| Pneumologie | 🟨 | ⬜ | ⬜ | ⬜ |

✅ sessions 1 et 2 intégrées · 🟨 session 1 intégrée · ⬜ rien pour l'instant

## Installation (2 minutes)

1. Installe **Anki** (version 23.10 ou plus récente) : [apps.ankiweb.net](https://apps.ankiweb.net).
2. Télécharge **`UPC_Annales_DFGSM.apkg`** depuis ce dépôt (page *Releases*, ou clique sur le fichier puis sur le bouton de téléchargement).
3. Double-clique sur le fichier. Si rien ne se passe : dans Anki, `Fichier > Importer`.
4. Le deck apparaît avec un sous-deck par matière. Toutes les cartes sont **suspendues** : reprends celles que tu veux travailler (voir [Cartes suspendues par défaut](#cartes-suspendues-par-défaut)).

**Mettre à jour :** télécharge la nouvelle version et importe-la de la même façon. Tes cartes existantes sont mises à jour et **ta progression est conservée**.

## Comment fonctionne une carte

- **Recto :** une question et jusqu'à 5 propositions, chacune avec une case. Coche toutes celles que tu penses **vraies**. L'ordre est mélangé à chaque fois.
- **Verso :** les propositions sont écrites en $\color{#9dff1b}{\textsf{vert si vraies}}$ et en $\color{#ff445d}{\textsf{rouge si fausses}}$. Celles où tu t'es trompé sont $\colorbox{#ffd199}{\color{black}\textsf{surlignées en orange}}$. Tu vois aussi ton score et la source de la question.

Barème (nombre de propositions mal cochées ou oubliées) :

| 0 erreur | 1 erreur | 2 erreurs | 3 erreurs ou plus |
|:---:|:---:|:---:|:---:|
| 1 pt | 0,5 pt | 0,2 pt | 0 pt |

Le score est seulement indicatif : c'est toi qui choisis ensuite *Encore / Difficile / Correct / Facile*.

Le deck contient aussi des questions à réponse courte (question → réponse) et quelques textes à trous ou schémas.

## Fiabilité des corrections

Chaque question porte un tag qui indique à quel point la correction est sûre :

| Tag | Sens |
|---|---|
| `Annale::Correction::valid` | Corrigé officiel de l'annale **et** cohérent avec le cours, donc fiable. |
| `Annale::Correction::ai` | Réponse établie par une IA, cohérente avec le cours, pas (encore) relue par un humain. |
| `Annale::Correction::none` | Correction incertaine ou contestée : lis la ligne **« À vérifier »** au verso. |

Les cartes `IA` et `none` peuvent contenir une erreur, méfie-toi surtout avant l'examen.

## Retrouver des cartes (tags)

Dans Anki, ouvre `Parcourir` et tape dans la barre de recherche :

| Je veux… | Je tape |
|---|---|
| une matière | `tag:Cardiologie` |
| une année | `tag:Annale::2023/2024` |
| uniquement les corrections fiables | `tag:Annale::Correction::valid` |
| enlever les sessions 2 | `-tag:Annale::Session_2` |
| garder celles à relire (donc enlever les "valid") | `-tag:Annale::Correction::valid` |
| les questions qui reviennent sur plusieurs années | `tag:Annale::Frequent` |

Tags d'une question d'annale :
- matière (ex: `Imagerie`)
- année d'étude et semestre (ex: `Annale::G2::S1`)
- année de l'annale (ex: `Annale::2026/2027`)
- session (ex: `Annale::Session_1`)
- correction (ex: `Annale::Correction::valid`)
- (bonus) `Annale::Frequent` si elle a été posée à l'identique (ou presque) au moins 2 années différentes

Une question posée plusieurs années porte un tag par année.

Exemple :\
voici la recherche permettant de ne garder que les annales de Cardiologie de l'année 2025/2026 session 1 qui sont retombées à l'identique au moins une fois.
`tag:Cardiologie tag:Annale::2025/2026 tag:Annale::Session_1 tag:Annale::Frequent`

## Cartes suspendues par défaut

Dans ce deck, **toutes les cartes sont suspendues** à l'import. Une carte suspendue reste dans le deck mais Anki ne te la montre jamais en révision, tant que tu ne l'as pas reprise.

Pourquoi c'est pratique :
- **Tu choisis ce que tu révises.** Tu reprends seulement la matière (ou l'année, la session…) que tu travailles en ce moment, au lieu de recevoir des cartes de toutes les matières en même temps.
- **Pas d'avalanche de nouvelles cartes.** Les cartes ajoutées dans une mise à jour arrivent elles aussi suspendues, elles ne s'invitent pas dans tes révisions sans que tu le décides.
- **Tu combines avec les tags.** Par exemple, tu peux ne reprendre que les corrections fiables (`tag:Annale::Correction::valid`) ou que les questions qui retombent (`tag:Annale::Frequent`).

### Carte ou note ?

Une **note** est une question. Elle peut produire une ou plusieurs **cartes** (une seule pour `UPC Annale`, `UPC Basic` et `UPC Replacement`, une par trou ou par zone pour `UPC Cloze` et `UPC Image`). Suspendre une note suspend toutes ses cartes.

### Reprendre (ou suspendre) des cartes depuis `Parcourir`

1. Ouvre `Parcourir` et tape ta recherche. Ajoute `is:suspended` pour ne voir que les cartes suspendues, par exemple :\
   `tag:Cardiologie is:suspended`
2. Sélectionne les cartes voulues (`Ctrl+A` pour tout sélectionner).
3. Menu `Cartes > Basculer la suspension` (raccourci `Ctrl+J`).

Le même raccourci sert à suspendre et à reprendre. Pour éviter les surprises, sélectionne des cartes qui sont toutes dans le même état : `is:suspended` pour les reprendre, `-is:suspended` pour les suspendre. Les cartes suspendues apparaissent sur fond jaune dans la liste.

Pour agir sur des notes entières plutôt que sur des cartes, clique sur l'interrupteur **Cartes / Notes** en haut à gauche de `Parcourir`, puis fais pareil.

### Suspendre pendant une révision

Si une carte te gêne pendant que tu révises :
- `@` suspend la carte affichée ;
- `!` suspend toute la note.

Tu les retrouves ensuite dans `Parcourir` avec `is:suspended`.

## Signaler une erreur ou demander un ajout

Pas besoin de savoir utiliser Git :

1. Va dans l'onglet **Issues** du dépôt, puis **New issue** (un compte GitHub gratuit suffit).
2. Indique : la matière, l'année, la session, le numéro de question (visible au verso) et, si possible, la bonne réponse avec sa source.
3. Envoie. Les mainteneurs pourront intègrer la correction et mettre à jour le deck.

On peut aussi proposer de **valider** une carte `IA` ou `none`, signaler une faute de frappe ou un problème d'affichage, ou demander une question oubliée.

## Limites connues

- Certaines corrections sont `IA` ou `none` (voir plus haut).
- Les questions dont l'image n'a pas pu être intégrée automatiquement sont ajoutées à la main, donc progressivement.
- Anki trop ancien (avant 23.10) : l'affichage des cartes peut être incorrect.

---

<details>
<summary><b>Pour les mainteneurs et les créateurs de cartes</b> (conventions techniques)</summary>

### Types de notes

Tous portent le préfixe `UPC`. Ne pas en créer d'autres sans en parler.

| Type | Usage | Champs |
|---|---|---|
| `UPC Annale` | Question à choix multiples (type principal) | `Header`, `P1`–`P5`, `Back Extra` |
| `UPC Basic` | Question / réponse courte | `Front`, `Back`, `Back Extra` |
| `UPC Cloze` | Texte à trous | `Text`, `Header`, `Back Extra` |
| `UPC Replacement` | Le texte du recto est remplacé au verso | `Header`, `Front`, `Replace_Front`, `Back Extra` |
| `UPC Image` | Schéma à compléter (occlusion d'image) | `Mask`, `Image`, `Header`, `Back Extra`, `Comments` |

### Champs de `UPC Annale`

Une note = une question. `Header` : l'énoncé, sous forme concise. `P1`–`P5` : les propositions (un champ vide n'est pas affiché). `Back Extra` : la source, puis une éventuelle justification.

Le template affiche déjà « Cochez les propositions vraies. » : l'énoncé ne le répète donc pas et suit un format uniforme `<type> – <thème>`.

| Cas | Format du `Header` / `Front` | Exemple |
|---|---|---|
| QRM (plusieurs réponses) | `QRM – <thème>` | `QRM – Système nerveux cholinergique` |
| QRU (une seule réponse) | `QRU – <thème>` | `QRU – Fréquence cardiaque sur un ECG à vitesse conventionnelle` |
| Énoncé générique, ou figure / ECG sans thème | `QRM` seul, image conservée dessous | `QRM<br><img …>` |
| Vignette clinique | `QRM – ` suivi du contexte complet | |
| Question à réponse rédigée | `QROC – <question>` ou `QROL – <question>` (question intacte) | `QROC – Quel test évalue les fonctions cognitives de façon globale ?` |
| Zonage sur une image | `QZONE – <consigne>`, image dessous | |

Une question à réponse rédigée (QROC, QROL, zonage) sans image va dans `UPC Basic` (`Front` = question, `Back` = réponse). Si l'énoncé n'est pas de type « vrai/faux », le thème est reformulé en groupe nominal (ex : `QRM – Caractéristiques de l'inflammation chronique`).

### Couleurs vrai / faux

La vérité d'une proposition est portée par une balise `<font>` autour du texte :

| Proposition | Balise |
|---|---|
| $\color{#9dff1b}{\textsf{Vraie}}$ | `<font color="#9dff1b">…</font>` |
| $\color{#ff445d}{\textsf{Fausse}}$ | `<font color="#ff445d">…</font>` |

> **⚠️ Attention**\
> Le template cherche le code `9dff1b` dans le champ. Utiliser **exactement** ces deux balises : une couleur collée depuis un autre éditeur (`<span style="color: …">`) n'est pas reconnue et la proposition est comptée fausse.

**Raccourcis de couleur (optionnel).** Le greffon [Color shortcuts](https://ankiweb.net/shared/info/2491935955) (`Outils > Greffons > Obtenir des greffons…`, code `2491935955`) permet de colorer le texte sélectionné au clavier. Configuration utilisée :

```json
{
  "keys": [
    ["#9dff1b", "alt+&"],
    ["#ff445d", "alt+é"]
  ]
}
```

`Alt+&` = vrai, `Alt+é` = faux (touches `1` et `2` d'un clavier AZERTY ; `alt+1` / `alt+2` en QWERTY).

### Format de la source (`Back Extra`)

Une ligne par annale, la plus récente d'abord, séparées par `<br>` :

```text
Annale 2023/2024, session 1 – Histo-Anat-Embryo – QCM Q5
Annale 2020/2021, session 1 – QCM Q8
```

Le type final peut être `QCM`, `QRU`, `QROC`, `QROL`, `ZONAGE` ou `QZONE`. Quand l'annale découpe le sujet en blocs, la section est reprise telle quelle (ex : `Cas clinique 2 – Q3`, `QI 1 – Q1`).

Lignes optionnelles à la suite :

- `Un item de la question avait été neutralisé et n’est pas repris.`
- `À vérifier : <explication du doute>` (obligatoire pour une correction `none`)

Ne pas indiquer dans la note qu'une réponse vient d'une IA : c'est le rôle du tag.

### Règles pour les cartes ajoutées

1. Utiliser uniquement les types `UPC`.
2. Respecter le code couleur dans `P1`–`P5`.
3. Rédiger le `Header` selon le format ci-dessus.
4. Poser les tags :
   - matière (ex: `Imagerie`)
   - année d'étude et semestre (ex: `Annale::G2::S1`)
   - année de l'annale (ex: `Annale::AAAA/AAAA`), un tag séparé par année
   - session (ex: `Annale::Session_1`)
   - correction (ex: `Annale::Correction::valid`)
5. Renseigner la source dans `Back Extra`.
6. Une note = une question, sans doublon (dans la mesure du possible). Si la même question tombe plusieurs années, une seule note avec une ligne par source et un tag par année, plus le tag `Annale::Frequent`. Ce tag se pose aussi sur les deux notes de toute paire de questions identiques ou presque, même non fusionnées.

</details>
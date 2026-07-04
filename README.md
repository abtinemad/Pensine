# Pensine — organiseur de pensée vérifiée

> « J'utilise la Pensine. On a parfois l'impression que l'esprit déborde de trop de pensées. » — Dumbledore

Un système personnel qui transforme des notes jetées en vrac en une mémoire organisée, vérifiée et vivante. Tu déverses tes pensées brutes ; le système les archive telles quelles, les retravaille au propre, contrôle ce qui est contrôlable, fait remonter chaque matin ce qui compte pour la journée, et se nettoie tout seul chaque semaine. Il est conçu pour évoluer avec toi — et pour qu'un jour, si l'organisation te sert vraiment, tu puisses la donner à quelqu'un d'autre.

Ce fichier documente les **principes** et le **journal des évolutions**. C'est la référence à lire pour comprendre le système, l'adapter, ou le partager.

---

## Le problème

Un carnet de notes accumule sans jamais ranger. Une app de tâches oublie le « pourquoi ». Une IA conversationnelle ne se souvient de rien d'un jour à l'autre. Aucun des trois ne distingue *ce que tu penses* de *ce qui est vrai* : ils gobent tout à égalité.

Ce système vise l'inverse : capturer sans friction, ranger sans perdre, et surtout **ne jamais confondre une pensée avec un fait**.

## Principes fondateurs

**Une pensée n'est pas un fait.** C'est la règle qui commande tout le reste. Rien de ce que tu notes n'est traité comme vrai tant que ça n'a pas passé un contrôle — une source pour un fait, l'agenda ou les emails pour un élément personnel. Ce qui n'est pas vérifiable reste une opinion, marquée comme telle. Ce qui est contredit t'est signalé, factuellement, jamais absorbé en silence.

**Trois registres.** La matière brute (registre 1) est ta pensée telle quelle. Les connaissances vérifiées (registre 2) sont ce qui a passé le contrôle, avec sa source. La file d'attente (registre 3) est ce qui est contredit ou invérifiable. Une note ne passe de 1 à 2 que par un contrôle explicite ; dans le doute, elle va en 3.

**Séparer la capture de la synthèse.** La matière première vit dans un fichier *append-only*, verbatim, jamais réécrit — c'est ta voix et ta trace. La version au propre vit dans un autre fichier, réorganisée en permanence par thèmes. Un seul fichier ne peut pas bien faire les deux : la capture est chronologique et figée, la synthèse est thématique et mouvante. Les mélanger recrée le fouillis qu'on voulait quitter.

**Trois vitesses de changement.** Le système est stratifié selon ce qui bouge vite ou lentement :

| Couche | Contenu | Change | Qui l'écrit |
|---|---|---|---|
| Constitution | Le prompt des tâches planifiées : logique de fond, vérification, sécurité | Rarement | Geste conscient (via l'assistant) |
| Conventions | Ton, format, rubriques, préférences, règles évolutives | Souvent | Toi, l'assistant, ou proposé par la consolidation |
| Données | La pensine elle-même (brute + nette) | En continu | Toi (via l'assistant) |

**L'humain garde les lois.** Le système peut réécrire ses conventions et ses données tout seul. Il ne peut pas réécrire sa constitution : ça reste un geste humain. C'est volontaire — un système ne doit pas pouvoir modifier ses propres lois de fond sans qu'une main soit dans la boucle. Il **détecte** qu'il doit changer, il **propose**, tu **décides**.

## Architecture

Fichiers (dans le dossier de travail de l'utilisateur) :

| Fichier | Rôle |
|---|---|
| `pensine-brute.md` | Matière première. Notes verbatim, datées, append-only. Jamais réécrite ni supprimée. |
| `pensine.md` | Version nette. Synthèse par thèmes + les trois registres + journal des briefings + archives. |
| `pensine-conventions.md` | Couche de règles évolutives lue par les tâches à chaque run. **Privée** (contient des valeurs personnelles) : exclue du dépôt via `.gitignore`, vit uniquement en local. |
| `pensine-conventions.example.md` | Squelette public de la couche conventions : mêmes règles, valeurs personnelles remplacées par des placeholders. C'est la version versionnée et partageable. |
| `README.md` | Ce document : principes et journal des évolutions. |

Tâches planifiées :

| Tâche | Cadence | Rôle |
|---|---|---|
| `briefing-matinal` | Chaque jour, 8h | Le flux : agenda du jour, emails à traiter, continuité pensine, apprentissage vérifié. |
| `consolidation-pensine` | Dimanche, 19h | Le fond : nettoyage, cohérence brute↔nette, archivage des fils clos, contrôle des échéances, méta-revue du système. |

## Les flux

**Verser une note.** Tu écris (bouton dans le briefing, ou message direct). La note est archivée verbatim dans `pensine-brute.md`, puis synthétisée au propre dans `pensine.md`. Rien n'est perdu ni déformé.

**Briefing matinal.** Détermine la date, lit les conventions et la pensine, croise avec Google Calendar et Gmail. Sort un message hiérarchisé — ce qui demande une décision aujourd'hui d'abord, l'informatif ensuite — et vérifie au passage les notes brutes non encore traitées.

**Consolidation hebdomadaire.** Fait la maintenance de fond que le briefing ne fait pas : fusionne les doublons, archive les fils clos, remonte les fils qui stagnent pour décision, recoupe les échéances, et prend du recul sur le système lui-même.

**Boucle d'évolution.** Quand la consolidation estime qu'une règle devrait changer, elle l'écrit dans « Propositions en attente de ton feu vert » (dans `pensine-conventions.md`). Tu valides → la règle monte dans « Règles actives » → elle est appliquée dès le lendemain. Le système apprend à se piloter sans jamais forcer la main.

## Adapter le système à quelqu'un d'autre

Ce qui est **personnel** et doit être changé : l'adresse email, les chemins de fichiers, les connecteurs branchés (Calendar, Gmail), le fuseau horaire, la langue, et bien sûr le contenu de la pensine. Ce qui est **réutilisable tel quel** : les principes, la structure des fichiers, les prompts des deux tâches, la couche de conventions.

Pour partager : ne partage jamais tes fichiers privés (`pensine.md`, `pensine-brute.md`, `pensine-conventions.md`) — ils contiennent ta vie et tes valeurs. Le dépôt git ne versionne QUE le **squelette** : ce README, les prompts des tâches (génériques, sans email ni chemins nominatifs), le `.gitignore`, et `pensine-conventions.example.md`. C'est exactement ce squelette qu'on peut donner à quelqu'un d'autre.

## Limites connues

Les tâches planifiées ne tournent que lorsque l'app est ouverte ; si elle est fermée à l'heure prévue, la tâche se lance au prochain lancement. Les skills installés (hors tâches planifiées) ne sont pas modifiables en session — ils passent par les réglages. La vérification vaut ce que valent les sources : le système est prudent par conception, mais un fait « vérifié » reste tributaire de sa source, datée et citée pour que tu puisses recontrôler.

---

## Journal des évolutions

<!-- Le plus récent en haut. Format : ### YYYY-MM-DD — titre, puis quelques lignes. -->

### 2026-07-04 — Durcissement : git, anonymisation, priorisation, carte

Deuxième vague le même jour, après la naissance du système :
- **Sécurité git.** Mise sous dépôt privé GitHub. Token sorti de `.git/config` (fuite locale évitée), authentification via le trousseau macOS (osxkeychain) — plus aucun secret en clair. Le push depuis l'environnement de l'assistant n'est plus possible : modèle acté « l'assistant édite et commit, l'utilisateur pousse » (commande d'une ligne, sans clé à saisir).
- **Anonymisation + purge d'historique.** Historique git réinitialisé (un seul commit propre) pour effacer les valeurs personnelles déjà poussées. Prompts des tâches neutralisés (« l'utilisateur », chemins en `~/`), email et nom d'utilisateur retirés des fichiers versionnés.
- **Conventions privatisées.** `pensine-conventions.md` exclu du dépôt (la consolidation y réécrit chaque semaine des valeurs sensibles) ; squelette public `pensine-conventions.example.md` versionné à la place.
- **Priorisation du focus à deux niveaux.** Bande URGENTE pilotée par les dates (court-circuite tout), puis le reste classé par catégories déduites de la brute. Leviers manuels `pinned`/`frozen`, poids modifiables.
- **Carte pensine enrichie dans le briefing.** Le widget de fin de briefing devient une carte à deux actions : verser une note, ou préparer la commande de sauvegarde GitHub.
- Règle de format ajoutée : pas de bloc `<run-summary>` dans la sortie.

### 2026-07-04 — Naissance du système

Point de départ : un unique `pensine.md` mélangeant note brute et rangement, entretenu par un briefing matinal quotidien.

Évolutions du jour, dans l'ordre :
- Séparation **brute / nette** en deux fichiers. La matière première verbatim quitte `pensine.md` pour `pensine-brute.md` (append-only). `pensine.md` devient la version retravaillée par thèmes.
- Le briefing matinal apprend à lire les deux fichiers : il scanne la brute pour les notes non traitées, vérifie, et n'écrit que dans la nette.
- Création de la **consolidation hebdomadaire** (dimanche 19h) : maintenance de fond, méta-revue, séparation nette entre ce qui est appliqué et ce qui requiert décision.
- Création de la **couche de conventions** (`pensine-conventions.md`) : règles évolutives lues à chaque run, avec une boucle proposition → feu vert → règle active. Formalisation du modèle à trois vitesses (constitution / conventions / données).
- Création de ce **README**.
- Consolidation du système dans `~/Documents/pensine/`, tâches re-pointées, et mise sous **git** : dépôt privé `<ton-compte>/Pensine`, données (`pensine.md`, `pensine-brute.md`) exclues via `.gitignore`. À partir d'ici, git tient l'historique réel des évolutions ; ce journal reste le récit lisible.

Proposition en attente (déposée dans les conventions) : quand ≥ 3 projets actifs, faire remonter chaque matin un seul projet-focus plutôt que la liste complète.

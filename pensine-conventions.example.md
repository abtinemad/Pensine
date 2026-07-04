# Pensine — conventions (EXEMPLE / SQUELETTE)

> ⚠️ Ceci est le **modèle public** de la couche conventions. Le fichier réel, `pensine-conventions.md`,
> contient des valeurs personnelles (santé, finances, noms de projets) et est **exclu du dépôt** via `.gitignore`.
> Ce squelette documente la STRUCTURE et les règles génériques, sans aucune donnée privée.
> Pour l'adopter : copie ce fichier en `pensine-conventions.md` et remplis les placeholders `<…>`.

> Couche de règles ÉVOLUTIVE qui pilote le comportement du briefing matinal et de la consolidation.
> Séparation des vitesses : le prompt des tâches (la « constitution ») change rarement ; ce qui bouge
> souvent — ton, format, rubriques, préférences — vit ici. Éditable librement.
>
> Boucle d'évolution : la consolidation hebdomadaire dépose ses recommandations dans « Propositions
> en attente de ton feu vert ». Tu valides → elles montent dans « Règles actives ». Les tâches lisent
> ce fichier au début de chaque run et l'appliquent. En cas de divergence de FORMAT/TON/RUBRIQUES avec
> le prompt, ce fichier prime ; pour la LOGIQUE DE FOND (vérification, registres, sécurité), le prompt fait foi.

---

## Règles actives
<!-- Appliquées à chaque run. Format : - [YYYY-MM-DD] <règle>. -->

- [YYYY-MM-DD] Ton : partenaire de pensée, pas assistant. Concis, direct. Ce qui demande une décision/action passe avant l'informatif. Frustration → analyse stratégique ou structure logique, jamais réassurance générique.
- [YYYY-MM-DD] La matière brute n'est jamais gardée dans la nette : elle vit uniquement dans `pensine-brute.md` (verbatim, append-only). La nette ne contient que du retravaillé.
- [YYYY-MM-DD] Quand ≥ 3 projets actifs, le briefing fait remonter UN seul projet-focus (l'arbitrage du jour), pas la liste complète — la pensine arbitre, elle n'inventorie pas.
- [YYYY-MM-DD] Toute entrée « Candidature / interview » sans date planifiée ni événement agenda associé est signalée comme « action non planifiée » à chaque consolidation — c'est là qu'un projet meurt en silence.
- [YYYY-MM-DD] Le focus du matin suit la section « Priorisation & classement du focus » : niveau 1 = bande URGENTE (toute échéance datée, court-circuite le reste, plus proche en tête) ; niveau 2 = le reste classé par catégories déduites de la brute, ordre intra-catégorie au barème de signaux. Leviers manuels (pinned/frozen) priment sur tout. Le briefing affiche le focus + « pourquoi lui ».

## Préférences de format
<!-- Comment les sorties sont mises en forme. -->

- Sections courtes, pas de préambule ni de conclusion bavarde. Une seule ligne de synthèse à la fin.
- Emails : distinguer nettement « requiert une réponse » de « pour information » ; agréger les newsletters/notifications en une ligne.
- Astreinte / garde : alerte distincte si elle tombe dans les 48 h.
- [YYYY-MM-DD] Ne JAMAIS émettre de bloc `<run-summary>…</run-summary>` dans la sortie : il s'affiche en clair et pollue le briefing. Le widget pensine reste le tout dernier élément, rien après.

## Priorisation & classement du focus
<!-- Comment le briefing ordonne les projets/tâches et choisit LE focus du jour. Deux niveaux : (1) bande URGENTE pilotée par les dates ; (2) le reste classé par catégories déduites de la brute. Leviers manuels au-dessus de tout. Tout est éditable ; un changement s'applique au run suivant. -->

**Leviers manuels (priment sur tout, même l'urgent) :**
- `focus:pinned =` (vide) — force le focus sur ce projet jusqu'à retrait.
- `focus:frozen =` (vide) — sort ce(s) projet(s) du classement (pause assumée, pas d'archivage).

**Niveau 1 — URGENT (piloté par les dates).** Toute tâche ou projet portant une échéance datée (confirmée par l'agenda ou posée explicitement) entre dans la bande urgente, classée par proximité — date la plus proche en tête. C'est la seule chose qui court-circuite le reste. S'il existe au moins un item urgent, le focus du matin = tête de la bande urgente.

**Niveau 2 — LE RESTE, par catégories.** Ce qui n'a pas de date est regroupé par catégorie thématique **déduite du contenu de la brute**, pas une taxonomie figée : les catégories émergent des thèmes récurrents et sont renommées / fusionnées / scindées à mesure que la brute évolue (entretenu à la consolidation). Dans une catégorie, l'ordre suit le barème de signaux ci-dessous.

**Catégories inférées — état actuel (révisable) :**
- **<Catégorie pro / obligations>** — <thèmes professionnels : travail, négociation, obligations>.
- **<Projets personnels>** — <tes projets nommés>.
- **<Contrainte-cadre>** — <ex. santé, échéance irréversible qui commande la fenêtre>.

**Barème de signaux (ordre intra-catégorie, et focus quand rien n'est urgent ; poids modifiables) :**
- Cadre / contrainte structurante : **+2** à ce qui doit être bouclé AVANT une échéance irréversible.
- Débloquant amont (débloque d'autres projets) : **+2**.
- Action faisable seul maintenant : **+1** ; en attente d'un tiers : **−1**.
- Mort silencieuse (entrée « action non planifiée ») : **+1** par tranche de 7 j d'inaction.
- Anti-négligence : **+1** si pas mis en focus depuis ≥ 5 j.

**Focus quand aucun item n'est urgent :** tête de la catégorie la plus sollicitée par le cadre du moment, choisie au barème.

**Tie-break déterministe :** échéance la plus proche → plus anciennement non-focus → ordre alphabétique.

**Sortie du briefing :** le focus + une ligne « pourquoi lui » (bande urgente, ou catégorie + signal dominant), pour que l'arbitrage reste auditable et contestable.

## Propositions en attente de ton feu vert
<!-- La consolidation dépose ici ses recommandations. Tu valides → elles montent dans « Règles actives ». Format : - [YYYY-MM-DD | proposé par X] <règle + raison>. -->

_(vide)_

## Journal des évolutions
<!-- Daté : quelle règle a changé et pourquoi. Le plus récent en haut. Décrire l'évolution du SYSTÈME, sans donnée personnelle. -->

- YYYY-MM-DD : création de la couche de conventions. Système à trois niveaux — constitution (prompts des tâches) / conventions (ce fichier) / données (pensine brute + nette).

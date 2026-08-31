# Décisions binôme — M6-B2 (À COMPLÉTER)

> **À remplir avant de coder.** Les briques forment une chaîne (feedback →
> stockage → jointure → réentraînement → promotion) : figer les contrats est ce
> qui vous permet d'avancer à deux en parallèle sans vous bloquer.

## Contrats d'interface (à figer en premier)

```text
Feedback   : {request_id: str, true_label: 0|1, comments: str|None}
Stockage   : table feedbacks(request_id PK, true_label, comments,
             created_at, used_for_training=0)
Comptage   : GET /feedback/count → {"count": int, "new": int}
Retrain    : python scripts/retrain.py --min-feedback N → exit 0
Promotion  : decide_promotion(candidate: dict, production: dict)
             → PromotionDecision(promote: bool, reason: str)
```

Modifications apportées à ces contrats en cours de route : _…_

## Trigger de réentraînement

**Seuil retenu : _200 ?_** — justification : _…_

**On compte** : _les feedbacks non consommés (`used_for_training = 0`)_ —
pourquoi pas le total ? _…_

⭐ Second déclencheur « ou dérive confirmée » (bonus) : _traité / non traité_ —
si traité, quelle fonction de M6-B1 est appelée ? _…_

## Politique de promotion

| Paramètre | Valeur retenue | Justification |
|---|---|---|
| Métriques critiques | _…_ | _…_ |
| Plancher de qualité | _…_ | _…_ |
| Tolérance de régression | _…_ | _…_ |
| Gain minimum exigé | _…_ | _…_ |

**Pourquoi le recall de la classe défaut est-il contraignant ?**
_(que coûte à Pyrenex un dossier en défaut prédit comme remboursé ?)_ — _…_

**Pourquoi F1 macro plutôt que l'accuracy ?**
_(quel est le taux de défauts dans les données ?)_ — _…_

## Politique de doublon sur les feedbacks

| Cas | Réponse retenue | Justification |
|---|---|---|
| `request_id` inconnu | _…_ | _…_ |
| Même `request_id`, même label | _…_ | _…_ |
| Même `request_id`, label différent | _…_ | _…_ |

## Résultat de notre exécution

**Décision obtenue** : _PROMOTE / REJECT_

| Métrique | Production | Candidat | Écart |
|---|---|---|---|
| f1_macro | _…_ | _…_ | _…_ |
| recall_default | _…_ | _…_ | _…_ |
| roc_auc | _…_ | _…_ | _…_ |

**Ce qu'on en conclut, en une phrase défendable devant Sophie Léger** : _…_

**Chemin de rejet démontré ?** _oui / non_ — comment : _…_

## RGPD

_… les feedbacks contiennent-ils de la PII ? …_

## Point de mi-parcours (jeudi 17h)

- État des briques : _…_
- **Switch des rôles** — qui reprend quoi : _…_

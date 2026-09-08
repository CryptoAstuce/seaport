# Chapitre 11 — Zones et ordres restreints

La zone est le point d'extension du protocole. Elle est nommee dans l'ordre et recoit deux privileges : annuler les ordres qui la designent, et autoriser les ordres de type restreint.

`contracts/interfaces/ZoneInterface.sol` decrit le contrat attendu. En 1.6, la zone est consultee deux fois : `authorizeOrder` avant l'execution, `validateOrder` apres. Chaque appel doit renvoyer le selecteur de la fonction comme valeur magique, sinon l'ordre est rejete.

`reference/lib/ReferenceZoneInteraction.sol` orchestre ces appels et construit le `ZoneParameters` transmis, ou l'on retrouve l'empreinte de l'ordre, l'appelant, les articles reellement depenses et recus, le `zoneHash` et l'`extraData`.

Le double appel est ce qui rend les verifications d'apres coup possibles : une zone peut constater l'etat final des soldes, pas seulement l'intention declaree.

`contracts/zones/PausableZone.sol` donne un exemple complet : son controleur peut annuler des ordres, executer des ordres restreints et suspendre d'un coup tous les ordres qui la designent, sans toucher aux autorisations de jetons.

`docs/ZoneDocumentation.md` liste d'autres usages : plafonds de prix, quotas par collection, blocage d'articles signales.

[Chapitre suivant : ordres de contrat](12-ordres-de-contrat.md)

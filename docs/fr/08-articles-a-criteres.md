# Chapitre 8 — Articles a criteres

Un article a criteres decrit un ensemble de jetons acceptables plutot qu'un jeton precis. C'est ce qui permet une offre du type « j'achete n'importe quel jeton de cette collection ».

Le champ `identifierOrCriteria` contient alors une racine de Merkle construite sur les identifiants acceptes. Une racine a zero signifie que tout identifiant convient.

Au moment du remplissage, l'appelant fournit des `criteriaResolvers`. Chacun designe un ordre, un cote, un indice d'article, l'identifiant retenu et sa preuve d'inclusion.

`reference/lib/ReferenceCriteriaResolution.sol` traite ces resolveurs. `_applyCriteriaResolvers` verifie que la cible est bien un article a criteres, appelle `_verifyProof` si la racine est non nulle, puis remplace le type et l'identifiant de l'article.

`_isItemWithCriteria` sert au controle final : apres resolution, plus aucun article a criteres ne doit subsister, sinon l'appel echoue.

Une limite decoule du modele : les criteres restent lies a un seul contrat de jetons, et tous les identifiants d'un meme article partagent le meme montant.

[Chapitre suivant : les voies d'execution](09-voies-d-execution.md)

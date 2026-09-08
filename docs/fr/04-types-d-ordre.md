# Chapitre 4 — Les types d'ordre

Le champ `orderType` combine trois preferences independantes et donne les valeurs de l'enumeration utilisee partout dans le code.

`FULL` contre `PARTIAL` decide si l'ordre accepte un remplissage partiel. Avec `PARTIAL`, chaque montant doit rester divisible par la fraction demandee, sans reste.

`OPEN` contre `RESTRICTED` decide de l'autorisation. Un ordre ouvert peut etre execute par n'importe qui. Un ordre restreint doit etre execute par l'emetteur ou la zone, ou bien recevoir l'accord de la zone via un appel a `authorizeOrder` puis `validateOrder`.

`CONTRACT` designe un cas a part : l'ordre n'est pas signe, il est fabrique au moment de l'execution par un contrat qui repond a `generateOrder`, puis confirme par `ratifyOrder`. C'est l'objet du chapitre 12.

Ces preferences se lisent dans `reference/lib/ReferenceOrderValidator.sol`, notamment dans `_doesNotSupportPartialFills`, et dans `reference/lib/ReferenceZoneInteraction.sol` pour le volet restreint.

Un meme carnet d'ordres peut melanger librement ces types dans une seule transaction.

[Chapitre suivant : hachage et signature](05-hachage-et-signature.md)

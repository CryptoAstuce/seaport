# Chapitre 3 — Anatomie d'un ordre

Un ordre reunit onze composants, decrits dans `docs/SeaportDocumentation.md`.

L'`offerer` fournit tous les articles offerts. La `zone` est un compte secondaire facultatif, detaille au chapitre 11. L'`offer` et la `consideration` sont les deux listes d'articles.

Un article porte un `itemType`, un `token`, un `identifierOrCriteria`, un `startAmount` et un `endAmount`. Les articles de `consideration` ajoutent un `recipient`.

Les six valeurs d'`itemType` sont `NATIVE`, `ERC20`, `ERC721`, `ERC1155`, puis `ERC721_WITH_CRITERIA` et `ERC1155_WITH_CRITERIA`. Pour ces deux dernieres, `identifierOrCriteria` ne designe plus un jeton precis mais une racine de Merkle.

`startTime` et `endTime` bornent la periode d'activite de l'ordre. `zoneHash` transporte 32 octets libres a destination de la zone. `salt` fournit l'entropie qui rend l'empreinte unique.

`conduitKey` choisit la source des autorisations : le hachage nul signifie que l'emetteur a approuve Seaport directement.

Enfin, `counter` doit correspondre au compteur courant de l'emetteur ; c'est le levier d'annulation en masse decrit au chapitre 6.

[Chapitre suivant : les types d'ordre](04-types-d-ordre.md)

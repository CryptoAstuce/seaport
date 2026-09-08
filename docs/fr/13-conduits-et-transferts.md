# Chapitre 13 — Conduits et transferts

Un conduit est un contrat intermediaire qui detient les autorisations de jetons a la place de Seaport.

`reference/conduit/ReferenceConduitController.sol` en gere le cycle de vie. `createConduit` deploie un conduit a adresse deterministe a partir d'une cle dont les vingt premiers octets doivent etre ceux du createur. `updateChannel` ouvre ou ferme les canaux, c'est-a-dire les contrats autorises a declencher des transferts. La propriete se transfere en deux temps, par `transferOwnership` puis `acceptOwnership`.

`reference/conduit/ReferenceConduit.sol` execute. `execute`, `executeBatch1155` et `executeWithBatch1155` ne sont ouvertes qu'a un canal ouvert.

L'interet est la stabilite des autorisations : un utilisateur approuve le conduit une fois, et les versions successives de Seaport peuvent etre branchees comme canaux sans nouvelle approbation.

Cote transferts, `reference/lib/ReferenceExecutor.sol` aiguille chaque execution selon le type d'article vers `_transferNativeTokens`, `_transferERC20`, `_transferERC721` ou `_transferERC1155`.

Un accumulateur regroupe les transferts qui partagent la meme cle de conduit. `_insert` empile, `_triggerIfArmedAndNotAccumulatable` vide la pile des que la cle change, et `_trigger` envoie le lot en un seul appel au conduit.

`ReferenceReentrancyGuard` encadre le tout et n'accepte les jetons natifs que pendant une execution en cours.

[Chapitre suivant : ordres en lot](14-ordres-en-lot.md)

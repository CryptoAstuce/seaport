# Chapitre 1 — Presentation de Seaport

Seaport est un protocole d'echange pour jetons natifs, ERC-20, ERC-721 et ERC-1155, publie par OpenSea sous licence MIT.

Chaque ordre decrit deux listes. L'`offer` reunit les articles que l'emetteur accepte de ceder ; la `consideration` reunit les articles qui doivent etre recus en echange, chacun avec son destinataire nomme.

Ce decoupage explique la souplesse du protocole : une vente simple, une offre d'achat, un lot, le versement de royalties ou une commission de place de marche s'ecrivent tous avec ces deux memes listes.

Le depot contient deux implementations du meme protocole. `contracts/` assemble la version deployee, tres optimisee, dont le coeur vit dans les paquets `seaport-core` et `seaport-types`. `reference/` contient une reimplementation lisible, sans assembleur, qui sert de reference de comportement.

Les chapitres qui suivent s'appuient surtout sur `reference/`, plus facile a lire, et sur `docs/SeaportDocumentation.md`.

La version etudiee est Seaport 1.6, annoncee dans l'en-tete de `contracts/Seaport.sol`.

Seaport ne detient jamais les articles echanges : il orchestre des transferts entre comptes qui lui ont accorde une autorisation, directement ou via un conduit.

Le contrat ne preleve aucun frais de protocole ; les commissions passent par des articles de `consideration` ordinaires.

[Chapitre suivant : architecture des contrats](02-architecture.md)

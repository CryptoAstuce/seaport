# Chapitre 10 — Fulfillments et executions

Les methodes de groupe demandent un second jeu de donnees : les `fulfillments`, qui indiquent quels articles peuvent etre regroupes en un seul transfert.

`reference/lib/ReferenceFulfillmentApplier.sol` s'en charge. `_applyFulfillment` exige que tous les articles reunis partagent le meme type, le meme contrat de jeton, la meme source d'autorisation cote offre et le meme destinataire cote contrepartie.

Le procede est comptable : les montants des articles vises sont mis a zero et cumules de chaque cote, les deux totaux sont compares, et le reliquat est reinscrit sur le premier article du cote excedentaire. Il en sort une seule `Execution`.

`_aggregateAvailable` joue le meme role pour les methodes « fulfill available », avec des composantes separees pour l'offre et pour la contrepartie.

Apres application, un balayage verifie qu'aucun article de contrepartie ne conserve un montant non nul : rien ne peut rester du.

Les executions dont l'expediteur et le destinataire coincident sont filtrees avant transfert, ce qui evite des mouvements inutiles.

[Chapitre suivant : zones et ordres restreints](11-zones-et-ordres-restreints.md)

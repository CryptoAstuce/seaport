# Chapitre 12 — Ordres de contrat

Introduits en version 1.2, les ordres de type `CONTRACT` mettent la liquidite on-chain au meme niveau que les ordres signes hors chaine.

L'emetteur n'est plus un compte qui signe, mais un contrat qui implemente `ContractOffererInterface`. Seaport l'appelle pendant l'execution.

`generateOrder` recoit l'appelant, le minimum a recevoir, le maximum a depenser et un `context` libre ; il renvoie l'offre et la contrepartie effectives. `ratifyOrder` est appele apres les transferts pour confirmation.

`reference/lib/ReferenceOrderValidator.sol` encadre cet echange dans `_callGenerateOrder` et `_getGeneratedOrder` : la reponse du contrat est decodee prudemment, et l'ordre est rejete si elle sort du cadre demande.

Ces ordres n'ont pas de signature ni de compteur ; leur suivi passe par un nonce propre, lisible via `getContractOffererNonce`.

La documentation insiste sur une limite : un ordre de contrat ne doit pas produire d'articles a criteres a la volee, car l'appelant n'aurait alors aucun moyen de fournir la preuve correspondante.

[Chapitre suivant : conduits et transferts](13-conduits-et-transferts.md)

# Chapitre 5 — Hachage et signature

Un ordre n'existe on-chain que par son empreinte. `reference/lib/ReferenceGettersAndDerivers.sol` la construit en trois temps.

`_hashOfferItem` et `_hashConsiderationItem` hachent chaque article separement, puis `_deriveOrderHash` combine ces empreintes avec les autres champs et le compteur de l'emetteur.

`_deriveEIP712Digest` prefixe le resultat par le separateur de domaine renvoye par `_domainSeparator`, ce qui lie la signature a ce contrat et a cette chaine : une signature valable sur un reseau ne l'est pas sur un autre.

La verification vit dans `reference/lib/ReferenceSignatureVerification.sol`. `_assertValidSignature` accepte trois formes : signature ECDSA classique de 65 octets, forme compacte EIP-2098 de 64 octets, et delegation a un portefeuille contrat via `_assertValidEIP1271Signature`.

Une signature n'est pas toujours necessaire. Si l'emetteur appelle lui-meme la fonction de remplissage, ou s'il a prealablement enregistre l'ordre par `validate`, la verification est passee.

C'est aussi ce raccourci qui cree la subtilite decrite au chapitre 15 sur les portefeuilles EIP-1271.

[Chapitre suivant : compteur et annulation](06-compteur-et-annulation.md)

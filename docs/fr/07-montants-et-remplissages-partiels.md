# Chapitre 7 — Montants et remplissages partiels

Un article porte deux montants, `startAmount` et `endAmount`. Quand ils different, le montant reel est interpole lineairement entre `startTime` et `endTime`.

`_locateCurrentAmount`, dans `reference/lib/ReferenceAmountDeriver.sol`, calcule la moyenne ponderee du temps ecoule et du temps restant, puis divise par la duree. Un drapeau `roundUp` decide du sens de l'arrondi : les articles dus au vendeur arrondissent vers le haut, ce qui evite qu'un arrondi favorise l'appelant.

C'est ce seul mecanisme qui produit les encheres anglaises et hollandaises, sans code specialise.

Le remplissage partiel se superpose a cela. L'appelant fournit une fraction `numerator/denominator` ; `_getFraction` l'applique et refuse tout resultat non entier.

`_applyFraction` combine les deux etapes : la fraction est appliquee aux deux montants avant l'interpolation, de sorte que la divisibilite ne depende pas de l'heure de remplissage.

Si la fraction demandee depasse ce qui reste, elle est reduite au reste disponible plutot que de faire echouer l'appel. `_greatestCommonDivisor`, dans `ReferenceOrderValidator`, garde la fraction stockee sous forme reduite.

[Chapitre suivant : articles a criteres](08-articles-a-criteres.md)

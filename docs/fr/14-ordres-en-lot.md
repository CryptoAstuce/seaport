# Chapitre 14 — Ordres en lot

La signature en lot, ajoutee en version 1.2, permet de creer plusieurs ordres avec une seule signature.

La charge signee est un arbre de Merkle typé EIP-712 : la racine est un `BulkOrder`, les feuilles sont des `OrderComponents`. L'utilisateur ne signe que la racine, mais chaque ordre reste ensuite remplissable independamment.

Les contraintes d'EIP-712 imposent exactement 2^N feuilles, avec N entre 1 et 24. Un lot de neuf ordres doit donc etre complete par des ordres vides, non remplissables, dont le seul role est de donner la bonne forme a l'arbre.

La signature transmise au remplissage concatene la signature ECDSA de 64 ou 65 octets, un indice sur trois octets, puis jusqu'a vingt-quatre preuves de 32 octets. Une signature valide mesure entre 99 et 836 octets.

Seaport decoupe lui-meme cette chaine, ce qui permet a l'appelant de traiter une signature de lot exactement comme une signature simple.

Le cout n'est pas nul : environ 4 000 unites de gaz pour un arbre de hauteur un, puis 700 de plus par niveau. La documentation conseille des ordres courts et renouveles plutot que des lots larges et durables.

[Chapitre suivant : limites et perimetre](15-limites-et-perimetre.md)

# Chapitre 15 — Limites connues et perimetre de ce parcours

La documentation du depot consacre une section entiere aux limites du protocole ; en voici les principales.

Les jetons a prelevement au transfert faussent les montants, puisque tout est calcule en memoire avant les transferts. Le contournement recommande est un ordre restreint dont la zone verifie les soldes apres coup.

Un destinataire hostile peut bloquer un ordre ou en gonfler le cout, par une fonction de repli couteuse ou un crochet de reception. Emballer les jetons natifs en WETH en cas d'echec fait partie des remediations evoquees.

Les pourboires ajoutes a la volee par l'appelant peuvent etre remplaces par un frontrunning ; seule une zone ou une offre entierement depensee protege contre cela.

Un ordre deja valide par `validate` ou partiellement rempli saute la verification de signature : un portefeuille EIP-1271 dont la signature est devenue invalide doit annuler explicitement l'ordre.

Enfin, les signatures de lot supposent une signature ECDSA de 64 ou 65 octets, ce qui exclut les signatures de comptes contrats plus longues.

Perimetre de ce parcours : rien n'a ete installe, compile, deploye ni execute. Aucun test n'a ete lance, aucune transaction envoyee. Ces chapitres decrivent ce que le code source dit faire, en renvoyant aux fichiers. Pour verifier par vous-meme, le depot fournit une suite Foundry et une suite Hardhat, decrites dans le `README` racine.

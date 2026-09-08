# Chapitre 6 — Compteur et annulation

Seaport offre deux facons d'annuler, et elles ne coutent pas la meme chose.

`cancel` annule des ordres precis. L'appelant doit etre l'emetteur ou la zone de chaque ordre, et doit fournir les parametres complets de l'ordre : annuler un ordre prive le rend donc public.

`incrementCounter` annule d'un coup tous les ordres signes avec le compteur courant. Le code se lit dans `reference/lib/ReferenceCounterManager.sol`.

Le detail interessant est que le compteur ne s'incremente pas de un. Depuis la version 1.2, il saute d'une valeur quasi aleatoire derivee du dernier hachage de bloc.

La raison est defensive : avec un compteur serie, un utilisateur pouvait etre amene a signer un lot d'ordres valables pour le compteur courant et pour les suivants. Un saut large rend un seul appel suffisant pour tout neutraliser.

Un ordre deja partiellement rempli garde son statut ; le compteur agit sur les empreintes futures, pas sur l'etat deja ecrit.

[Chapitre suivant : montants et remplissages partiels](07-montants-et-remplissages-partiels.md)

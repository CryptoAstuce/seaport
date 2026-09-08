# Chapitre 9 — Les voies d'execution

`reference/ReferenceConsideration.sol` expose quatre familles de fonctions de remplissage, du cas le plus contraint au plus general.

`fulfillBasicOrder` couvre les six trajets courants, de `ETH_TO_ERC721` a `ERC1155_TO_ERC20`. L'ordre doit tenir dans un moule strict : un seul article offert, pas de criteres, montants fixes, emetteur destinataire du premier article de contrepartie. En echange, l'appel est court et peu couteux. La variante `fulfillBasicOrder_efficient_6GL6yc` existe uniquement pour obtenir un selecteur commencant par des octets nuls.

`fulfillOrder` et `fulfillAdvancedOrder` acceptent n'importe quel ordre. Seaport construit implicitement un ordre miroir dont l'appelant est l'emetteur. La variante avancee ajoute la fraction a remplir, les resolveurs de criteres et un champ `extraData`.

`fulfillAvailableOrders` et sa variante avancee traitent un groupe d'ordres et ignorent silencieusement ceux qui sont annules, expires ou deja remplis, au lieu de faire echouer le lot.

`matchOrders` et `matchAdvancedOrders` n'ont pas d'appelant beneficiaire : Seaport verifie seulement que les envies coincident entre les ordres fournis.

[Chapitre suivant : fulfillments et executions](10-fulfillments-et-executions.md)

# Chapitre 2 — Architecture des contrats

`contracts/Seaport.sol` est un contrat presque vide : il herite de `Consideration` et se contente de fixer son nom et de recevoir l'adresse du `ConduitController` au deploiement.

Toute la logique est empilee par heritage, une couche par responsabilite. La version lisible de cette pile se lit dans `reference/` : `ReferenceConsideration` expose les fonctions publiques, puis viennent `ReferenceOrderCombiner`, `ReferenceOrderFulfiller`, `ReferenceOrderValidator`, `ReferenceExecutor`, `ReferenceCriteriaResolution`, `ReferenceZoneInteraction` et les briques de bas niveau.

Chaque couche ne connait que celle du dessous : le combinateur d'ordres appelle le remplisseur, qui appelle le validateur, qui appelle le verificateur de signature.

`ReferenceConsiderationBase` fixe au deploiement les valeurs immuables : separateur de domaine EIP-712, empreintes de types, adresse du controleur de conduits, code de reference des conduits.

Les structures partagees sont declarees a part, dans `seaport-types` pour la version deployee et dans `reference/lib/ReferenceConsiderationStructs.sol` pour la version lisible.

Cette separation entre orchestration, validation et transfert revient dans tous les chapitres suivants.

[Chapitre suivant : anatomie d'un ordre](03-anatomie-d-un-ordre.md)

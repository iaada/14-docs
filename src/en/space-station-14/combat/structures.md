# Structures

This document covers structures, structural damage, and structure damage modifier sets. A "structure" is any entity which accepts the `Structural` damage type, and are typically (but not always) static entities like walls, machines, and furniture. They're never items. Structures should be themed as solid objects that predominantly remain in one place.

## Structural Damage

Structural damage is used make a damage source extra effective against the environment separated from its effectiveness against players and mobs. This type of damage has no basis in reality, but serves to carve out a niche for certain weapons and to help the very large and strong station degrade proportionally to its small and squishy inhabitants. This damage type should be used sparingly and purposefully. It belongs on thematic entities like a fire axe, or as part of events which target the station like meteors.

## Structure Health

The amount of damage a structure can take before it's gets destroyed (it's health) should always be considered relative to similar entities. If it's a "strong" wall, it should have more health than a wall, and if it's a "weak" wall it should have less. But when there's a strong similarity in visual appearance and gameplay utility, it's likely the entities should share the same health value. Small deviations aren't likely to make a meaningful difference, and limiting the number of unique values reduces maintenance burden. Damage resistances can be leaned on to create the small differences between slightly different entities.

A simple hierarchy of health between different structures is as follows: `Partial Tile < Full Tile` and `Furniture < Barrier < Machine < Door < Wall`. The first set is obvious, following the expectation that smaller things are weaker. The second set requires a bit more explanation.

Furniture is the weakest of the bunch due to being simple decorations and set dressing. The absence of furniture is acutely felt but not meaningfully important and represents the beginning of the station's degradation. Next is "barriers", mainly windows. These are weak but not completely trivial to destroy, acting as obstacles for petty vandals but entry points for serious criminals.

Machines are not airtight and so their destruction is less catastrophic. However, they're afforded more health than windows because they need a larger range to support malfunctions. A machine not working right is more interesting than its outright destruction and this is better accomplished when the machine can take some hits.

Finally, doors are weaker than walls. Any room that's meant to be entered has a door and that door is intuitively an entry point. Breaching a room through a door is the expected and natural path, and its health reflects as much. Walls being big, dense hunks of metal or other materials are naturally the strongest of the bunch.

## Damage Resistance

Structures must have a damage modifier set which reflects the material it's made of. In other words, an object made of steel should use the steel modifier set. This makes it easier to understand the resistances of an entity because it's based on a meaningful element of its appearance and composition. When in doubt (such as a steel girder inside a plastic wall), use a modifier set which reflects the appearance.

As much as possible material modifier sets should reflect an intuitive understanding of real world materials. Steel is strong, glass is fragile, wood burns. Players should be capable of estimating the resistances of an entity just by looking at it, and similar materials should have similar resistances to help that understanding. This does not necessarily mean a modifier set should be an exact reflection of reality. For example glass has a high resistance to electrical currents, but if shot with a lightning bolt you'd still expect to see damage. Immunity to damage types should be avoided, relying instead on reductions.

Almost all damage resistances should be handled through flat reductions. Percentage reductions are most impactful against high damage sources, but high damage sources are meant to be effective sources of damage. As a result percentage reductions cause damage numbers to inflate so that the effective damage sources are actually effective. Additionally the amount of damage reduced by percentage sources is variable, making it difficult to fully understand the resistance it provides. These types of resistances should be rare and implemented for a specific reason.

In contrast flat reductions are simple and obvious. No matter the source it will get reduced by a set amount. And unlike percentages, flat reductions are able to completely reduce a source of damage to make a structure feel resilient and weak weapons feel weak. When designing weapons it becomes much easier to establish the strength in relation to its target.

Damage modifier sets are also able to amplify damage taken, and when used to amplify percentages don't be modest. Players should be rewarded for correctly identifying that a certain weapon is better suited to the job. Be cautious when amplifying with a flat modifier, as the flat amount will be added regardless of the actual type of damage being dealt. This should only be done with a very clear intent.
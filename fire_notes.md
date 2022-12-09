# Fire Mechanics

## Two stats to fire weapons

1. Added Burning
   - Structure Burn Damage

2. Added Heat
   - Player Burn Damage

## Ammo and their key stats

| Ammo | Added Burning | Added Heat |
| --- | --- | --- |
| 3C-High Explosive Rocket | 1.75 | 1.75 |
| 4C-Fire Rocket | 3.0 | 3.0 |
| Flamethrower Ammo | 1.0 | 6.5 |
| Flame Ammo | 1.0 | 6.5 |

## Weapons and their key stats

Firing the weapon at the structure will add to the structures "Pre-Mitigation Damage" value. The total value added per ammo spent is listed in the "Burn per ammo" column.

$$ PreMitigationValue = (AmmoAddedBurningValue * WeaponBurningMultiplier)*MaxAmmo $$

| Weapon | Max Ammo | Burning Multiplier | Burn per ammo |
| - | - | - | - |
| Willow's Bane (W) | 55 | 0.2 | 11 |
| "Molten Wind” v.II (C) | 75 | 0.2 | 15 |
| T14 "Vesta" Tankette (C) | 100 | 0.2 | 20 |
| H-19 "Vulcan" (C) | 100 | 0.2 | 20 |
| O'Brien V.130 Wild Jack (W) | 100 | 0.2 | 20 |
| Noble Firebrand Mk: XVII (W) | 150 | 0.6 | 90 |
| Flood Juggernaut Mk. VII (W) | 150 | 0.6 | 90 |

## Entities mitigation values

Every 5 seconds, the structure will take the current "Pre-Mitigation Damage" value and apply the structure types mitigation to the value. The amount removed is shown in the table below.

$$ PostMitigationValue = PreMitigationValue - (PreMitigationValue * MitigationPercentage)  $$

| Entity | Mitigation
| --- | --- |
| Light Vehicles | 0% |
| Tier 1 Tank | 80% |
| Tier 2 Tank | 99% |
| Tier 0 Structure | 0% |
| Tier 1 Structure | 20% |
| Tier 2 Structure | 40% |
| Tier 2 BStructure | 40% |
| Tier 3 Structure | 95% |
| Heavy Build Site | 50% |
| Tier 1 Garrison House | 25% |
| Tier 2 Garrison House | 50% |
| Tier 3 Garrison House | 75% |
| Trench | 95% |

## Fire Intensity Thresholds

The "Pre-Mitigation" value after it has been calculated with the mitigation value gives the "Post-Mitigation" value. This value is the amount of damage done to the health of the structure from the damage over time effect. A fire is self sustaining at Low intensity and will grow in strength independently when the gain rate is greater than the decay rate.

When your character reaches a burn value of 1, you will ignite on fire. The "Character Burn" value represents how much the fire adds to your character burn value at each 5 second tick.

| "Post-Mitigation" value | Character Burn | Fire Damage Gain Rate | Fire Damage Decay Rate | Intensity |
| --- | --- | --- | --- | --- |
| -1 | 0.0 | 0.0 | 0.0 | None |
| 0.0 | 0.15 | 0.5 | 0.5 | Low |
| 8.0 | 0.15 | 2.0 | 0.5 | Medium |
| 16.0 | 0.15 | 3.5 | 0.5 | High |
| 25.0 | 0.25 | 5.0 | 0.5 | Blazing |
| 40.0 | 0.25 | 5.0 | 0.5 | Blazing2 |

### Examples

Colonial Flamethrower against Tier 2 Bunker
$$ PreMitigation = 15 =(1 *0.2)* 75 $$
$$ FireIntensityMedium = 9 = 15 - (15 * 0.4 ) $$

Noble Firebrand Mk: XVII against Tier 2 Garrison House
$$ PreMitigation = 90 = (1 *0.6)* 150 $$
$$ FireIntensityHigh = 22.5 = 90 - (90 * 0.75) $$

## Important factors

The max "Pre-Mitigation Damage" value is currently 200. This means a Tier 3 Structure can only ever reach a medium intensity fire. ( 200 - (200 x 0.95)) = 10

The range of the Character Burn value is currently 6 meters.

A character on fire will take 10 damage per second. You have 100 health so have 10 seconds to extinguish yourself of you will burn to death.

The weather has a multiplier effect on fires of 8.0, we can assume this is for each weather intensity level and that it inversely impacts the "Pre-Mitigation Value" by that factor.

## Water

Water interacts on the "Pre-Mitigation" value that the structure has accumulated either from an ongoing fire that is self sustaining or from a flamethrower that has added to the value. Water however moves the value in the opposite direction.

| Ammo | Added Burning | Added Heat |
| - | - | - |
| Water Bucket Full | 3.0 | 3.0 |
| Water | 2.0 | 6.5 |

## Firefighting tools and their stats

To counter fires we have water buckets which come in crates of 80 and fire trucks which must be modified at a facility. The water bucket can be reloaded twice to have two tosses of water in it and a character typically can hold 8 inventory items. This means a character with a full loadout can remove 30 units from the "Pre-Mitigation" value.

The fire truck has an inventory of 15 which means a single fire truck can remove 525 units from the "Pre-Mitigation" value before running out of reloads.

| Tool | Max Ammo | Burning Multiplier | Burn per ammo |
| - | - | - | - |
| Water Bucket | 2 | N/A | 6 |
| R-12b - “Salva” Flame Truck (C) | 100 | 0.35 | 35 |
| Dunne Dousing Engine 3r (W) | 100 | 0.35 | 35 |

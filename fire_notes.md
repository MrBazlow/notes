# Fire Mechanics

## Ammo and their key stats

| Ammo | Added Burning | Added Heat |
| --- | --- | --- |
| 3C-High Explosive Rocket | 1.75 | 1.75 |
| 4C-Fire Rocket | 3.0 | 3.0 |
| Flamethrower Ammo | 1.0 | 6.5 |
| Flame Ammo | 1.0 | 6.5 |

## Weapons and their key stats

Firing the weapon at the structure will add to the structures "Pre-Mitigation Damage" value. The total value added per ammo spent is listed in the "Burn per ammo" column.

$$ PreMitigationFireValue = (AmmoAddedBurningValue * WeaponBurningMultiplier)*MaxAmmo $$

| Weapon | Max Ammo | Burning Multiplier | Burn per ammo |
| - | - | - | - |
| Willow's Bane (W) | 55 | 0.2 | 11 |
| "Molten Wind” v.II (C) | 75 | 0.2 | 15 |
| T14 "Vesta" Tankette (C) | 100 | 0.2 | 20 |
| H-19 "Vulcan" (C) | 100 | 0.2 | 20 |
| O'Brien V.130 Wild Jack (W) | 100 | 0.2 | 20 |
| Noble Firebrand Mk: XVII (W) | 150 | 0.6 | 90 |
| Flood Juggernaut Mk. VII (W) | 150 | 0.6 | 90 |

## Entities fire mitigation values

Every 5 seconds, the structure will take the current "Pre-Mitigation" burn value and apply the structure types mitigation to the value to create the "Post-Mitigation" burn value. The amount removed is shown in the table below.

$$ PostMitigationFireValue = PreMitigationFireValue - (PreMitigationFireValue * FireMitigationPercentage)  $$

| Entity | Mitigation |
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

## Water


Water interacts on a separate "Pre-Mitigation" extinguish value that each structure has. This value is accumulated from tools which apply extinguishing damage type to the structure such as the ammo types below. As the system is based off the fire system above, the names are similar in nature.

| Ammo | Added Burning | Added Heat |
| - | - | - |
| Water Bucket Full | 3.0 | 3.0 |
| Water | 2.0 | 6.5 |

## Firefighting tools and their stats

To counter fires we have water buckets which come in crates of 80 and fire trucks which must be created at player built facilities. These tools have distinctly different levels of efficacy and may be located in different parts of the tech tree as a result.

The total value added to the "Pre-Mitigation" extinguish value per ammo spent is listed in the "Extinguish per ammo" column.

```math
PreMitigationExtinguishValue = (AmmoAddedBurningValue * WeaponBurningMultiplier)*MaxAmmo
```

| Tool | Max Ammo | Extinguish Multiplier | Extinguish per ammo |
| - | - | - | - |
| Water Bucket | 2 | null | 6 |
| R-12b - “Salva” Flame Truck (C) | 100 | 0.35 | 70 |
| Dunne Dousing Engine 3r (W) | 100 | 0.35 | 70 |

## Entities water mitigation values

While a "Pre-Mitigation" burning value of 200 means a raging fire on a Tier 1 structure, it means a medium fire on Tier 3 structure. To ensure that the impact of putting out the fire feels consistent with the size of the fire, a separate set of mitigation values are used to calculate the impact of water on the structure; these values are inversely proportional to the fire mitigation values. 

```math
PostMitigationExtinguishValue = PreMitigationExtinguishValue - (PreMitigationExtinguishValue * WaterMitigationPercentage)
```

| Entity | Mitigation |
| --- | --- |
| Light Vehicle | 100% |
| Tier 1 Tank | 100% |
| Tier 2 Tank | 100% |
| Tier 0 Structure | 99% |
| Tier 1 Structure | 66% |
| Tier 2 Structure | 33% |
| Tier 2 BStructure | 33% |
| Tier 3 Structure | 0% |
| Heavy Build Site | 50% |
| Tier 1 Garrison House | 80% |
| Tier 2 Garrison House | 65% |
| Tier 3 Garrison House | 50% |
| Trench | 0% |

## Fire Intensity Thresholds

The Damage value is calculated by subtracting the "Post-Mitigation" extinguish value from the "Post-Mitigation" burn value. This value is the amount of damage done to the health of the structure from the damage over time effect every five seconds. It is also the determining factor for the intensity of the structures fire. A fire is self sustaining at Low intensity and will grow in strength independently when the gain rate is greater than the decay rate, when a fire reaches the Blazing intensity it will have the ability to spread to nearby structures.

| Damage value | Fire Damage Gain Rate | Fire Damage Decay Rate | Intensity |
| --- | --- | --- | --- |
| -1 | 0.0 | 0.0 | None |
| 0.0 | 0.5 | 0.5 | Low |
| 8.0 | 2.0 | 0.5 | Medium |
| 16.0 | 3.5 | 0.5 | High |
| 25.0 | 5.0 | 0.5 | Blazing |
| 40.0 | 5.0 | 0.5 | Blazing2 |

### Examples

Warden Flamethrower against Tier 2 Bunker

```math
PreMitigationFire = 11 =(1 *0.2)* 55
```

```math
PostMitigationFire = 6.6 = 11 - (11 * 0.4 )
```

```math
PostMitigationFire = Damage
```

```math
Damage > 0 \to FireIntensityLow
```

Noble Firebrand Mk: XVII against Tier 2 Garrison House

```math
PreMitigationFire = 90 = (1 *0.6)* 150
```

```math
PostMitigationFire = 22.5 = 90 - (90 * 0.75)
```

```math
PostMitigationFire = Damage
```

```math
Damage > 25 \to FireIntensityBlazing
```

Character with a full water bucket and 8 Water in their inventory putting out the previous Tier 2 Garrison House fire

```math
PreMitigationExtinguish = 30 = (3 * 1) * 10
```

```math
PostMitigationExtinguish = 10.5 = 30 - (30 * 0.65)
```

```math
PostMitigationFire - PostMitigationExtinguish = Damage
```

```math
22.5 - 10.5 = 12
```

```math
Damage > 8 \to FireIntensityMedium
```

A fire truck with one bottle of water is putting out the fire at the Tier 2 Garrison House that the Noble Firebrand Mk: XVII set alight

```math
PreMitigationExtinguish = 70 = (2 * 0.35) * 100
```

```math
PostMitigationExtinguish = 35 = 70 - (70 * 0.5)
```

```math
PostMitigationFire - PostMitigationExtinguish = Damage
```

```math
22.5 - 35 = -12.5
```

```math
Damage < -1 \to FireIntensityNone
```

## Important factors

The max "Pre-Mitigation Damage" value is currently 200. This means a Tier 3 Structure can only ever reach a medium intensity fire.

```math
FireIntensityMedium = 10 = 200 - (200 * 0.95)
```

### Weather

During a Weather event (Snow or Rain), each five second tick will also include a passive increase to the "Pre-Mitigation" extinguish value in a way similar to applying a bucket of water to the structure. There are three tiers of each weather event and the value added increases in a linear fashion.

However weather events will also have higher levels of wind which if a Blazing intensity fire is created will more rapidly spread to other structures nearby.

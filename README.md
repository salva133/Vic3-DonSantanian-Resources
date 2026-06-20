# DonSantanian Resources

A small dependency mod that provides a single, shared set of scripted triggers and effects for my other Victoria 3 mods. Instead of each mod shipping its own copy of the same checks and helpers, they all reference the definitions here.

Everything below depends only on vanilla content, so each entry can be dropped into any mod that loads this one underneath it. The catalogue is grouped by file; every trigger and effect is listed by its exact in-game name so you can search for it and call it directly.

## Triggers

### Geography — state scope (`dsr_geography_triggers.txt`)

Each tests the region of the state in scope against a continent or world-region.

- **`state_is_in_europe`** — Western, Central, Southern, Northern or Eastern Europe, the Balkans, or Russia.
- **`state_is_in_north_america`** — Canada, the Pacific Coast, the Great Plains or the Atlantic Coast.
- **`state_is_in_central_america`** — the Central America region.
- **`state_is_in_south_america`** — Brazil, La Plata, the Andes or Gran Colombia.
- **`state_is_in_americas`** — any North, Central or South American state (combines the three above).
- **`state_is_in_africa`** — the Nile Basin, North, West, Equatorial, East or Southern Africa.
- **`state_is_in_middle_east`** — the Near East, Arabia or Greater Persia.
- **`state_is_in_central_asia`** — the Himalayas or Central Asia.
- **`state_is_in_india`** — North or South India.
- **`state_is_in_east_asia`** — North or South China, Northeast Asia (Manchuria) or Siberia.
- **`state_is_in_china`** — North or South China only (deliberately excludes Manchuria).
- **`state_is_in_southeast_asia`** — Indochina or Indonesia.

### Geography — country scope (`dsr_geography_triggers.txt`)

Each tests the country's **capital** state with the matching state-level trigger (capital check so the trigger is safe before states finish initialising):
**`country_is_in_europe`**, **`country_is_in_north_america`**, **`country_is_in_central_america`**, **`country_is_in_south_america`**, **`country_is_in_africa`**, **`country_is_in_middle_east`**, **`country_is_in_central_asia`**, **`country_is_in_india`**, **`country_is_in_east_asia`**, **`country_is_in_southeast_asia`**, **`country_is_in_china`**.

### Religion (`dsr_religion_triggers.txt`)

- **`is_christian`** — the scope's religion carries the `heritage_christian` trait.
- **`is_jewish`** — the scope's religion carries the `heritage_jewish` trait.
- **`is_muslim`** — the scope's religion carries the `heritage_islamic` trait.
- **`is_abrahamic_non_mohammedan`** — Christian or Jewish heritage (i.e. Abrahamic but not Muslim).
- **`country_is_jewish_nation`** — every primary culture is Jewish-heritage and the state religion is Jewish.
- **`country_is_a_judeo_christian_nation`** — the state religion is of Christian or Jewish heritage.

### Government & politics — country scope (`dsr_country_triggers.txt`)

- **`country_is_recognised`** — not colonial, decentralized or unrecognized.
- **`country_is_non_leftist_republic`** — runs a Corporate State, Presidential or Parliamentary Republic.
- **`country_is_monanarchy`** — holds both the Monarchy and the Anarchy law at once (the combined "monanarchy" shape).
- **`country_has_fascist_government_trigger`** — detects a fascist government by its legal and heraldic silhouette: either a republican facade with an autocratic executive and a fascist coat of arms, or a corporatist autocracy that is not a Germanic ethnostate, non-ethnostate Austria, or a Hispanophone country (those read as other strains of fascism).
- **`is_welfare_state_with_low_legitimacy`** — Old Age Pension plus Worker Protections, Social Security and Workplace Safety funded to level 5, and government legitimacy below 25.

### Ideology availability — country scope (`dsr_country_triggers.txt`)

Each checks the prerequisite technology so an ideology can appear:

- **`is_possible_ideology_fascist`** — `mass_propaganda` researched.
- **`is_possible_ideology_communist`** — `socialism` researched.
- **`is_possible_ideology_anarchist`** — `anarchism` researched.

### Law stance — country scope (`dsr_country_triggers.txt`)

- **`reactionary_stance_on_free_speech`** — interest groups lean above neutral on Outlawed Dissent or State Security.
- **`liberal_stance_on_free_speech`** — interest groups lean below neutral on Outlawed Dissent or State Security.
- **`staunch_multiculturalist`** — interest groups lean above neutral on the Multicultural law.

### Migration — country scope (`dsr_country_triggers.txt`)

- **`country_eligible_as_mass_migration_source_country`** — can have mass migration to ROOT and holds a sizeable culture (over 1000 pops) that shares a heritage or language trait with ROOT's primary cultures.

### Characters (`dsr_character_triggers.txt`)

- **`is_leftist_agitator`** — an agitator with a progressive or socialist ideology.
- **`is_right_wing_agitator`** — an agitator with a reactionary, conservative or monarchist ideology.

### States (`dsr_state_triggers.txt`)

- **`state_is_occupied`** — the state's controller is not its owner.
- **`state_is_occupied_by_root`** — the state is controlled by ROOT.

### Coat of arms (`dsr_coa_triggers.txt`)

Government-shape checks for dynamic coat-of-arms definitions. The plain variants test the country in scope; the `coa_def_*` wrappers test `scope:actor`, as coat-of-arms definition files require.

- **`coa_def_monarchy_trigger`** — `scope:actor` wrapper around vanilla's monarchy coat-of-arms check.
- **`coa_democratic_republic_trigger`** — a non-leftist republic that has a voting franchise.
- **`coa_def_democratic_republic_trigger`** — `scope:actor` wrapper of the above.
- **`coa_undemocratic_republic_trigger`** — a non-leftist republic with no voting franchise.
- **`coa_def_undemocratic_republic_trigger`** — `scope:actor` wrapper of the above.

## Effects

### Country effects (`dsr_country_effects.txt`)

- **`remove_all_economy_buildings_from_country`** — strips every economy building from every state of the country: industry, agriculture, mines, plantations, misc resources, power plants, ports and railways. Leaves auto-managed and non-economic buildings (trade centres, manor houses, financial districts, subsistence, military, government, monuments, canals, construction, company HQs) intact.
- **`deindustrialize_country`** — a leaner strip that removes only military and heavy-industry buildings: barracks, all naval buildings, the chemical / synthetics / steel plants, power plants, the motor / automotive / electrics industries and munition plants.
- **`set_random_governance_principle`** — randomly enacts one Governance Principle (Monarchy, Presidential / Parliamentary Republic, Theocracy, Council Republic or Corporate State).
- **`set_random_distribution_of_power`** — randomly enacts one Distribution of Power, with the Technocracy and Anarchy outcomes pulling in the matching bundle of supporting laws.
- **`decentralize_countries`** — turns every country beyond the top 200 by prestige into a decentralized country. Callable from any scope; leaves the `country_rank` global variable behind.
- **`exile_least_popular_agitator`** — exiles the country's least popular agitator and saves them as `scope:exiled_character` for follow-up script.
- **`country_kill_all_non_primary_pops_in_all_states`** — kills 99% of every non-primary-culture pop in every state, then starts enacting Slavery Banned if slavery is still legal.
- **`collapse_pop_literacy`** — models a literacy collapse, capping pop literacy at 20% across the country, with academics and engineers retained at 60%.
- **`set_default_devout_ig_name`** — restores the base-game default Devout interest-group name from vanilla's religion / culture mapping (e.g. Orthodox Church, Sunni Madrasahs, Anglican Church), falling back to the generic Devout name. Useful for cleanly lifting a custom Devout-name override.

### State effects (`dsr_state_effects.txt`)

- **`add_state_trait_to_region_if_missing`** — parameterized (`STATE`, `TRAIT`) macro that tags a state region with a state trait only when none of its states already carry it. Idempotent, so it is safe to call repeatedly (e.g. from `on_game_started`).
- **`state_kill_all_non_primary_pops`** — kills 99% of every pop in the state whose culture is not a primary culture of the state's root country.
- **`state_kill_acceptance_1_pops`** — kills 10% of the pops of every culture sitting at the lowest acceptance tier (below the status-2 threshold) in the state's root country.

### Dynamic naming effects (`dsr_dynamic_naming_effects.txt`)

Parameterized building blocks for culture-based dynamic state and hub renaming, mirroring vanilla's `evaluate_and_assign_state_hub_dynamic_names` pattern. A consuming mod supplies its own state dispatcher, language trait (`TRAIT`), localization-key suffix (`SUFFIX`) and on_action hooks; the vanilla `no_dynamic_naming` game rule is honoured.

- **`evaluate_and_assign_state_hub_names`** — gate that resets names under the `no_dynamic_naming` rule, otherwise hands over to the consuming mod's dispatcher effect (`ASSIGN_EFFECT`). State scope.
- **`assign_culture_state_hub_names_coastal`** — sets the state name plus city, port, mine, farm and wood hubs when the owner has the trait; resets to vanilla otherwise.
- **`assign_culture_state_hub_names_inland`** — as coastal, but without a port hub.
- **`assign_culture_state_hub_names_hubs_only`** — sets only the mine, farm and wood hubs; the state name and city hub are left untouched.
- **`assign_culture_state_hub_names_coastal_keep_vanilla`** — the coastal variant for states vanilla also renames for other languages: resets only when the owner fails the supplied `VANILLA_NAMES_TRIGGER`, so vanilla's competing branches keep working.
- **`assign_culture_state_hub_names_inland_keep_vanilla`** — the inland keep-vanilla variant of the above.

## Using it as a dependency

This mod does nothing on its own — it is meant to be loaded underneath the mods that depend on it. A mod that uses these triggers and effects must declare the dependency in its `.metadata/metadata.json` and list this mod as a required item on its Steam Workshop page. Because everything is called by its bare name, a consuming mod just references the trigger or effect directly; do not ship a second copy.

## Compatibility

Everything here depends only on vanilla content — state regions `sr:region_*`, discrimination traits, laws, technologies, institutions, country types, buildings, interest-group and culture / religion keys, the `no_dynamic_naming` game rule and vanilla's coat-of-arms triggers — so the library tracks vanilla (currently game version 1.13) and carries no gameplay content of its own.

# DonSantanian Resources

A small dependency mod that provides a single, shared set of scripted triggers and effects for my other Victoria 3 mods. Instead of each mod shipping its own copy of the same checks and helpers, they all reference the definitions here.

## What it provides

- **Geography triggers** — continent / world-region checks at state and country level: Europe, North America, Central America, South America, Africa, the Middle East, Central Asia, India, East Asia, China and Southeast Asia, plus a combined state-level Americas check. State-level triggers test the state's region; country-level triggers test the country's capital.
- **Religion triggers** — heritage checks: Christian, Jewish, Muslim, and Abrahamic-non-Mohammedan, plus the nation-level Jewish and Judeo-Christian checks.
- **Government & politics triggers** — recognised country, non-leftist republic, the combined monarchy-plus-anarchy "monanarchy" shape, fascist-government detection, welfare-state-with-low-legitimacy, ideology-availability (Fascism / Communism / Anarchism, by prerequisite technology), and free-speech / multiculturalism law stances.
- **State & demographic triggers** — occupation checks (occupied at all, or occupied by ROOT), agitator alignment (left-wing / right-wing), and mass-migration source eligibility.
- **Coat-of-arms triggers** — government-shape checks for dynamic coat-of-arms definitions: democratic republic and undemocratic republic, each as a plain country-scope trigger plus the `coa_def_*` actor-scope wrapper used by coat-of-arms files, and a `coa_def_*` wrapper around vanilla's monarchy check.
- **Country effects** — a bulk effect that strips every economy building (industry, agriculture, mines, plantations, resources, power plants, ports and railways) from all states of a country, random Governance Principle / Distribution of Power assignment, decentralizing every country beyond the top 200 by prestige, exiling a country's least popular agitator, and pop-surgery helpers that kill or replace non-primary-culture pops (the country-wide variant also starts enacting Slavery Banned where slavery is still legal).
- **State effects** — tagging a state region with a state trait if missing (idempotent, parameterized), and killing the non-primary-culture pops of a single state.
- **Dynamic naming effects** — parameterized building blocks for culture-based state and hub renaming (coastal / inland / hubs-only layouts, plus keep-vanilla variants for states vanilla already renames for other languages). A consuming mod supplies its own state dispatcher, language trait, localization keys and on_action hooks; the vanilla `no_dynamic_naming` game rule is honoured.

## Using it as a dependency

This mod does nothing on its own — it is meant to be loaded underneath the mods that depend on it. A mod that uses these triggers and effects must declare the dependency in its `.metadata/metadata.json` and list this mod as a required item on its Steam Workshop page.

## Compatibility

Everything here depends only on vanilla content — state regions `sr:region_*`, discrimination traits, laws, technologies, institutions, country types, buildings, the `no_dynamic_naming` game rule and vanilla's coat-of-arms triggers — so the library tracks vanilla (currently game version 1.13) and carries no gameplay content of its own.

# DonSantanian Resources

A small dependency mod that provides a single, shared set of scripted triggers for my other Victoria 3 mods. Instead of each mod shipping its own copy of the same checks, they all reference the definitions here.

## What it provides

- **Geography triggers** — continent / world-region checks at state and country level: Europe, North America, Central America, South America, the Americas, Africa, the Middle East, Central Asia, India, East Asia, China and Southeast Asia. State-level triggers test the state's region; country-level triggers test the country's capital.
- **Religion triggers** — heritage checks: Christian, Jewish, Muslim, and Abrahamic-non-Mohammedan, plus the nation-level Jewish and Judeo-Christian checks.
- **Government & politics triggers** — recognised country, republic and monarchy/anarchy shapes, fascist-government detection, welfare-state-with-low-legitimacy, ideology-availability (Fascism / Communism / Anarchism), and free-speech / multiculturalism law stances.
- **State & demographic triggers** — occupation checks, agitator alignment (left-wing / right-wing), and mass-migration source eligibility.

## Using it as a dependency

This mod does nothing on its own — it is meant to be loaded underneath the mods that depend on it. A mod that uses these triggers must declare the dependency in its `.metadata/metadata.json` and list this mod as a required item on its Steam Workshop page.

## Compatibility

The triggers depend only on vanilla content — state regions `sr:region_*`, discrimination heritage traits, laws, technologies, institutions and country types — so the library tracks vanilla and carries no gameplay content of its own.

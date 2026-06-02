# DonSantanian Resources

A small dependency mod that provides a single, shared set of geography and
religion scripted triggers for my other Victoria 3 mods. Instead of each mod
shipping its own copy of the same continent and religion-heritage checks, they
all reference the definitions here.

## What it provides

- **Geography triggers** — continent / world-region checks at state and country
  level: Europe, North America, Central America, South America, the Americas,
  Africa, the Middle East, Central Asia, India, East Asia, China and Southeast
  Asia. State-level triggers test the state's region; country-level triggers
  test the country's capital.
- **Religion triggers** — heritage checks: Christian, Jewish, Muslim, and
  Abrahamic-non-Mohammedan.

## Using it as a dependency

This mod does nothing on its own — it is meant to be loaded underneath the mods
that depend on it. A mod that uses these triggers must declare the dependency in
its `.metadata/metadata.json` and list this mod as a required item on its Steam
Workshop page.

## Compatibility

The triggers depend only on vanilla state regions (`sr:region_*`) and vanilla
discrimination heritage traits, so the library tracks vanilla and carries no
gameplay content of its own.

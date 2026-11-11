# About this fork

This fork of [PokemonTCG/pokemon-tcg-data](https://github.com/PokemonTCG/pokemon-tcg-data) started when the original paused after 30th Celebration. The original has since resumed with Delta Reign, so this fork merges its changes and keeps its own corrections on top. It keeps the same files and JSON format, so tools that read the original data can read this one.

**Differences from the original:**

- Delta Reign (`me6`, DLR): both repositories added the set separately. This fork merged the original's version, adopted its four corrections, and kept its own data wherever the card images support it: flavor text, empty retreat costs, Adventure Lantern as an Item, Mega Rayquaza Cap without a Mega Evolution rule, the Legendary Stadium rule about combining 2 halves, the Special Energy subtype, and Nidoran ♀ spelled like the rest of the archive. The [merge commit](https://github.com/CDEngineer/pokemon-tcg-data/commit/7ff7795) lists each difference.
- The Standard legality fix for Ascended Heroes and Perfect Order (upstream pull request #623, not merged there).
- The full comparison is on GitHub: [original...fork](https://github.com/PokemonTCG/pokemon-tcg-data/compare/master...CDEngineer:pokemon-tcg-data:master).

**Removed here:** the legacy v1 format. The `v2_to_v1.rb` conversion script no longer runs on current Ruby, and this fork doesn't have the resources to maintain it, so it was removed. The "Version 1 and Version 2 Data" section of the original README below no longer applies; the original repository still has the script.

**How cards are checked:** every new card is checked field by field against official English card images: name, stage, HP, attacks, abilities, rules text, weakness, resistance, retreat, illustrator, rarity, regulation mark, and flavor text. Drafts translated from Japanese or taken from previews are only a starting point. New sets follow the conventions of the newest upstream sets, which leave out Trainer reminder lines.

**Contributing:** pull requests are welcome. Please use official English card text only, checked against card images, and keep the existing format.

This fork is not affiliated with Pokémon, Nintendo, Creatures, GAME FREAK, or the original maintainers. Card text and images belong to their owners. Like the original repository, this fork has no license file.

The original README follows.

---

# Pokémon TCG Data

> [!IMPORTANT]
>
> ## This project is being deprecated
>
> Pokémon TCG Data and the Pokémon TCG API are legacy projects and are no longer recommended for new integrations.
>
> **The Pokémon TCG API is scheduled to be taken offline on March 1, 2027.**
>
> For actively maintained Pokémon TCG data, pricing, price history, graded card data, population reports, image recognition, and support for additional trading card games, please use **[Scrydex](https://scrydex.com)**.
>
> **Scrydex:** https://scrydex.com
> **API Documentation:** https://scrydex.com/docs
>
> Existing data in this repository will remain available for historical and compatibility purposes. Developers currently using the Pokémon TCG API should migrate to Scrydex before March 1, 2027.

---

This repository contains the card data historically used by the [Pokémon TCG API](https://pokemontcg.io/).

The project is now considered legacy. The existing JSON files will remain available for developers who depend on them, but this repository should not be used as the primary data source for new applications.

For current Pokémon TCG data and actively maintained API access, use [Scrydex](https://scrydex.com).

## Scrydex

Scrydex is the actively maintained platform for developers building applications around trading card game data.

In addition to Pokémon, Scrydex supports multiple trading card games and provides access to features including:

* Card and expansion metadata
* Raw card pricing
* Graded card pricing
* Historical price data
* Graded sold listings
* Population reports
* Market trends
* Card image recognition
* Additional TCGs beyond Pokémon

For more information:

* [Scrydex](https://scrydex.com)
* [API Documentation](https://scrydex.com/docs)

## Downloading the Data

The historical JSON data in this repository can still be cloned directly:

```bash
git clone https://github.com/PokemonTCG/pokemon-tcg-data.git
```

You can also download data from the repository's releases.

This repository should primarily be considered a historical or compatibility data source.

Applications that require continuously maintained card data should use the [Scrydex API](https://scrydex.com).

## Pokémon TCG API Deprecation

The [Pokémon TCG API](https://pokemontcg.io/) is being deprecated and is scheduled to be taken offline on **March 1, 2027**.

Existing integrations may continue to function until the shutdown date, but developers should avoid starting new integrations against the Pokémon TCG API.

If your application currently relies on the Pokémon TCG API, please migrate to [Scrydex](https://scrydex.com) before **March 1, 2027**.

New applications should use Scrydex from the start.

## Version 1 and Version 2 Data

Version 1 data is no longer maintained.

The `v2_to_v1.rb` Ruby script is retained for developers who still need to generate the legacy V1 JSON format from V2 data.

To install Ruby:

https://www.ruby-lang.org/en/documentation/installation/

You will also need the `json` gem:

```bash
gem install json
```

To generate the V1 data:

```bash
ruby v2_to_v1.rb
```

The generated card data will be written to:

```text
/cards/en/v1
```

## Contributing

This repository is maintained primarily for historical and compatibility purposes.

Routine card-data updates and new feature development are no longer the focus of this project.

For current data, API access, or support, please use [Scrydex](https://scrydex.com).

## Migrating to Scrydex

If you currently use Pokémon TCG Data or the Pokémon TCG API in an application, please migrate to Scrydex before the Pokémon TCG API shutdown on **March 1, 2027**.

Scrydex provides a maintained API designed for production applications and expands on the original Pokémon TCG API with pricing, historical market data, graded card information, population reports, image recognition, and support for additional trading card games.

Documentation is available at:

https://scrydex.com/docs

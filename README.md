# About this fork

This fork of [PokemonTCG/pokemon-tcg-data](https://github.com/PokemonTCG/pokemon-tcg-data) started when the original paused after 30th Celebration. The original has since added Delta Reign, but it is now deprecated: its README below calls it legacy, and the Pokémon TCG API that it feeds is scheduled to go offline on March 1, 2027. This fork keeps the data going as JSON files: it merges any changes the original still makes, adds new sets, and keeps its own corrections on top, so it has everything the original has plus the fixes below. It keeps the same files and JSON format, so tools that read the original data can read this one; it does not provide an API.

**Corrections in this fork that the original lacks:**

- **Standard legality:** the Standard legality of Ascended Heroes and Perfect Order cards is corrected. The original still has the wrong values (the fix was offered upstream as pull request #623 and not merged).
- **Standard rotations:** the 2025 and 2026 rotations are applied, which the original never did. Cards marked F, G or older no longer list Standard, unless a printing marked H or later reprints them (same name, and for Pokémon the same attacks) or they are basic Energy; 2,824 cards and 19 set entries changed.
- **Illustrators:** every card in Surging Sparks, Prismatic Evolutions, Journey Together and Destined Rivals (`sv8`, `sv8pt5`, `sv9`, `sv10`) has its illustrator, read from the card images. The original has none for these sets.
- **Card fixes:** Arceus LV.X (pl4-94, dpp-DP53) prints "LV.X" without a space; McDonald's 2012 Drilbur (mcd12-8) has its two attacks, which the original merges into one; Ethan's Pichu (sv10-71) and Team Rocket's Chingling (sv10-85) attacks cost one Colorless Energy, not nothing.
- **Delta Reign (`me6`, DLR):** both repositories added the set separately. This fork merged the original's version and adopted the four fields it had right, then checked every remaining difference against the card images. Where the two differ, this fork matches the printed cards:
  - Adventure Lantern (me6-90, me6-126) is an Item; the original lists it as a Pokémon Tool.
  - Mega Rayquaza Cap (me6-100) is a plain Pokémon Tool; the original adds a MEGA subtype and the Mega Evolution ex rule, which the card doesn't print.
  - The six Legendary Stadium halves (me6-94 to me6-99) include their printed rule about combining 2 different halves; the original leaves it out.
  - The three Special Energy cards (me6-132 to me6-134) have the Special subtype and no illustrator, like Special Energy in earlier sets; the original has no subtype and an illustrator of "—".
  - Flavor text is included on the 92 cards that print it; the original has none for this set.
  - Pokémon with free retreat record it explicitly (a retreat cost of 0); the original leaves the field out.
  - Nidoran ♀ is spelled with a space, like the archive's other 15 Nidoran ♀ cards, so Nidorina's evolution still matches across sets.
- The Delta Reign [merge commit](https://github.com/CDEngineer/pokemon-tcg-data/commit/7ff7795) shows each difference, and GitHub shows the [full comparison with the original](https://github.com/PokemonTCG/pokemon-tcg-data/compare/master...CDEngineer:pokemon-tcg-data:master).

**Adopted from pull requests to the original:** the original has not merged these community pull requests, open or closed, so this fork applies them, each as one commit that keeps the contributor as author. Each was checked against card images or the archive first.

- [#612](https://github.com/PokemonTCG/pokemon-tcg-data/pull/612) Fix regulation mark of sv6-226 (evanchiu).
- [#624](https://github.com/PokemonTCG/pokemon-tcg-data/pull/624) Fix me5-115 Mega Chandelure ex: add Stage 2 subtype and Mega Evolution ex rule (M-A-Zinc).
- [#600](https://github.com/PokemonTCG/pokemon-tcg-data/pull/600) Fix Antique Cover Fossil number, add evolvesTo (bbuck), followed by our corrections.
- [#597](https://github.com/PokemonTCG/pokemon-tcg-data/pull/597) Corrected card rarity for rsv10pt5-131 (Archen from White Flare) (JashSK).
- [#598](https://github.com/PokemonTCG/pokemon-tcg-data/pull/598) Corrected rarity for cards zsv10pt5-171 and rsv10pt5-172 (Red Victini from Black Bolt and White Flare) (JashSK).
- [#625](https://github.com/PokemonTCG/pokemon-tcg-data/pull/625) Replace non-breaking spaces in sv1, sv2 and svp card text (M-A-Zinc).
- [#291](https://github.com/PokemonTCG/pokemon-tcg-data/pull/291) Add JSON schemas (serras), data fixes only.
- [#578](https://github.com/PokemonTCG/pokemon-tcg-data/pull/578) Fixing typos in reprinted cards (Cealgair), without the xy9-121 change, followed by our corrections.
- [#616](https://github.com/PokemonTCG/pokemon-tcg-data/pull/616) Added missing artist data for ME3 set (DasMrMr).
- [#552](https://github.com/PokemonTCG/pokemon-tcg-data/pull/552) Add illustrators for Stellar Crown cards (C-Ezra-M).
- [#607](https://github.com/PokemonTCG/pokemon-tcg-data/pull/607) Me1 add artists (CardsOnHudson), followed by our corrections.
- [#611](https://github.com/PokemonTCG/pokemon-tcg-data/pull/611) me2pt5: Update national Pokedex number from 206 to 982 for Larry's Dudunsparce ex (AntoineTurmel).
- [#613](https://github.com/PokemonTCG/pokemon-tcg-data/pull/613) Fix card me2pt5-206 by removing its nationalPokedexNumbers since it's a tool and not Pokémon Hypno (ClementTurmel).
- [#563](https://github.com/PokemonTCG/pokemon-tcg-data/pull/563) Fix missing pokedex no (ajakkes), svp numbers only.
- [#615](https://github.com/PokemonTCG/pokemon-tcg-data/pull/615) Add Basic Energies MEE (mfedatto), followed by our corrections.
- [#548](https://github.com/PokemonTCG/pokemon-tcg-data/pull/548) Added swshp-SWSH299 (Cealgair), followed by our corrections.
- [#481](https://github.com/PokemonTCG/pokemon-tcg-data/pull/481) Add MCD23 for match battle 2023 (tkfnetwork, with Cealgair), followed by our corrections.

**Removed here:** the legacy v1 format. The `v2_to_v1.rb` conversion script no longer runs on current Ruby, and this fork doesn't have the resources to maintain it, so it was removed; the original repository still has the script.

**How cards are checked:** every new card is checked field by field against official English card images: name, stage, HP, attacks, abilities, rules text, weakness, resistance, retreat, illustrator, rarity, regulation mark, and flavor text. Drafts translated from Japanese or taken from previews are only a starting point. New sets follow the conventions of the newest upstream sets, which leave out Trainer reminder lines.

**Contributing:** pull requests are welcome. Please use official English card text only, checked against card images, and keep the existing format.

This fork is not affiliated with Pokémon, Nintendo, Creatures, GAME FREAK, or the original maintainers. Card text and images belong to their owners. Like the original repository, this fork has no license file.

The start of the original README follows, with its deprecation notice; its remaining sections are left out.

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

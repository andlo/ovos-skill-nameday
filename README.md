# Nameday — a design document, not a working skill yet

**Status: idea and sourcing-investigation stage.**

## The idea

"Hvem har navnedag i dag" / "hvornår har Andreas navnedag" - name
days (a name-to-calendar-day mapping, distinct from birthdays) are
a real, actively-celebrated tradition, not a niche curiosity.

## Not Danish-specific - this must be multi-locale from the start

Initial framing treated this as a `da-dk` feature. That was wrong.
Name-day traditions are actively maintained in Denmark, Sweden,
Finland, Poland, the Czech Republic, Hungary, Bulgaria, Greece,
Latvia, Lithuania, Croatia, Slovakia, Slovenia, Romania, and others -
a comparable spread to which languages have a native Wikipedia
vital-articles list in `ovos-skill-wiki-offline`. Some locales
(English-speaking countries, broadly) have no equivalent tradition at
all - that's a real, honest gap to document per-locale, not a bug to
fix, same as "The Spanish gap" in wiki-offline.

## Sourcing

Each country/language maintains its own official or de-facto list
(day → name(s), sometimes several names per day, sometimes a name on
several days). Needs per-locale investigation before building -
likely Wikipedia-based (each language edition tends to have a
"List of name days" article) matching the exact sourcing pattern
`ovos-skill-wiki-offline/data/build_data.py` already solved:
fetch wikitext, extract structured entries, verify against a second
source before trusting completeness. Wikipedia list articles have
already shown drift/inconsistency issues once (see wiki-offline's
"master list vs category tags" and "The Spanish gap" findings) - budget
time for the same kind of verification here, not just a straight
scrape-and-ship.

## Relationship to a possible holidays/calendar skill

Deliberately kept as a **separate** skill from any future
"helligdage" (public holidays) skill, despite both being "calendar
knowledge": holidays can be computed algorithmically per-country via
the `holidays` Python library (no bundled data needed at all), while
name days require an actual bundled per-locale dataset (closer to
wiki-offline's architecture than a calculation). Different data
sourcing, different maintenance burden, different failure modes -
worth keeping the skills' scopes narrow and separate rather than
merging them just because both answer "what's special about today."

## Open questions (resolve before implementing)

- Which locales to launch with in v1 - probably da-dk, sv-se, fi-fi
  as the first batch (matches existing project language familiarity),
  expand from there.
- Multiple names per day, and multiple days per name - how to phrase
  "whose name day is it" vs "when is X's name day" cleanly when either
  can have more than one answer.
- Whether to bundle as one skill with per-locale data files (matches
  wiki-offline/geography's existing pattern) rather than separate
  skills per country.

## Category
**Daily**

## Tags
#nameday #navnedag #calendar #idea #design-doc

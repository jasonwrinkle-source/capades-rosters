# capades-rosters

Roster packs for Flexcapades hypermaps. A roster pack is one small JSON
file holding a group's roster for one map — its DMs and top players as
samples, each with an authored menu blurb — so every member can load the
whole roster in one step instead of passing profiles around one by one.

## The demo pack

`friday-knights.json` is a worked example for Questcapades: a fictional
Friday-night table (Maren, Theo, Priya). Its QR code is
`friday-knights-qr.svg` — print it, post it, scan it: the code opens
Questcapades with the roster attached, and the app loads the three
members into the Samples menu.

## How a pack works

A pack file is named by its slug: `<slug>.json`. The link a group
disseminates is:

    https://<skin>.capades.io/#roster=<slug>

Opening that link loads the pack from the site and saves its entries as
local samples on that member's device (re-opening updates them in
place). The same pack can also travel as a plain file: the app's
Samples menu has **Import roster pack** and **Export roster pack**, so
a group can start with files alone, no hosting anywhere.

Pack shape:

    { "format": "flexcapades-roster", "version": 1,
      "skin": "<skin id, e.g. questcapades>",
      "name": "<pack name>",
      "samples": [ <sample entries> ] }

Each entry is a normal sample: `{kind: "sample", name, about, count,
payload}` — `about` is the member's menu blurb (the hover tip), and
`payload` is a standard profile payload whose ratings key on the
skin's topic ids. Photos do not travel in packs. A pack only loads on
its own skin.

## Getting a pack hosted

Packs in this repo are bridged into the live site by YoBiche (copied to
`hosted/rosters/` in the main repo, shipped with the next deploy) —
the same bridge pattern as capades-skins. Authoring a pack needs no
code: build the roster in the app (save each member as a local sample,
write their blurb, Export roster pack) and commit the exported file
here under its slug, or write the JSON directly.

Whether hosted packs are a Patreon perk (hosted for a group, refreshed
on a cadence) or simply self-serve is Jason's open call — the format
and the app support both, and this repo works either way.

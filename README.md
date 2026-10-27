# rsg-theatre

Theatre Raleur (Saint Denis) stage shows for RSG Framework, rebuilt from Rockstar's `show_nbx_*` scripts.

## Features
- Ticket seller NPC at the theatre ticket fence (ox_target) with a playbill NUI
- Server-scheduled shows (rotation or random) every `Config.ShowInterval` minutes
- Ticket holders near the stage when the show starts get the full performance: curtain opens, performers play the original anim scene, curtain closes
- 14 shows: Can-Can I & II, Big Band I & II, Fire Performer, Fire Dancer, Fire Breather, Snake Dancer I & II, Sword Dancer, Feats of Strength, Escape Artist, Escape from the Noose, Odd Fellows
- NPC audience fills the theatre seats during a show (Rockstar's seat list and Saint Denis population set), configurable with `Config.Audience`
- Multi-part acts play their playlists in sequence, switching as each part ends, like Rockstar's scripts
- `/theatre [showId]` admin command to start a show now
- Theatre door locks added to rsg-doorlock automatically on first start (main doors open, side doors locked)

## Install
1. Drop `rsg-theatre` into your resources and `ensure rsg-theatre` after rsg-core, ox_lib, ox_target, oxmysql and rsg-doorlock.
2. No items needed. Tickets are held server-side (per character) until the holder watches a show.
3. On first start the four theatre door locks are inserted into `rsg_doorlocks` (skipped if a door with the same name already exists). Restart rsg-doorlock once afterwards to load them. `doors.sql` is the same data if you prefer to run it by hand.

## Config
- `Config.TicketPrice`, `Config.TicketCooldown`, `Config.TicketSeller.buyDistance`
- `Config.ShowInterval`, `Config.FirstShowDelay`, `Config.ShowOrder`, `Config.MaxShowLength`
- `Config.Stage`, `Config.AudienceRadius` – ticket holders must be inside this radius when the curtain rises
- `Config.AdminCommand`, `Config.AdminPermission`

## Notes
- If an admin forces a show, the next scheduled show waits until it has finished instead of being skipped.
- Performers and props are spawned locally on each viewer's client, so nothing is networked.
- The Snake and Sword dancer origins aren't set explicitly in their decompiled scripts; they use the shared stage origin. Adjust in config if they stand off-mark.

Support: https://buymeacoffee.com/rexshack

# WORK — unfinished implementation

## Upstream gap review — 29 October 2026

Seven remaining implementation candidates are tracked as UG2–UG8 in
[TODO.md](TODO.md#unfinished-upstreamfork-candidates--reviewed-29-october-2026).
The source limits describe upstream; local inspection below establishes the
missing adapter boundary, not a reproduced multiplayer defect. Recheck the integrated upstream and the latest fork audit before implementation.

| ID | Remaining implementation and current local boundary |
| --- | --- |
| UG2 | prop_stick_sync.cpp::ReplayStick falls back to frozen/static flags and physics-off after a missed trace. PropStickStatePayload carries identity, flags, pose and velocities, without the support identity. Add support/component resolution and destruction cleanup without attaching to a guessed surface. |
| UG3 | prop_stick_sync::ConvergeStuck and prop_wire_parity converge existing flags during other replication paths. Ghezra `70641f091` supplies a toolgun lane reference, but no equivalent host-admitted route is installed here. Add live action authority and final state delivery, preserving native freeze/static distinctions and current hold guards. |
| UG4 | The upstream laptop stabilizes its seat locally. No stabilizeSeat/occupied-chair reservation route was found in our coop controllers. Bind protection to the actual chair, operator and laptop lease; clear it on exit, body/world replacement and disconnect. Receiver-side competing-hold arbitration is already present and does not itself reserve an occupied chair. |
| UG5 | No red-phone ring adapter was found in coop controllers or protocol. Capture the native selected ring/cue and its lifetime; host ownership must not duplicate native client rolls. |
| UG6 | No desk virusEvent adapter was found. Dish precision, server state and power-panel replication cover parts of the aftermath, not the native virus trigger and phase ownership. Map the actual graph before defining its shared effects and join policy. |
| UG7 | download_arm_sync replays native begin; no objectRenderer/lifecrystal-specific birth scope was found in coop. Bind any shared signal output to one host-owned invocation across either arm/birth arrival order, including failed construction and replacement. Preserve personal camera/ending branches. |
| UG8 | Upstream #49 requests runtime 3D-print synchronization even with matching local files. No printer-specific output/content adapter was found in coop prop routes. Establish the actual printed class and mesh initialization, then add canonical birth/content/transform/lifetime and late-join handling. This source report does not establish our package's exact failure or require distributing users' files. |

Source links are attached to each TODO item. Existing event, entity, resource,
mod-integration and physics backlogs remain the owners of overlapping work;
do not duplicate them or import gameplay-only acceptance as implementation.

Development target: **0.9.2164**. [TODO.md](TODO.md) lists priorities.
This file contains implementation work and the constraints needed to finish it.
Checks, completed-change reports and release evidence belong in
[TESTLOG.md](TESTLOG.md).

## Active queue and appliance review — 4 November 2026

The next implementation batch first owns these concrete defects:

- [ ] Q01: initialize a token bucket exactly once even when its first clock is zero.
- [ ] Q02: do not move the refill clock backwards and credit the same elapsed interval twice.
- [ ] Q03: apply a reduced burst ceiling before a same-clock spend.
- [ ] Q04: reject non-finite/negative token budgets instead of admitting a NaN stream.
- [ ] Q05: prevent recursive service of the same pending intent.
- [ ] Q06: own the served payload across occupant reset and native callbacks.
- [ ] Q07: do not pop a successor occupant's head when an old callback returns Done.
- [ ] Q08: do not refund an old Wait into the successor occupant's bucket.
- [ ] Q09: cancel service when its clock callback replaces the queued head.
- [ ] Q10: consume an uncertain callback attempt on exception, without replaying it next tick.
- [ ] Q11: release the service guard on callback/copy/clock exceptions.
- [ ] Q12: keep service admission closed through in-callback queue replacement.

The appliance part owns these individually named repairs:

- [ ] C01: reject coffee press frames with null function/locals.
- [ ] C02: bound the action parameter read by the function frame.
- [ ] C03: refuse unreadable client action frames instead of brewing locally.
- [ ] C04: cancel a client press if key lookup retires its actor.
- [ ] C05: cancel a client send after session/world retirement during key lookup.
- [ ] C06: reject non-ASCII, empty, None and oversized outgoing device keys.
- [ ] C07: reject malformed incoming device keys at the handler boundary.
- [ ] C08: require the installed, running host and a world-ready connected sender at ingress.
- [ ] C09: bind queued presses to the sender's transport generation.
- [ ] C10: clear coffee intents when the installed Session pointer changes.
- [ ] C11: clear them on same-pointer session serial changes.
- [ ] C12: clear them on world changes.
- [ ] C13: clear the coffee intent session pointer at disconnect.
- [ ] C14: clear queued presses at disconnect independently of roster teardown order.
- [ ] C15: refuse a Tick argument belonging to another session.
- [ ] C16: stop the slot drain after a callback retires the host scope.
- [ ] C17: retain the authorized device incarnation through native action preparation.
- [ ] C18: pass the same puppet body that supplied the reach verdict.
- [ ] C19: refuse a recycled puppet incarnation after reach callbacks.
- [ ] C20: refuse a rekeyed/rebound device before native action admission.
- [ ] C21: do not write old action results into successor-session counters.
- [ ] C22: do not clear a successor occupant's wait state after an old callback.
- [ ] C23: expire a press waiting indefinitely for the sender's body.
- [ ] S01: match coffee PRE/POST notes by invocation, not actor address alone.
- [ ] S02: preserve an outer brew/hit note across nested watched calls.
- [ ] S03: reject notes whose actor incarnation changed before POST.
- [ ] S04: reject notes whose UFunction incarnation changed before POST.
- [ ] S05: reject notes from an earlier installed session pointer.
- [ ] S06: reject notes from an earlier same-pointer session serial.
- [ ] S07: reject notes from an earlier world.
- [ ] S08: reject notes after a host/client role change.
- [ ] S09: retire PRE snapshots invalidated by native flag/other-actor reads.
- [ ] S10: consume a POST note before callbacks so duplicate POST cannot publish twice.
- [ ] S11: retain the bag's exact incarnation while capturing PRE amounts.
- [ ] S12: own the POST snapshot across recursive publication.
- [ ] S13: cancel publication when POST maker-flag reads retire the actor.
- [ ] S14: stop the bag branch after maker publication retires the session.
- [ ] S15: do not update new-session publication counters from an old callback.
- [ ] S16: guard the publisher's key read against actor retirement.
- [ ] S17: reject rekeyed actors during publication/retry.
- [ ] S18: keep controller authority through record capture/chunk delivery.
- [ ] S19: retain bounded retry debt for refused guarded publications.
- [ ] S20: drop retry debt whose actor/session/world ownership expired.
- [ ] S21: clear old notes and retry debt on Install context replacement.
- [ ] S22: disable coffee state callbacks immediately at disconnect.
- [ ] S23: bound cancelled-hit diagnostics and distinguish recycled maker addresses.
- [ ] S24: bound class tallies and distinguish recycled class addresses.
- [ ] S25: settle refused coffee state watch registrations once.
- [ ] S26: validate OtherActor frame bounds before reading its pointer.
- [ ] S27: bind awaited client-record admission to the current host/sender/actor scope.
- [ ] W01: guard coffee classification through class lookup and actor replacement.
- [ ] W02: invalidate hasCup offsets on class serial replacement.
- [ ] W03: invalidate hasCoffee offsets on class serial replacement.
- [ ] W04: invalidate coffeeReady offsets on class serial replacement.
- [ ] W05: cancel bag-field reads invalidated during offset resolution.
- [ ] W06: retry missing coffee bool metadata without requiring a new class address.
- [ ] A01: refuse appliance actions when the player parameter write fails.
- [ ] A02: refuse appliance actions when the action parameter write fails.
- [ ] A03: validate the appliance actor incarnation through function lookup.
- [ ] A04: validate the player incarnation through frame preparation.
- [ ] A05: validate class/function incarnations through frame preparation.
- [ ] A06: check the caller's authority immediately before native dispatch.
- [ ] A07: report caller retirement after an attempted native action without replaying it.

These 75 boundaries are queue/bucket and appliance repairs, not wire or package changes.

## Upstream integration in progress

- [ ] UP2: finish semantic review of source integration through upstream
  `4fbf1acf0` (436 graph commits after `ad5315611`; 130 after the previous
  `dc4cd7307` source integration). The code is transferred and builds; the
  review still owns authority and lifetime seams beyond the exercised fixtures.
- [ ] UP4: finish ownership review for merged cord/coffee and coordinate/radio
  tower adapters against existing fork routes and 32-player capacity.
- [ ] UP5: finish prop syncer/swinger handoff review, including parked supports,
  bind-wait replacement, join ordering, hand arbitration and container recovery.
- [ ] UP6: finish Geom Octa authority/effect and Vulkan teardown review across
  device, window and world replacement.

UP1 documentation conflict resolution and UP7 fixture/build verification are
recorded in [TESTLOG.md](TESTLOG.md#integration-error-audit-30-october-2026).
The development DLL uses b2219 and is not a newly qualified release package.
The published fork IDs remain reserved; the renamed HitIntent keeps ID 242,
and the new container request/reply/commit use 264/265/266. The PvP throw nonce,
Kerfur release marker, food state and placement request IDs remain separate.
Source transfer does not add upstream ancestry to Git; no commit was requested.

- [ ] UP8: finish actual upstream history integration. At `2131fa9cc`, the latest
  fork merge has parents `6604633bf` and `f9ad5ef9c`, neither the upstream tip.
  The last common ancestor remains `ad5315611`; Git reports 632 fork-only and
  436 upstream-only commits. A real merge preview against `4fbf1acf0` conflicts
  in 80 paths. Reconcile those changes with the existing fork adaptations and
  record the upstream parent through a genuine merge; do not clear the count
  by declaring unreviewed upstream changes already merged.

## Fork follow-ups — reviewed 4 November 2026

- [ ] Own concurrent disc inserts with exact device occupancy, sender generation,
  admitted eject/output completion and bounded retry/refund state. Ghezra
  `1bc4675d1` demonstrates the race; its fixed-delay, unbounded swap queue is not
  sufficient. Preserve canonical ordering and checked writes.
- [ ] Add host-admitted module purchases separately from level upgrades,
  including exact row, reach, debit/output and duplicate/refusal behavior.
  Ghezra `13b120e67` is a reference; the current module branch still runs locally.
- [ ] Establish personal/shared provenance for transient spawner drops at join.
  Ghezra `10b3a8c8e` is a reference; lifespan alone must not exempt shared props,
  and the incomplete-snapshot valve must remain effective.

Other new Ghezra entity/resource/event candidates remain with their owners below.
The full 41-commit disposition is in [the fork audit](FORK_AUDIT_20261022.md).

## Client prop physics

- [ ] Fix joined-client object vibration, ejection and support penetration on
  boxes, desks and workbenches while host physics appears stable. Trace ordinary
  prop pose application, drive/park/end handoffs and simulation reactivation;
  resolve conflicting simulation/transform ownership and preserve stable resting
  contacts, collisions, pickup/drop and canonical host motion. The report does
  not yet establish the responsible route or whether client displacement reaches
  the host. Current config exposes no dedicated user-facing stack-physics fix;
  do not substitute arbitrary network tuning for a confirmed implementation.

## Player presentation and toys

- [ ] Finish remote flashlight presentation beyond the imported body-shadow fix
  from Ghezra `97f1f6072`. Continue from
  the existing retained state, replacement replay and same-component reconciliation;
  keep sender/slot ownership and current pawn/light bindings through native calls.
- [ ] Fix the falling-player T-pose. Resolve selected-model pose transfer and
  physics takeover in engine_ragdoll_skin/engine_playerragdoll and the remote
  display; preserve death-free puppet spawning and the standing warmup bridge.
- [ ] Finish held-toy variant schemas and hook/function ownership beyond the
  Dingus/ABPlush capture inputs. Keep PRE/POST provenance and bounded native work.
- [ ] Finish watoy start-cue and physics-hook ownership. Preserve the existing
  activation/audio/emitter schemas, original-hand provenance, shared View ownership
  and presentation budgets. Never replay an uncertain admitted activation.
- [ ] Finish thrown-sponge foam and resource ownership beyond window dabs;
  preserve the original draw's material/size and at-most-once native cleaning.
- [ ] Fix remaining stow stalls beyond indexed save-record class restoration;
  retain pending item-state restoration while classes are unavailable.
- [ ] Fill missing model previews and custom-skin compatibility while retaining
  rig exclusions. Treat skeletal scaling and creature physics as separate adapters.

## Event adapters and generator effects

- [ ] Finish Dreams scene-effect/lifetime adapters while keeping sleep,
  createDream/leaveDream, wake rewards, personal nightmare rolls and Insomniac
  consequences with their owner. Do not synthesize shared reward props.
- [ ] Finish Ariral Reputation state, selected outcomes, relocation and late join.
  Use calcRep's -75/-25/25/75 tiers and the actual tier/mainGamemode listeners;
  launchEvent itself is empty.
- [ ] Implement remaining Player-Activated trigger/outcome/effect routes with
  canonical authority for simultaneous activations.
- [ ] Finish Time-Related routes: 3AM eligibility and mainGamemode calendar
  branches outside eventer, including June 28 21:00, April 1 and November 29 22:49.
- [ ] Separate personal/session consequences for each Ending and implement its
  adapter; do not replay quit/travel on remote puppets.
- [ ] Finish Story Mode actor, phase, audio, bookkeeping and current-state joins.
  Horde/dropper need wave/class budgets, alive sets, countdowns and timeline
  ownership. Keep health/effects personal where native; avoid repeated rewards
  or save work from replaying a start.
- [ ] Finish Random event effects, including shared black fog beyond client
  producer suppression. Keep bp7Spawner's camera/roll/pause/quit owner-local;
  its ten-second eligible-roll scaling is already implemented.
- [ ] Map Signal processing/playback triggers, funny-rule gates and selected
  outcomes, then implement phases/effects and current-state joins.
- [ ] Implement level/map-script routes from the extracted headers. Use
  build/priority-level-scripts (263 headers, 52 scripted maps, 172 functions)
  and build/requested-events-audit; preserve personal and protection/exit branches.
- [ ] treeSpawner: transport the host-selected walking tree's visibility, mesh
  scale, movement and lifetime; finish client producer suppression and late join.
  Then scale only the native 600–900-second spawn wait, preserving mode,
  rendering and proximity gates.
- [ ] serverBreaker: finish protected-floppy consumption delivery to every
  recipient, protection/repair audio and delegate consequences. Retain the
  selected box, native day/difficulty/upgrade probabilities, slot-canonical ordering
  and retry ownership. Then scale only the native 1200–600-second eligible wait.
- [ ] Finish shared sky-event phases/cues, audio, delayed email/accounting,
  six pre-session latent continuations and remaining custom effects/creatures.
- [ ] Finish arirShipVanishing_C and other appearance/event variants beyond the
  arirShipAppear_C phase adapter; include shared reputation consequences.

Frequency changes must preserve eligibility, probabilities, personal dream rolls
and story dates. Scale eligible-roll waits without changing AI/animation cadence,
effect durations or sleep needs.

## Console, items and resource transactions

- [ ] Finish Rufus/thiccfus cross-player targets/grabs, audio/HUD, corpse/loot,
  damage and explosion transport; Madness/variant AI, damage/effects and remaining
  funny-rule HUD/events and toy/squeeze sounds.
- [ ] Finish llama marker/save/event-accounting lifecycle beyond the existing
  PlacedSave marker route and invocation-bound Begin recovery. Keep native host
  contributions authoritative; do not infer latent age from an absent sender or
  replay uncertain timer creation. Refused cleanup needs an owned retry path.
- [ ] Finish atomic paid wall/cement repair request/result and exact personal
  stock across hand/slot/drop, refusal and disconnect. Keep the current no-spend
  client refusal until debit, accepted output and refund form one transaction.
- [ ] Arbitrate concurrent water/cement/coal writers, stale in-flight records,
  dryTimer ownership and personal-hand transitions; finish output/accounting.
- [ ] Finish cross-peer personal debit/output/refund, personal extraction
  overrides/raw takeObj, receipt-less recovery and debt persistence across
  world/session reconstruction. Retain the local base-container escrow/refund
  boundary; never guess a refund or replay an uncertain admitted native effect.
- [ ] Finish remaining package/food subclass outputs, cross-peer portion/output
  arbitration and personal effects before host acceptance. Add native poison-pour,
  roach and reward routes plus uncertain-open refund recovery and persistence.
  Do not admit arbitrary replaceProp. Admission alone is not a committed output.
- [ ] Finish buried-item/treasure transaction authority and save-file persistence;
  mirror construction must not replay native treasure/loot-producing BeginPlay.
- [ ] Cover remaining dynamic grime sources and persist explosion/salt-rocket
  scorch provenance through full save/world reconstruction.

## Entity implementation

- [ ] Grayboar: complete join/audio/time coordination, host targets, turn/pitch,
  helper/delegate retirement, held-item handoffs, weapon/collision damage, one
  corpse/loot, lightning replacement and charged explosion/punch/spin effects.
- [ ] Rozitals: complete Great Pyramid, Kavotia, Pagonioplo-Igetis, Scouts and
  Soltomia action/effect adapters. Kavotia needs fire/laying montage, speech,
  canonical beam/impact/damage and exact phase timing.
- [ ] Antibreather / Fossilhound: complete player/cave-dependent Antibreather
  spawning, cross-peer attacks and Fossilhound ticker/attack routes.
- [ ] Arirals: complete follower/shooter/pigBeater and gun-stealer behavior,
  stolen/held/thrown-item ownership, attachments, shots/hits and event phases.
  Slapper Character classification and exact summoner spawn admission are
  implemented; its attacks, item handoffs and effects still need adapters.
- [ ] Greys / Flamethrower Tank: complete grayTest targets/actions/effects and
  firetank turret, fire, fuel, damage and destruction.
- [ ] Geoms: complete Ramiel (geomOcta_C) movement/charge/beam/audio/damage and
  Egg-shaped Geom (eg_C) retrieval/landing/special actions.
- [ ] UFOs: complete child spawns, beam/material/audio phases and join state for
  Boomerang, Joil, Grey Ship, Midas, Pill, Trifo and Orbs; resolve Grey Ship names.
- [ ] Deer / Fish / Cockroach: complete deer/deer_ded spawn/death/rejoin,
  caught prop_fish_0..21_C inventory and roach movement/eating/crushing/join state.
- [ ] Blue Brain Cheese, Restocker, Eye, Wolfgang, Tree with Eyes, Living Mushroom,
  Space Jellyfish: complete exact behavior/effect routes. Wolfgang derives from
  actor_save; do not map every eyes entity to eyer.
- [ ] Bone Man, Bloody Skeleton, Curious Eyes, Mimic, Flesh Slug, Zombie Deer:
  complete attacks/effects/lifetime, missing name mappings, shared mimic
  rendering/disguise/damage and centipede visibility.
- [ ] Ghost, Ghost Log, Fireflies, Walking Mannequin, Black Spot: complete missing
  names/effects/phases. Finish remaining wisp limb/blood presentation beyond the
  implemented animation-readiness and body/world-bound grab/release cancellation.
- [ ] Demons: complete individual targets, rituals/run-end behavior for SKerfur-O,
  Eyeless Insomniac, Insomnia Demon, Abandoned Kerfur, Flesh Erie, Goat Statue,
  Stolas Statue and Furfur. Keep live/zombie/angry Flesh Erie classes distinct.
- [ ] Forbidden: complete missing class mappings, spawn availability and local/global
  effects for Black Friend, CorpseWalker, Crasher, Fast-shadow Figure, Fridge,
  Interloper, The Exit Door, The Head, Pool Entity, Mountain People, Cursed Spider,
  Rune Sphere, Shadow Figure, Fake Kel and Black Sphere. Keep debug actors out of normal play.
- [ ] Living Erie / Girufus / Rufus: complete Girufus mapping and distinct
  interaction, animation, damage, ownership and lifetime behavior.
- [ ] Gnomes / Krampus: complete group spawning, presents, revenge, interaction,
  damage/death/shared lifetime and Krampus attack/fireball/jump/target/despawn.

## Requested mod integrations

- [ ] EmoteWheel 1.0.1: replace the upstream empty network bridge with owned
  emote/variant/phase/music state, interruption, late join and body/world cleanup.
- [ ] VEmu 1.1.0: define shared console/cartridge/AV/input ownership and emulator
  state/audio/video transport. Upstream AV output excludes SmartTV; an explicit
  adapter is required to support that combination.
- [ ] JeepMod 0.11.1: finish custom trunk/key/container/upgrade routes beyond
  inherited ATV pose/seat admission; preserve one shared inventory and lifetime.
- [ ] PhotographyPlus 0.10.3: implement task/reward/save ownership and photo
  submission routing without duplicating host rewards or another player's photos.
- [ ] SmartTV 0.9.6: implement custom player mode/source/playback/join ownership
  beyond vanilla media routes; keep local device/OBS access local.
- [ ] Audit FireTower 1.0.4 door/ModActor ownership and add any missing shared
  interaction/lifetime routes; retain matching local scenery and collision.

## Tooling and regression maintenance

- [ ] Reduce public-prose findings in documents, src.comment_doc_row and
  src.files_not_swept; restore required reading-room references. Existing gate
  findings and evidence belong in TESTLOG.

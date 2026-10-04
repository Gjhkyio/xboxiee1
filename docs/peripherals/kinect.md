# Kinect for Xbox 360 (peripheral overview)

> Scope: what Kinect IS on 360 (dates, connectivity, sensor facts). Protocol/SDK internals are UNKNOWN here; PrimeSense/open-USB history noted without how-to.

## Identity — CONFIRMED (tertiary, Wikipedia with cited primaries)

- Motion peripheral, no handheld controller (vs Wii Remote/PS Move). PrimeSense-based first gen; unveiled E3 2009 as “Project Natal”; 360 launch 2010-11-04 NA (EU 11-10, COL 11-14, AU 11-18, JP 11-20); Windows 2012-02-01; 360 discontinued 2016-04-20; One 2017-10-25; 35M units to 2017-10-25. Source: Wikipedia “Kinect” (fetched via search 2026-10-04; refs: Gizmodo, Xbox Wire 2016-04-20, BGR, IGN).
- Dash integration: SysExt/Kinect dash 12611 (2010-11-01) + Kinect Fun Labs (`marketplace.xbox.com/.../Kinect-Fun-Labs/66acd000-...` Archive 2011) per Kinect refs.

## Hardware facts on page — PARTIALLY CONFIRMED (needs teardown/manual primary)

- Bar + motorized tilt base; above/below display. IR + depth (structured pattern per MS citations), RGB options 640×480 / 1280×1024 lower-rate; range 1.2–3.5 m; 4-mic array, 16-bit 16 kHz, source-localization + noise-suppression → headset-free party chat; streaming IR pre-depth-map possible (page wording).
- Connectivity USB 2.0: Type-A on Phat (with SEPARATE mains power cable — tilt motor exceeds USB budget; Joystiq/MS Store refs) vs proprietary USB+power AUX on Slim S/E (no external PSU needed). SDKs for Windows later; USB “left open by design” (TechFlash 2010) enabling community drivers — historical note only.

## Queued (UNKNOWN here)

- XUSB peripheral auth (“Security Method 3” per x360-research snippet), mic/camera packet formats, motor control, dash service contracts. Needs x360-research full read + USB captures + SDK docs.

## Sources / References

- Wikipedia “Kinect”, `https://en.wikipedia.org/wiki/Kinect` — dates, PrimeSense/Natal, sensor/mic/power/AUX facts with per-claim refs above. Search-verified 2026-10-04 (tertiary; follow refs for primaries).
- Xbox Support Kinect setup tips (official, peripheral-level) — queued.

# Selected engineering projects

These notes explain what each project solves, the technical approach, and where to look in the code. For installation and current compatibility, use the linked repository documentation.

## CourierPilot · Android courier assistant

**Problem.** Courier offer screens often make it hard to compare pay against the full route before the offer expires.

**Approach.** An Android app observes the user's courier offer screen, extracts relevant information with OCR and accessibility integrations, estimates routes, and displays a compact pay-per-kilometre overlay. It keeps an on-device offer history, with optional, sanitized diagnostics.

**Engineering areas:** Kotlin, Jetpack Compose, Android Accessibility and notification services, ML Kit OCR, local persistence, routing with Valhalla, defensive UI-state handling.

**Trade-off:** screen-based integrations depend on layouts controlled by third parties. Uncertain routes are labelled as estimates instead of shown as exact numbers.

![CourierPilot app screen examples: Home, History, Addresses and Stats](https://raw.githubusercontent.com/Bl0ck154/CourierPilot/main/docs/assets/app-screens-light.png)

<sub>UI examples from the CourierPilot repository.</sub>

[Source and APK](https://github.com/Bl0ck154/CourierPilot) · [Release signing](https://github.com/Bl0ck154/CourierPilot/blob/main/docs/RELEASE_SIGNING.md)

## Ninebot Scooter Blocker · Bluetooth hardware companion

**Problem.** Reconnecting to a scooter, checking telemetry and applying a software lock takes more effort than a quick stop should require.

**Approach.** An Android BLE companion offers quick locking, live status, ride history, charging alerts and persistent connection management. The software lock is a convenience and an additional deterrent, not a replacement for a physical lock.

**Engineering areas:** Java, Android lifecycle, Bluetooth Low Energy, reconnection logic, telemetry parsing and on-device statistics.

**Trade-off:** scooter firmware and authentication vary by model. The documented hardware-tested baseline is more trustworthy than promising universal Ninebot/Segway compatibility.

![Illustrated Ninebot BLE and software-lock workflow](https://raw.githubusercontent.com/Bl0ck154/Ninebot-scooter-blocker/main/docs/assets/ble-workflow.gif)

<sub>Animated feature illustration, not captured app footage.</sub>

[Source, compatibility notes and releases](https://github.com/Bl0ck154/Ninebot-scooter-blocker)

## InstaFix Revived · Self-hosted link previews

**Problem.** Instagram links can produce incomplete embeds or Reels that do not play in messaging apps.

**Approach.** A Go service fetches public metadata and responds with preview-friendly tags, with optional proxying and media recovery paths. Documentation includes a measured Telegram preview-size boundary and the resulting Reel fallback strategy.

**Engineering areas:** Go HTTP services, OpenGraph metadata, media handling, Docker, proxy and caching behavior, regression tests.

**Trade-off:** upstream behavior and social-platform embed behavior change without notice. The former hosted demo is offline; the repository documents self-hosting.

![Sample chat embed from InstaFix documentation](https://raw.githubusercontent.com/Bl0ck154/InstaFix-Revived/main/.github/assets/orig_embed.jpg)

<sub>Preview example maintained in the InstaFix repository.</sub>

[Source and self-hosting guide](https://github.com/Bl0ck154/InstaFix-Revived) · [Telegram Reel investigation](https://github.com/Bl0ck154/InstaFix-Revived/blob/main/docs/telegram-reel-previews.md)

## Reddit MCP Publisher · Agent actions with owner approval

**Problem.** Agents that can read social content also need clear boundaries before publishing from a real account.

**Approach.** An MCP integration separates reading, preparing a draft, previewing the live target, approving the exact draft, and attempting publication. The tool checks for removal notices and supports browser fallbacks.

**Engineering areas:** TypeScript, MCP tool interfaces, browser automation, stateful publishing workflows and action validation.

**Trade-off:** account sessions, browser compatibility and subreddit rules are external dependencies. Approval does not guarantee a post remains published.

[Source and workflow demo](https://github.com/Bl0ck154/reddit-mcp-publisher)

## Wolt Discount Monitor · Public promotion dashboard

**Problem.** Discovering meaningful discounts across many venues takes repeated manual browsing.

**Approach.** A public dashboard collects visible promotions, ranks them and lets people filter noisy or potentially account-restricted offers before following a link to the venue.

**Engineering areas:** JavaScript, data filtering, GitHub Pages, scheduled collection and data-quality checks.

**Trade-off:** a visible promotion is not necessarily valid for every account. Currency, city availability, store status and campaign eligibility must be verified rather than assumed.

[Source](https://github.com/Bl0ck154/wolt-discount-monitor) · [Live dashboard](https://bl0ck154.github.io/wolt-discount-monitor/)

## Instagram → Telegram · Scheduled automation without a server

**Problem.** Keeping a Telegram channel synchronized with public Instagram content is tedious.

**Approach.** Python and GitHub Actions schedule retrieval through Apify, detect previously seen items and send new posts, Reels or carousels to Telegram.

**Engineering areas:** Python, GitHub Actions, scheduling, secrets management and deduplication.

**Trade-off:** Apify usage may cost money, scheduled jobs can run late, and external APIs may change.

[Source and setup](https://github.com/Bl0ck154/instagram-to-telegram)

---

I maintain other utilities and contribute to existing open-source projects. See the [main profile](README.md) and [public repositories](https://github.com/Bl0ck154?tab=repositories).

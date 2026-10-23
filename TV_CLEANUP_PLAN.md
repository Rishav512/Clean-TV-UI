# TV Clean-Up Plan — Xiaomi MiTV-AXSO0 (dangal)

> **Device:** Xiaomi Mi TV 4C Pro / 4A Pro · Android TV 9 · SDK 28 · Amlogic TXLX · ~1 GB RAM  
> **Repo:** CleanYourTV v2.6.0 · commit `0bb7f7edbf53349c7975a29495515453ed850526` ✅  
> **Date:** 2026-10-23

---

## Your Choices (confirmed)

| Question | Answer |
|---|---|
| Top apps (dock order) | YouTube → Netflix → JioHotstar → Prime Video |
| Features to keep | Casting (Chromecast) · Voice search (mic button) |
| Features to remove | Live TV tuner (not used) |
| Auto updates | Keep ON |
| Ad-blocking DNS | ON — `dns.adguard.com` (Private DNS) |
| Wallpaper | Slideshow — Car · Northern Lights · Milky Way Canyon |

---

## Before-State Snapshot

| Metric | Value |
|---|---|
| Total packages | 111 |
| Already disabled | 0 |
| Free RAM | ~207 MB / 1014 MB |
| Swap used | ~141 MB / 256 MB (half full — TV is memory-pressured) |
| Processes | 261 |
| Uptime | 20 min |
| Home screen | `com.google.android.tvlauncher` (Android TV stock) |

**Screenshot saved:** `tv-cleanup/screenshots/homescreen_before.png`

---

## Step-by-Step Plan

### STEP 1 · Disable ads, tracking and sponsored content
**What:** Turn off 8 apps that show you ads, track what you watch, and push sponsored content rows.  
**Why:** These run all the time in the background eating RAM and showing ads.  
**Gain:** Less RAM used, fewer ads, cleaner home screen.  
**Lose:** Nothing you'd notice — these are all background ad/tracking services.  
**Undo:** One command re-enables all of them instantly.

| Plain name | Package | What it does |
|---|---|---|
| Xiaomi analytics | `com.miui.tv.analytics` | Sends your watch history to Xiaomi servers |
| Xiaomi statistics | `com.xiaomi.statistic` | Usage stats sent to Xiaomi |
| Google feedback | `com.google.android.feedback` | Sends crash/usage data to Google |
| Google bug reporter | `com.google.android.tv.bugreportsender` | Uploads bug reports to Google |
| PatchWall (ad home) | `com.mitv.tvhome.atv` | Xiaomi's ad-filled home screen overlay |
| Web content ads | `com.xm.webcontent` | Pulls sponsored web content rows |
| Floating frame ads | `com.xiaomi.floatingframe` | Floating ad banners |
| Google TV recommendations | `com.google.android.tvrecommendations` | Sponsored "recommended" content rows |
| Leanback recommendations | `com.google.android.leanbacklauncher.recommendations` | More sponsored rows |
| Auto-install partner apps | `android.autoinstalls.config.xioami.dangal` | Silently installs partner (paid) apps |
| Glance lock-screen ads | `com.glance.tv` | News and ads on the standby screen |
| Mi TV+ live channel ads | `com.mitv.tvhome.mitvplus` | Sponsored live channel rows |
| Sensara TV guide | `co.sensara.tv.mitv` | Sponsored show recommendations |

### STEP 2 · Disable unused Xiaomi background services
**What:** Turn off 4 Xiaomi services you don't need.  
**Why:** They start at boot and sit in RAM doing nothing useful for you.  
**Gain:** Faster boot, more free RAM.  
**Lose:** "TV Manager" cleaner app (you won't need it), Xiaomi handbook, a legal text screen.  
**Firmware updates:** I'll leave this off. You can re-enable it if you want to check for one.

| Plain name | Package | What it does |
|---|---|---|
| TV Manager | `com.xiaomi.mitv.tvmanager` | Xiaomi's RAM cleaner (unneeded after debloat) |
| Mi TV Handbook | `com.xiaomi.mitv.handbook` | A static help manual app |
| Legal text screens | `com.xiaomo.tv.milegal` | Static privacy/legal text |
| Firmware updater | `com.xiaomi.mitv.updateservice` | Auto firmware update checker |

### STEP 3 · Disable unused preloaded apps
**What:** Turn off apps that came preloaded but you don't use.  
**Why:** They start themselves at boot and take up RAM.  
**Lose:** These apps. They're not gone, just sleeping — re-enable any from Settings → Apps.

| Plain name | Package | What it does |
|---|---|---|
| Mi Music | `com.xiaomi.mimusic2` | Xiaomi music app |
| Google Play Games | `com.google.android.play.games` | Gaming platform (for phone games) |
| Google Play Movies | `com.google.android.videos` | Play Movies & TV (separate from YouTube) |
| Mi Gallery | `com.mitv.gallery` | Photo viewer (Media Player still works for USB) |

### STEP 4 · Disable unused preloaded streaming apps
**What:** Turn off streaming apps that came pre-installed but you don't use.  
**Why:** They wake up at boot and show unwanted notifications.  
**Lose:** These streaming services. Re-enable from Settings → Apps if you ever want one.

*I'll confirm this list with you before touching anything — some of these may be ones you use.*

| Plain name | Package |
|---|---|
| FanCode | `com.fancode.tv` |
| Sun NXT | `com.suntv.sunnxt.mitv` |
| Eros Now | `com.eros.mitv` |
| Discovery+ | `com.discoveryplus.mitv` |
| DD National | `com.ddnational.prasarbharati` |
| Al Jazeera | `net.aljazeera.english` |

### STEP 5 · Turn on Private DNS (ad-blocking)
**What:** Change one setting — Private DNS — to route TV traffic through AdGuard's free DNS.  
**Why:** Blocks ads in apps, blocks tracking, speeds up browsing.  
**Undo:** Set Private DNS back to "Automatic" — one command.

### STEP 6 · Install the clean home screen (launcher)
**What:** Build and install the CleanYourTV launcher from the repo. Set it as the new Home.  
**Why:** Replaces the cluttered stock home screen with a clean, fast, Apple-TV-style dock.  
**What you get:** Your 4 apps in a dock at the bottom, slideshow wallpaper, no ads.  
**Undo:** Run the repo's restore script — stock home screen comes back in 10 seconds.  
**Needs:** JDK 17 + Android SDK (I'll check and install if needed).

### STEP 7 · Set up slideshow wallpaper
**What:** Push the 3 generated wallpapers to the TV and configure them as a rotating slideshow.  
**Wallpapers:** Car · Northern Lights · Milky Way Canyon (all 4K 16:9).

---

## What I will NEVER touch

| Category | Examples |
|---|---|
| Android core | SystemUI, Settings, framework, WebView |
| Google services | GMS (Play Services), Play Store, GSF |
| Network | Wi-Fi, Bluetooth, Ethernet, DNS resolver |
| Remote & input | Remote service, Bluetooth pairing, keyboard (Gboard) |
| Casting (you use it) | Chromecast (`com.google.android.apps.mediashell`) |
| Voice search (you use it) | Google Assistant (`com.google.android.katniss`, Pumpkin) |
| Your apps | Netflix, YouTube, JioHotstar, Prime Video, VLC, etc. |
| Droidlogic hardware | All `com.droidlogic.*` — controls HDMI, display, sound |
| Launcher (until new one is installed) | `com.google.android.tvlauncher` |

---

## Log Table (fills in as we go)

| When | Change | Why | Undo command |
|---|---|---|---|
| — | — | — | — |

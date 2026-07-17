# Custom EPG for IPTV (Sparkle TV & Strong 8)

A curated XMLTV EPG guide with only the channels you want — UK (Premier League, EFL, British sports) first, then Canada, USA, and Australia. Generated daily via GitHub Actions and served from a public URL your IPTV app can auto-pull.

## ✅ EPG URL

```
https://raw.githubusercontent.com/farleyflex/epg-guide/main/epg.xml
```

Use this URL in Sparkle TV or Strong 8 as your EPG source. It auto-updates every day at 6:00 AM UTC.

**Current status:** 75 channels, 9,000+ programs, 5 days of guide data. All channel IDs verified to match your IPTV provider's EPG IDs.

---

## Setup Instructions

### Sparkle TV

1. Open **Sparkle TV** on your Android TV
2. Add your IPTV provider as a source (Xtream Codes — use your provider's server, username, and password)
3. Go to **Settings** → **EPG** → **Add EPG Source**
4. Enter the EPG URL:
   ```
   https://raw.githubusercontent.com/farleyflex/epg-guide/main/epg.xml
   ```
5. Set update interval to **24 hours**
6. Sparkle will match your channels to the EPG using the channel IDs

### Strong 8 App

1. Open **Strong 8** on your Android TV
2. Add your IPTV provider (Xtream Codes — use your provider's server, username, and password)
3. Go to **Settings** → **EPG Settings**
4. Enter the EPG URL:
   ```
   https://raw.githubusercontent.com/farleyflex/epg-guide/main/epg.xml
   ```
5. Set auto-update to **24 hours**
6. Trigger a manual EPG update to load it immediately

### How channel matching works

The EPG file contains `<channel id="...">` entries. Your IPTV app matches these IDs to the channels in your playlist. The `xmltv_id` values in `channels.xml` are set to match the EPG channel IDs that your IPTV provider uses (e.g., `skysportspremiereleague.uk`, `ESPN.us`, `CBC.ca`, `FoxSports3.au`).

All 75 channel IDs in this EPG have been verified to match your Strong 8 provider's `epg_channel_id` values. If a channel shows no EPG data in your app, check that the channel name in your playlist corresponds to one of the channels listed below.

---

## Channels Included (75 channels)

### Group 1: UK — Premier League, EFL, British Sports (32 channels)
**Source:** mytelly.co.uk

**Sports:**
| Channel | EPG ID |
|---------|--------|
| Sky Sports Premier League | `skysportspremiereleague.uk` |
| Sky Sports Football | `skysportsfootball.uk` |
| Sky Sports Main Event | `skysportsmainevent.uk` |
| Sky Sports Cricket | `skysportscricket.uk` |
| Sky Sports Golf | `skysportsgolf.uk` |
| Sky Sports F1 | `skysportsf1.uk` |
| Sky Sports Racing | `skysportsracing.uk` |
| Sky Sports Mix | `skysportsmix.uk` |
| Sky Sports News | `skysportsnews.uk` |
| Sky Sports Action | `skysportsaction.uk` |
| Sky Sports Tennis | `skysportstennis.uk` |
| Sky Sports+ | `SkySportsArena.uk` |
| TNT Sports 1-8 | `tntsports1.uk` through `tntsports4.uk`, `TNTSport1.uk` through `TNTSport4.uk` |
| Premier Sports 1-2 | `premiersports1.uk`, `premiersports2.uk` |

**General:**
| Channel | EPG ID |
|---------|--------|
| BBC One | `bbc1.uk` |
| BBC Two | `bbc2.uk` |
| BBC News | `BBCNews.uk` |
| BBC Parliament | `BBCParliament.uk` |
| Channel 4 | `Channel4.uk` |
| Channel 5 | `Channel5.uk` |
| U&Dave | `Dave.uk` |
| Sky News | `SkyNews.uk` |

### Group 2: Canada (19 channels)
**Source:** tvpassport.com

| Channel | EPG ID |
|---------|--------|
| CBC | `CBC.ca` |
| CBC News Network | `CBCNews.ca` |
| CTV Toronto | `CTVHT.ca` |
| CTV News Channel | `CTVNC.ca` |
| CTV Drama | `CTVDrama.ca` |
| CTV Comedy | `CTVComedy.ca` |
| Sportsnet 360/One/Ontario/East/Pacific/West/World | `Sportsnet360.ca` etc. |
| TSN 1-5 | `TSN1.ca` through `TSN5.ca` |
| Global Toronto | `CIII.ca` |

### Group 3: USA (21 channels)
**Source:** tvpassport.com

| Channel | EPG ID |
|---------|--------|
| ESPN | `ESPN.us` |
| ESPN News | `ESPNNews.us` |
| FOX Sports 1/2 | `foxsports1.us`, `foxsports2.us` |
| NFL Network | `NFLNetwork.us` |
| Golf Channel | `GolfChannel.us` |
| MLB Network | `MLBNetwork.us` |
| CBS Sports Network | `CBSSportsNetwork.us` |
| Big Ten Network | `BigTenNetwork.us` |
| TNT | `TNT.us` |
| AMC | `AMC.us` |
| HBO / HBO 2 | `HBO.us`, `HBO2.us` |
| Showtime | `Showtime.us` |
| Starz | `Starz.us` |
| CNN | `cnn.us` |
| MSNBC | `msnbc.us` |
| CNBC | `CNBC.us` |
| USA Network | `USANetwork.us` |
| Discovery Channel | `DiscoveryChannel.us` |
| History Channel | `HistoryChannel.us` |

### Group 4: Australia (5 channels)
**Source:** foxtel.com.au

| Channel | EPG ID |
|---------|--------|
| FOX SPORTS 503/505/506 | `FoxSports3.au`, `FoxSports5.au`, `FoxSports6.au` |
| Fox Sports News | `FoxSportsNews.au` |
| Sky News Australia | `SKYNewsLive.au` |

---

## How It Works

- **GitHub Actions** runs the [iptv-org/epg](https://github.com/iptv-org/epg) grabber every day at 6:00 AM UTC
- The grabber fetches 5 days of program data from the source sites listed in `channels.xml`
- The output `epg.xml` is committed to this repo
- Your IPTV app pulls the EPG from the raw GitHub URL automatically

## Manual Trigger

Go to the **Actions** tab → "Generate EPG" → "Run workflow" to regenerate the EPG on demand.

## Customizing

Edit `channels.xml` to add or remove channels. Each entry specifies:
- `site` — the EPG source website (mytelly.co.uk, tvpassport.com, foxtel.com.au)
- `site_id` — the channel ID on that source site
- `xmltv_id` — the ID in the output XMLTV file (must match your IPTV provider's channel IDs)
- Channel name — the display name

See [SITES.md](https://github.com/iptv-org/epg/blob/master/SITES.md) for all available EPG source sites.

## Why a Custom EPG?

Your IPTV provider has 55,000+ channels but you only watch a fraction of them. The provider's built-in EPG is a massive file (72MB) that takes forever to load and clutters your guide with channels you don't care about. This custom EPG gives you a clean, curated guide with only the channels you actually watch, organized by your preferred country grouping (UK first, then CA, US, AU).

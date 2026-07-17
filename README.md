# Custom EPG for IPTV (Sparkle TV & Strong 8)

A curated XMLTV EPG guide with only the channels you want — UK (Premier League, EFL, British sports) first, then Canada, USA, and Australia. Generated daily via GitHub Actions and served from a public URL your IPTV app can auto-pull.

## EPG URL

```
https://raw.githubusercontent.com/farleyflex/epg-guide/main/epg.xml
```

Use this URL in Sparkle TV or Strong 8 as your EPG source. It auto-updates every day at 6:00 AM UTC.

---

## Channels Included (~70 curated channels)

### Group 1: UK — Premier League, EFL, British Sports
**Source:** mytelly.co.uk

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
| Eurosport 1-2 | `Eurosport1.uk`, `Eurosport2.uk` |
| BBC One/Two/News/Parliament | `bbc1.uk`, `bbc2.uk`, `BBCNews.uk`, `BBCParliament.uk` |
| Channel 4/5 | `Channel4.uk`, `Channel5.uk` |
| Dave, HGTV, Sky News | `Dave.uk`, `HGTV.uk`, `SkyNews.uk` |

### Group 2: Canada
**Source:** tvpassport.com

| Channel | EPG ID |
|---------|--------|
| CBC, CBC News | `CBC.ca`, `CBCNews.ca` |
| CTV Toronto, CTV News, CTV Drama/Comedy | `CTVHT.ca`, `CTVNC.ca`, `CTVDrama.ca`, `CTVComedy.ca` |
| Sportsnet 360/One/Ontario/East/Pacific/West/World | `Sportsnet360.ca` etc. |
| TSN 1-5 | `TSN1.ca` through `TSN5.ca` |
| Global Toronto | `CIII.ca` |

### Group 3: USA
**Source:** tvpassport.com

| Channel | EPG ID |
|---------|--------|
| ESPN, ESPN 2, ESPN News | `ESPN.us`, `ESPN2.us`, `ESPNNews.us` |
| FOX Sports 1/2 | `foxsports1.us`, `foxsports2.us` |
| NFL Network, MLB Network, Golf Channel | `NFLNetwork.us`, `MLBNetwork.us`, `GolfChannel.us` |
| CBS Sports Network, Big Ten Network | `CBSSportsNetwork.us`, `BigTenNetwork.us` |
| TNT, AMC, USA Network | `TNT.us`, `AMC.us`, `USANetwork.us` |
| HBO, HBO 2, Showtime, Starz | `HBO.us`, `HBO2.us`, `Showtime.us`, `Starz.us` |
| CNN, MSNBC, CNBC | `cnn.us`, `msnbc.us`, `CNBC.us` |
| Discovery Channel, History Channel | `DiscoveryChannel.us`, `HistoryChannel.us` |

### Group 4: Australia
**Source:** foxtel.com.au

| Channel | EPG ID |
|---------|--------|
| FOX SPORTS 503/505/506 | `FoxSports3.au`, `FoxSports5.au`, `FoxSports6.au` |
| Fox Sports News | `FoxSportsNews.au` |
| Fox Cricket, Fox League, Fox Footy | `FoxCricket.au`, `FoxLeague.au`, `FoxFooty.au` |
| Sky News Australia | `SKYNewsLive.au` |
| Arena, Comedy, Discovery, FOX8 | `Arena.au`, `Comedy.au`, `DiscoveryChannel.au`, `Fox8.au` |

---

## Setup Instructions

### Sparkle TV

1. Open **Sparkle TV** on your Android TV
2. Add your IPTV provider as a source (Xtream Codes or M3U — use your provider's details)
3. Go to **Settings** → **EPG** → **Add EPG Source**
4. Enter the EPG URL:
   ```
   https://raw.githubusercontent.com/farleyflex/epg-guide/main/epg.xml
   ```
5. Set update interval to **24 hours**
6. Sparkle will match your channels to the EPG using the channel IDs listed above

### Strong 8 App

1. Open **Strong 8** on your Android TV
2. Add your IPTV provider (Xtream Codes — use your provider's details)
3. Go to **Settings** → **EPG Settings**
4. Enter the EPG URL:
   ```
   https://raw.githubusercontent.com/farleyflex/epg-guide/main/epg.xml
   ```
5. Set auto-update to **24 hours**
6. Trigger a manual EPG update to load it immediately

### How channel matching works

The EPG file contains `<channel id="...">` entries. Your IPTV app matches these IDs to the channels in your playlist. The `xmltv_id` values in `channels.xml` are set to match the EPG channel IDs that your IPTV provider uses (e.g., `skysportspremiereleague.uk`, `ESPN.us`, `CBC.ca`, `FoxSports3.au`).

If a channel shows no EPG data, it means the provider's channel ID doesn't match any ID in this EPG file. You can check which IDs your provider uses by looking at your playlist's `tvg-id` values, or checking your provider's EPG endpoint.

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

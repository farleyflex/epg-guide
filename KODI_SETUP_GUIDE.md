# Kodi IPTV Setup Guide — Clean UI + Recording + Custom EPG

This guide sets up Kodi on your Android TV with:
- **Arctic Horizon 2** skin for a modern, clean interface
- **PVR IPTV Simple Client** for live TV channels
- **Your custom curated EPG** (75 UK/CA/US/AU channels)
- **Recording** — schedule and save shows to your device storage

---

## What You Need

1. Your Android TV box (with internet connection)
2. A USB drive (to transfer the playlist file) OR a file manager app on your Android TV
3. About 30 minutes

---

## Step 1: Install Kodi

1. On your Android TV, open the **Google Play Store**
2. Search for **Kodi**
3. Install it (it's free, official)
4. Open Kodi once to let it initialize, then exit

---

## Step 2: Get the Playlist File onto Your Android TV

Your curated playlist file (`playlist.m3u`) contains 75 channels with correct EPG IDs. It's stored on your computer. You need to get it onto your Android TV box.

### Option A: USB Drive (simplest)
1. Copy `playlist.m3u` to a USB drive from your computer
2. Plug the USB drive into your Android TV box
3. Use a file manager app (like **File Commander** or **Solid Explorer** from Play Store) to copy the file to your Android TV's internal storage
4. Put it somewhere you'll remember, like:
   ```
   /storage/emulated/0/playlist.m3u
   ```
   (This is the "Download" or "Internal Storage" folder)

### Option B: Download directly on the Android TV
If you can access the file via a URL or cloud drive:
1. Open a browser on your Android TV (or use **Send files to TV** app from Play Store)
2. Download `playlist.m3u` to your device storage

### Note about the playlist file
This file contains your IPTV credentials in the stream URLs. This is normal — every IPTV playlist has credentials in it. Just don't share the file or upload it anywhere public. It stays on your Android TV box.

---

## Step 3: Install the PVR IPTV Simple Client

1. Open **Kodi**
2. Go to **Add-ons** (the open box icon in the left menu)
3. Click the **box icon** at the top left (the open box with an up arrow)
4. Select **Install from repository**
5. Select **Kodi Add-on Repository** (the official one)
6. Scroll down and select **PVR clients**
7. Find **PVR IPTV Simple Client** and click it
8. Click **Install**
9. Wait for it to install (you'll see a notification when done)

---

## Step 4: Configure PVR IPTV Simple Client

1. After installation, go back to **Add-ons** → **My add-ons** → **PVR clients**
2. Click on **PVR IPTV Simple Client**
3. Click **Configure** (the gear icon)
4. Under **General** settings:
   - **M3U Play List URL:** Leave this BLANK
   - **Location:** Select **Local Path (include Local Network)**
   - **M3U Play List Path:** Browse to where you saved `playlist.m3u` on your Android TV
     (e.g., `/storage/emulated/0/playlist.m3u`)
   - **Cache M3U at local storage:** Turn this **ON**

5. Under **EPG Settings**:
   - **Location:** Select **Remote Path (Internet address)**
   - **XMLTV URL:** Enter your custom EPG URL:
     ```
     https://raw.githubusercontent.com/farleyflex/epg-guide/main/epg.xml
     ```
   - **Cache EPG at local storage:** Turn this **ON**
   - **Number of days to keep EPG data:** Set to **5**

6. Under **Channels**:
   - **Channel order:** Set as you prefer (by channel number or name)

7. Click **OK** to save settings

---

## Step 5: Enable Live TV in Kodi

1. Go to **Kodi Settings** (gear icon at the top)
2. Select **PVR & Live TV**
3. Turn **ON** the toggle for **Enabled** (or "PVR Manager Enabled")
4. Wait — Kodi will now load your channels and EPG data. This can take 1-2 minutes the first time.
5. You should see a **TV** or **Live TV** option appear in your Kodi home screen.

---

## Step 6: Install Arctic Horizon 2 Skin

This gives Kodi a clean, modern look instead of the default interface. Arctic Horizon 2 is not in the default Kodi repository — you need to add the developer's repository first.

### Step 6a: Add the jurialmunkey repository

1. Go to **Kodi Settings** (gear icon at the top)
2. Select **File manager**
3. Select **Add source**
4. Click the box that says `<None>`
5. Type exactly:
   ```
   https://jurialmunkey.github.io/repository.jurialmunkey/
   ```
6. Give it a name at the bottom, e.g., type `jurialmunkey`
7. Click **OK**

### Step 6b: Install the repository

1. Go back to the Kodi home screen
2. Go to **Add-ons** (the open box icon)
3. Click the **box icon** at the top left (open box with up arrow)
4. Select **Install from zip file**
5. A warning may appear about unknown sources — click **Yes** to allow it (you can disable this later)
6. Select **jurialmunkey** (the source you just added)
7. Select **repository.jurialmunkey-3.4.zip**
8. Wait for the "Add-on installed" notification at the top right

### Step 6c: Install Arctic Horizon 2

1. Go to **Add-ons** → click the **box icon** at the top left
2. Select **Install from repository**
3. Select **Jurialmunkey's Kodi Repository** (it should now be in the list)
4. Scroll down and select **Look and feel**
5. Select **Skins**
6. Find **Arctic Horizon 2** and click it
7. Click **Install**
8. Wait — it will download the skin and all its dependencies (this can take a minute or two)
9. Kodi will ask if you want to switch to the new skin — click **Yes**
10. Answer any setup prompts that appear

### Alternative skins (if Arctic Horizon 2 doesn't work)

From the same jurialmunkey repository:
- **Arctic Fuse 3** — similar style, more customizable home screen widgets
- **Arctic Fuse 2** — slightly older but stable
- **Aura** — another clean minimal option

You can also try skins from the default Kodi repository:
- Go to **Settings** → **Interface** → **Skin** → **Get More...** → try **Estuary Mod v2** or **Aeon Nox Silvo**

### Arctic Horizon 2 Settings (recommended for IPTV)
Once installed, customize it:
1. Go to **Settings** → **Interface** → **Skin** → **Configure Skin** (gear icon)
2. Under **Home menu**:
   - Make sure **TV** or **Live TV** is enabled/visible
   - You can hide menu items you don't need (Music, Pictures, etc.)
3. Under **Background**:
   - Set to **Solid color** or use fanart for a cleaner look
4. Adjust the **view types** for channels:
   - Go to **TV** → **Channels** → press the menu button on your remote → **View** → choose **List** or **Wide List** for the channel browsing

---

## Step 7: Using Your IPTV Channels

### Browsing Channels
1. From the Kodi home screen, select **TV** (or **Live TV**)
2. You'll see:
   - **Channels** — all 75 channels
   - **Groups** — UK, Canada, USA, Australia
   - **Guide** — the EPG program guide (5 days of data)

### Watching a Channel
1. Go to **TV** → **Channels**
2. Select a channel — it starts playing
3. Press **OK** on your remote to bring up the channel list while watching
4. Press the **back** button to stop

### Using the EPG Guide
1. Go to **TV** → **Guide** (or press the Guide button on your remote if you have one)
2. You'll see a grid showing what's on now and what's coming up
3. Use arrow keys to navigate, **OK** to tune to a channel

---

## Step 8: Recording

### Setting Up Recording Storage
1. Go to **Kodi Settings** → **PVR & Live TV** → **Recording**
2. Set the **Recording folder path** to where you want recordings saved:
   - If your Android TV has a USB drive or SD card, use that
   - Otherwise use internal storage (e.g., `/storage/emulated/0/Recordings/`)
3. Create the folder if it doesn't exist (use your file manager app)

### Recording a Show
1. While watching a channel, press the **menu/context** button on your remote
2. Select **Record** (or "Record this channel")
3. Choose whether to record just this program or set up a recurring recording

### Recording from the EPG Guide
1. Go to **TV** → **Guide**
2. Highlight a future program
3. Press the **menu/context** button on your remote
4. Select **Record** — Kodi will schedule the recording and automatically tune in when the program starts

### Viewing Recordings
1. Go to **TV** → **Recordings** from the Kodi home screen
2. Select a recording to play it back

---

## Step 9: Updating the Playlist

If you need to update the channel list (e.g., if your provider changes stream IDs):
1. Generate a new `playlist.m3u` file
2. Copy it to your Android TV, replacing the old one
3. In Kodi, go to **Settings** → **PVR & Live TV** → **General** → **Clear data**
4. Kodi will reload from the new file

---

## Troubleshooting

### No channels showing up
- Verify the playlist.m3u file path is correct in pvr.iptvsimple settings
- Go to **Settings** → **PVR & Live TV** → **General** → **Clear data**, then restart Kodi
- Check that the M3U file is not empty: open it with a text editor and confirm it has channel entries

### EPG shows "No information available"
- Verify the EPG URL is correct: `https://raw.githubusercontent.com/farleyflex/epg-guide/main/epg.xml`
- Go to **Settings** → **PVR & Live TV** → **General** → **Clear data**, then restart Kodi
- The EPG updates daily at 6 AM UTC via GitHub Actions. If it's stale, you can trigger a manual update from the GitHub repo's Actions tab.

### Channels play but no EPG data
- This means the `tvg-id` in your M3U doesn't match the `channel id` in the EPG XML
- Verify the M3U was generated correctly (open it and check that `tvg-id` values like `skysportspremiereleague.uk` are present)

### Recording fails
- Check that the recording folder path is valid and writable
- Make sure you have enough storage space
- Some IPTV streams may not be recordable (provider restriction)

### Kodi is slow
- Reduce the EPG days from 5 to 3 in pvr.iptvsimple settings
- Clear Kodi cache: **Settings** → **System** → **Cache** → clear
- If using fanart backgrounds, switch to solid color in skin settings

### Skin installation fails
- Make sure you're using the official Kodi Add-on Repository
- Try a different skin if Arctic Horizon 2 won't install — **Arctic Fuse 3** or **Aeon Nox Silvo** are good alternatives

---

## Your EPG URL (for reference)

```
https://raw.githubusercontent.com/farleyflex/epg-guide/main/epg.xml
```

This is a public URL with no credentials. It auto-updates daily at 6:00 AM UTC with 5 days of guide data for 75 curated UK/CA/US/AU channels.

---

## Summary of What's Where

| Item | Location | Contains Credentials? |
|------|----------|-----------------------|
| Playlist (M3U) | Local file on your Android TV box | YES — keep private |
| EPG (XMLTV) | GitHub public URL | NO — safe to share |
| Kodi + Skin | Installed on your Android TV | NO |
| PVR IPTV Simple | Kodi add-on | NO (reads from local M3U + remote EPG) |

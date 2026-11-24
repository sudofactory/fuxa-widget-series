# EP4 · How-to videos (Video)

New staff tap a button on the tablet, and the how-to video for that machine plays right there. No more explaining the cup sealer for the third time.

新人在平板上按一下按鈕，那台機器的教學影片就在旁邊播，不用再第三次解釋封口機怎麼用。

## Files

| File | What it is |
|---|---|
| `how-to-videos.json` | The FUXA project after this episode: everything from EP3 (phone menu `MainView`, `Door sign`, `Opening hours`, `Boba log`), plus tags `video_url` and `video_play` and the page `How-to` with three buttons and a Video widget |
| `_images/how-to/cup_sealer.mp4` | How to use the cup sealer (24 s) |
| `_images/how-to/cook_boba.mp4` | How to cook boba (30 s) |
| `_images/how-to/closing_up.mp4` | Closing up (25 s) |

The three clips are hand-drawn, with a spoken step for each picture and light ukulele music. Use them to try the page, or swap in your own.

Made and tested with FUXA 1.3.5. The `How-to` page does not depend on the other pages, so you can also build it in an empty project.

## Open it in FUXA

1. Copy the folder `_images/how-to` into FUXA's `_images` folder, so the clips end up in `_images/how-to/`.
   - FUXA started with `--userDir <folder>`: `<folder>/_images/how-to/`
   - otherwise `_images` is in FUXA's `server` folder; for an npm install that is `node_modules/@frangoteam/fuxa/server/_images/how-to/`
2. In the FUXA editor, open the save menu (top left) and choose **Save Project As** to keep a copy of your current project. Opening this file **replaces** the project you have open.
3. In the same menu choose **Open Project** and pick `how-to-videos.json`.
4. Open the page from any phone or tablet on the same Wi-Fi (use your computer's IP, not `localhost`; 1881 is FUXA's default port):
   - How-to: `http://YOUR-PC-IP:1881/view?name=How-to`
   - or the menu: `http://YOUR-PC-IP:1881/home` → **4 How-to**
5. Tap **Cook boba**: the video switches and plays by itself. Tap the video to pause or go full screen.

## 匯入方式

1. 把 `_images/how-to` 資料夾複製到 FUXA 的 `_images` 資料夾裡，影片會在 `_images/how-to/` 底下。
   - FUXA 用 `--userDir <資料夾>` 啟動的話：`<資料夾>/_images/how-to/`
   - 沒有指定的話，`_images` 在 FUXA 的 `server` 資料夾裡；npm 安裝是 `node_modules/@frangoteam/fuxa/server/_images/how-to/`
2. 在 FUXA 編輯器左上角打開存檔選單，先按 **Save Project As** 備份目前的專案。開啟這個檔案會**取代**你目前的專案。
3. 同一個選單按 **Open Project**，選 `how-to-videos.json`。
4. 用同一個 Wi-Fi 的手機或平板打開（用電腦的 IP，不是 `localhost`；1881 是 FUXA 預設埠）：
   - 教學頁：`http://你的電腦IP:1881/view?name=How-to`
   - 或從選單：`http://你的電腦IP:1881/home` → **4 How-to**
5. 按 **Cook boba**，影片換過來、自己開始播。點一下影片可以暫停或全螢幕。

## What is inside

- Tag `video_url` on FUXA Server: string, Init value `/_images/how-to/cup_sealer.mp4`. The Video widget plays whatever address is in this tag; the Init value makes the page open with a video, even after a restart.
- Tag `video_play` on FUXA Server: number. Every tap adds one, so the number always changes and the video starts.
- Page `How-to` (1024 x 768):
  - Video widget linked to `video_url`, **Show controls** and **Loop** on. Address starts with `/_images/…` (no computer name in front, so a tablet can find it). Actions: `video_play`, min 1, max 1000000000, type **Start**.
  - Three buttons, Events → **Click**:
    - **Set Value** with the clip's address → `video_url` (`/_images/how-to/cup_sealer.mp4`, `cook_boba.mp4`, `closing_up.mp4`)
    - **Set Value** 1, function **increase** → `video_play`
- Colours: background `#FFF3DC`, title bar `#7B4B2A`, buttons `#3DBE7A` / `#7B4B2A` / `#2F80ED` with white text, frame `#222831`, font Quicksand-Bold.

## 內容說明

- FUXA Server 上的 tag `video_url`：string，Init value `/_images/how-to/cup_sealer.mp4`。Video 元件播的就是這個 tag 裡的網址；有 Init value，頁面打開一定有影片，重開也一樣。
- FUXA Server 上的 tag `video_play`：number。每按一下加 1，數字一定會變，影片就開始播。
- 頁面 `How-to`（1024 × 768）：
  - Video 元件連 `video_url`，**Show controls**、**Loop** 打開。網址從 `/_images/…` 開始（前面不帶電腦名稱，平板才找得到）。Actions：`video_play`、min 1、max 1000000000、type **Start**。
  - 三顆按鈕，Events → **Click**：
    - **Set Value** 填影片網址 → `video_url`（`/_images/how-to/cup_sealer.mp4`、`cook_boba.mp4`、`closing_up.mp4`）
    - **Set Value** 1、function **increase** → `video_play`
- 配色：背景 `#FFF3DC`、標題列 `#7B4B2A`、按鈕 `#3DBE7A`／`#7B4B2A`／`#2F80ED` 白字、外框 `#222831`、字體 Quicksand-Bold。

## Good to know

- Which files play is up to the browser, not FUXA. MP4 (H.264) plays everywhere; MOV and HLS (`.m3u8`) also work. WebM and MKV only in some browsers (iPad Safari does not play MKV). AVI, Ogg, YouTube links and camera streams do not play (for YouTube use the iframe widget). Not sure? Convert to MP4 (H.264).
- The address can also be a web address to an MP4 file, as long as the shop has internet.
- Print a QR code with the page address and stick it on the machine: staff scan it with a phone on the shop's Wi-Fi.
- Music in the clips: "Ukulele Song" and "Happy Whistling Ukulele" from FreePD (CC0).

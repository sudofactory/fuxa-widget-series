# EP3 · Boba log (Table)

One tap on the tablet, and the time the boba was cooked is written down. No more sticky notes.
Video: *When Was This Boba Cooked? One Button Answers It (FUXA Table)*

煮好一鍋珍珠，在平板上按一下，時間就記下來了，不用再貼便利貼。

## Files

| File | What it is |
|---|---|
| `boba-log.json` | The FUXA project after this episode: everything from EP2 (phone menu `MainView`, `Door sign` with the CLOSED layer, `Opening hours`), plus tag `boba_batches` and the page `Boba log` with a button, a count and a History table |

Made and tested with FUXA 1.3.5. Only want the starting point? Use EP2's file: [../ep2-opening-hours](../ep2-opening-hours/). The `Boba log` page does not depend on the other pages, so you can also build it in an empty project.

## Open it in FUXA

1. In the FUXA editor, open the save menu (top left) and choose **Save Project As** to keep a copy of your current project. Opening this file **replaces** the project you have open.
2. In the same menu choose **Open Project** and pick `boba-log.json`.
3. If you use EP2's opening hours, add them again on `http://YOUR-PC-IP:1881/view?name=Opening%20hours` (the hours are not stored in the project file; see EP2).
4. Open the page from any phone or tablet on the same Wi-Fi (use your computer's IP, not `localhost`; 1881 is FUXA's default port):
   - Boba log: `http://YOUR-PC-IP:1881/view?name=Boba%20log`
   - or the menu: `http://YOUR-PC-IP:1881/home` → **3 Boba log**
5. Tap **New batch**, then the refresh icon at the top right of the table: a new row with the time.

## 匯入方式

1. 在 FUXA 編輯器左上角打開存檔選單，先按 **Save Project As** 備份目前的專案。開啟這個檔案會**取代**你目前的專案。
2. 同一個選單按 **Open Project**，選 `boba-log.json`。
3. 有用 EP2 營業時間的話，到 `http://你的電腦IP:1881/view?name=Opening%20hours` 重新加上（營業時間不存在專案檔裡，見 EP2）。
4. 用同一個 Wi-Fi 的手機或平板打開（用電腦的 IP，不是 `localhost`；1881 是 FUXA 預設埠）：
   - 珍珠紀錄：`http://你的電腦IP:1881/view?name=Boba%20log`
   - 或從選單：`http://你的電腦IP:1881/home` → **3 Boba log**
5. 按 **New batch**，再按表格右上角的重新整理圖示，就多一列帶時間的紀錄。

## What is inside

- Tag `boba_batches` on FUXA Server: number. In **Tag options**, all three switches are on (**Registration Enabled**, **Save if changed**, **To restore**) and **Save value interval** is **0**: FUXA saves the value with the time every time it changes.
- Page `Boba log` (1024 x 768):
  - Button **New batch** (320 x 120): Events → **Click**, **Set Value**, value **1**, function **increase**, tag `boba_batches`. Every tap adds one.
  - Output linked to `boba_batches` (the big number under *Batches logged*). Keep it on the same page as the button: the button counts on from the value the page shows.
  - Table, type **History table**, date range **Last day**, Realtime **off**, **Date Range** on (the page gets a range list, a date picker and an export button). Columns: **Cooked at** (timestamp, format left empty so every tap keeps its own row) and **Batch #** (variable `boba_batches`).
- Colours: background `#FFF3DC`, button `#7B4B2A` with white text, number `#7B4B2A`, table header `#F4E3C8`, selection `#D9A066`.

## 內容說明

- FUXA Server 上的 tag `boba_batches`：number。**Tag options** 三個開關都打開（**Registration Enabled**、**Save if changed**、**To restore**），**Save value interval** 設 **0**：值一變，FUXA 就連同時間存一筆。
- 頁面 `Boba log`（1024 × 768）：
  - 按鈕 **New batch**（320 × 120）：Events → **Click**、**Set Value**、值 **1**、function **increase**、tag `boba_batches`。每按一下加 1。
  - Output 連 `boba_batches`（*Batches logged* 下面的大數字）。要和按鈕放同一頁，按鈕才會從頁面上的數字接著加。
  - 表格，type **History table**、date range **Last day**、Realtime **關**、**Date Range** 開（頁面上會有天數選單、選日期和匯出按鈕）。欄位：**Cooked at**（timestamp，格式留空，每按一下都是獨立一列）和 **Batch #**（variable `boba_batches`）。
- 配色：背景 `#FFF3DC`、按鈕 `#7B4B2A` 白字、數字 `#7B4B2A`、表格標題列 `#F4E3C8`、選取 `#D9A066`。

## Good to know

- The table does not refresh by itself: tap the refresh icon at the top right of the table. Do not turn **Realtime** on for this: a History table in Realtime adds a row every second, even when nobody taps.
- **Last 3 days** shows more; the clock icon picks any dates; the arrow downloads the rows as a CSV file (`data.csv`) for a spreadsheet or an inspection.
- A brand-new tag shows `NaN` until the first tap; after that the number counts up.
- Every time FUXA starts, the table gets one or two extra rows with the start-up time and the last number. That is FUXA saving its starting value, not a pot of boba.
- On iPad Safari the refresh icon may be drawn outside the table (above the number). It still works; Chrome on a computer or an Android tablet shows it in the right place.
- Anyone on the same network can open these pages. Do not forward the port on your router; if you need it from outside, connect through a VPN.

## 要知道的事

- 表格不會自己更新：按表格右上角的重新整理圖示。不要為了這個打開 **Realtime**：History table 開了 Realtime 會每秒自己加一列，沒人按也一樣。
- **Last 3 days** 可以看更多天；時鐘圖示可以選任何日期；箭頭會把紀錄下載成 CSV 檔（`data.csv`），可以放進試算表或給稽查看。
- 新建的 tag 在第一次按之前會顯示 `NaN`，按過之後就會正常往上加。
- 每次 FUXA 啟動，表格會多一兩列啟動時間、數字是上一次的值。那是 FUXA 存起始值，不是多煮了一鍋。
- iPad 的 Safari 可能會把重新整理圖示畫在表格外面（數字上方），一樣按得到；電腦的 Chrome 或 Android 平板會顯示在正確位置。
- 同一個網路裡的人都打得開這些頁面。不要在路由器上開轉送埠；要從外面連，請透過 VPN。

# EP2 · Opening hours (Time Scheduler)

At closing time, with nobody touching anything, the door sign turns to CLOSED.
Video: *Nobody Touched It. My Sign Flipped to Closed (FUXA Time Scheduler)*

打烊時間一到，沒人碰，門牌自己變成 CLOSED。

## Files

| File | What it is |
|---|---|
| `opening-hours.json` | The FUXA project after this episode: EP1's phone menu (`MainView`) and door sign, plus tag `open_hours`, the page `Opening hours` with a Time Scheduler, and the red CLOSED layer on `Door sign` |

Made and tested with FUXA 1.3.5. Only want the starting point? Use EP1's file: [../ep1-door-sign](../ep1-door-sign/).

## Open it in FUXA

1. In the FUXA editor, open the save menu (top left) and choose **Save Project As** to keep a copy of your current project. Opening this file **replaces** the project you have open.
2. In the same menu choose **Open Project** and pick `opening-hours.json`.
3. **Add your hours.** The opening hours are not stored in the project file. Open `http://YOUR-PC-IP:1881/view?name=Opening%20hours`, click **+**, pick the start and end time with the clock icons, tick the days, then **Save Schedule** and **Confirm**. Until you do, the sign stays CLOSED.
4. Open the pages from any phone or tablet on the same Wi-Fi (use your computer's IP, not `localhost`; 1881 is FUXA's default port):
   - Phone menu: `http://YOUR-PC-IP:1881/home`
   - Door sign: `http://YOUR-PC-IP:1881/view?name=Door%20sign`

## 匯入方式

1. 在 FUXA 編輯器左上角打開存檔選單，先按 **Save Project As** 備份目前的專案。開啟這個檔案會**取代**你目前的專案。
2. 同一個選單按 **Open Project**，選 `opening-hours.json`。
3. **加上你的營業時間。** 營業時間不存在專案檔裡。打開 `http://你的電腦IP:1881/view?name=Opening%20hours`，按 **+**，用時鐘圖示選開始和結束時間、勾星期，再按 **Save Schedule**、**Confirm**。還沒加之前，門牌會一直是 CLOSED。
4. 用同一個 Wi-Fi 的手機或平板打開（用電腦的 IP，不是 `localhost`；1881 是 FUXA 預設埠）：
   - 手機選單：`http://你的電腦IP:1881/home`
   - 門牌：`http://你的電腦IP:1881/view?name=Door%20sign`

## What is inside

- Tag `open_hours` on FUXA Server: boolean. The Time Scheduler sets it to **1 (true) at the start time** and back to **0 (false) at the end time**.
- Page `Opening hours` (1024 x 768): one Time Scheduler (588 x 640, centered). Its device `Opening hours` is linked to `open_hours`.
- Page `Door sign`: EP1's sign, plus three items drawn last so they sit on top: a red rectangle over the whole page (`#B92D3A`), `CLOSED` and `See you tomorrow` in white. Each has two rules: `open_hours` **0 to 0 Show**, **1 to 1 Hide**.

The rule this gives you: outside opening hours the sign is always CLOSED; during opening hours the phone decides (Open / Back in 5 min / Closed from EP1 still work).

| Time | `open_hours` | Sign |
|---|---|---|
| During opening hours | 1 | whatever the phone picked |
| After hours, and days you did not tick | 0 | CLOSED |

## Good to know

- The schedule runs on the computer running FUXA, even with every browser closed. Keep that computer on: set its power to **never sleep**, and make sure its clock is right.
- Do not switch `open_hours` by hand: the scheduler sets it back to what the hours say.
- Anyone on the same network can open these pages. Do not forward the port on your router; if you need it from outside, connect through a VPN.

## 要知道的事

- 排程在跑 FUXA 的那台電腦上執行，瀏覽器全部關掉也照跑。那台電腦要一直開著：電源設定改成**永不睡眠**，時間也要對。
- 不要手動切 `open_hours`：排程會把它改回營業時間該有的值。
- 同一個網路裡的人都打得開這些頁面。不要在路由器上開轉送埠；要從外面連，請透過 VPN。

# EP1 · Door sign (Select value)

Pick a state on your phone, and the tablet at the door changes.
Video: *I Replaced My "Back in 5 Minutes" Note with This (FUXA Select Value)*

在手機上選一個狀態，門口的平板就跟著換。

## Files

| File | What it is |
|---|---|
| `door-sign.json` | The FUXA project built in the video: tag `door_mode`, the phone menu (`MainView`), the sign (`Door sign`), and a left sidebar with both pages |

Made and tested with FUXA 1.3.5.

## Open it in FUXA

1. In the FUXA editor, open the save menu (top left) and choose **Save Project As** to keep a copy of your current project. Opening this file **replaces** the project you have open.
2. In the same menu choose **Open Project** and pick `door-sign.json`.
3. Open the pages from any phone or tablet on the same Wi-Fi (use your computer's IP, not `localhost`; 1881 is FUXA's default port):
   - Phone menu: `http://YOUR-PC-IP:1881/home`
   - Door sign: `http://YOUR-PC-IP:1881/view?name=Door%20sign`

## 匯入方式

1. 在 FUXA 編輯器左上角打開存檔選單，先按 **Save Project As** 備份目前的專案。開啟這個檔案會**取代**你目前的專案。
2. 同一個選單按 **Open Project**，選 `door-sign.json`。
3. 用同一個 Wi-Fi 的手機或平板打開（用電腦的 IP，不是 `localhost`；1881 是 FUXA 預設埠）：
   - 手機選單：`http://你的電腦IP:1881/home`
   - 門牌：`http://你的電腦IP:1881/view?name=Door%20sign`

## What is inside

| Value | Menu label | Sign | Color | Text |
|---|---|---|---|---|
| 0 | Open | OPEN / Come on in | `#2e7d32` green | white |
| 1 | Back in 5 min | BACK IN 5 MIN / Be right back | `#f9a825` yellow | black |
| 2 | Closed | CLOSED / See you tomorrow | `#c62828` red | white |

- Tag `door_mode`: number, initial value 0, **To restore** on, so the state survives a restart.
- The sign is one rectangle (colored by `door_mode`) and six lines of text. Each line shows on its own value and hides on the others. In the editor the six lines sit on top of each other; at run time only one pair shows.

## Keep it on your own network

Anyone on the same network can open these pages and change the sign. Do not forward the port on your router; if you need it from outside, connect through a VPN.

同一個網路裡的人都能打開這兩頁、改門牌。不要在路由器上開轉送埠；要從外面連，請透過 VPN。

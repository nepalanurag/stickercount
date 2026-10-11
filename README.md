# StickerCount

A Monopoly GO! sticker counter that runs entirely in your browser.

Live app: https://nepalanurag.github.io/stickercount/

## What this is

Tracking a sticker album by hand is tedious, so I built a page that reads the album screenshots for you. Take photos of your sticker album pages, and it tells you which stickers you are missing and which extras you have. Everything runs on-device; nothing is uploaded anywhere.

## What it does

- You select up to 24 album-page screenshots (the page enforces the cap).
- For each page it OCRs the strip at the bottom to read the set number (Tesseract.js, in the browser).
- Then it checks each of the 9 sticker slots: a slot counts as owned if more than 10% of its sampled pixels are colorful (missing stickers are grey silhouettes), and it counts as an extra if the duplicate-count badge area is mostly white.
- It lists your missing stickers and extras per set, shows a debug view of the analyzed pages, and includes a trade matcher: paste another player's missing/extra list and it tells you which stickers you can give or receive.

The grid coordinates are calibrated for a Pixel 9 screenshot (1080x2424) and scaled to any image size, so other screenshots work too. The only network use is the Tesseract.js and Tailwind CDNs; your images never leave the browser.

## How to run

There is no build step and no server. Just open `index.html` in a browser (or use the live link above). It needs internet access for the CDNs.

## Methods in plain words

No machine learning beyond the OCR: the trick is that Monopoly GO draws missing stickers as grey silhouettes, so "has color" is a surprisingly good ownership test. The set number comes from reading the page's bottom strip, and the trade matcher is plain set intersection against a pasted list.

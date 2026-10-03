# StickerCount

A Monopoly GO! sticker counter that runs entirely in your browser.

Take a photo of a sticker album page and it counts what you have and what you still need, using on-device OCR (Tesseract.js). Nothing is uploaded anywhere.

Just open `index.html` in a browser (it needs internet access for the Tesseract.js CDN).

## What it does

From reading the code (the OCR pipeline needs a browser with images, so this walkthrough is from the source, which passes a syntax check):

- You select up to 24 album-page screenshots (the page enforces the cap). The grid coordinates are calibrated for a Pixel 9 screenshot (1080x2424) and scaled to any image size.
- For each page it OCRs the strip at the bottom to read the set number, then checks each of the 9 sticker slots: a slot counts as owned if more than 10% of its sampled pixels are colorful (missing stickers are grey silhouettes), and as an extra if the duplicate badge area is mostly white.
- It lists your missing stickers and extras per set, shows a debug view of the analyzed pages, and has a trade matcher: paste another player's missing/extra list and it tells you which stickers you can give or receive.

## Sample run

No live run was done here since the OCR needs real album screenshots in a browser. The flow for a set page looks like this in the results panel:

```
Missing
Set 21: 1, 3, 4

Extras
Set 21: 8
```

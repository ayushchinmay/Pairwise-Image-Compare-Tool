# Pairwise Image Ranker

Rank a batch of image variations by comparing two at a time. Get your top 3, with their settings.
One HTML file. Runs in your browser. Images are never uploaded. This tool was initially created to compare and rank images generated using ComfyUI.

## Quick start

1. Open `comfyui_pairwise_image_ranker.html` in Chrome, Edge or Firefox.
2. Drop your images on the drop zone.
3. Click **Start Comparison Rounds**.
4. Pick the better image each round: click it, or press **←** / **→**. Too close? Press **↓** for a tie.
5. Read your top 3. Export. Click **Clear Gallery** for the next batch.

No images handy? Click **Load Sample Batch**.

## Keys

| Key | Does |
|---|---|
| **←** / **→** | Pick left / right |
| **↓** | Tie (each image gets half a point) |
| **M** | Magnifier on/off |
| Mouse wheel over an image | Magnifier zoom (while it's on) |
| **Space** (hold) | Peek at specs while in Blind Mode |
| **Ctrl+Z** / **⌘Z** | Undo last pick |
| **Esc** | Close the inspector |

## Modes

| Mode | Use when |
|---|---|
| **Round-Robin** (default) | 5–10 images. Every pair once. Most reliable. |
| **Fast Tournament Sort** | 10+ images. Fewer clicks. Every image gets its own rank (no shared ranks). |

## During voting

- **Blind Mode** is on by default: filenames, models and settings are hidden. Hold **Space** to peek. Settings are context only; they never affect the ranking.
- **Magnifier:** hover one image and the same spot is magnified on both. Scroll to zoom from 1.5× to 12×.
- **Layout:** Side-by-Side for portrait. Stacked for landscape and ultra-wide.
- **Sizing:** Fill Card Width = biggest image. Fit Screen Height = no scrolling.

## Results

- **Rank Score:** `#1 (4W - 1L - 1T, 75%)`. A tie counts as half a win.
- **Shared ranks (`#3=`):** images on equal points share a rank. Their head-to-head result separates them if there is one.
  - Circular picks (A beat B, B beat C, C beat A) stay level, since you rated them equally. Nothing asks you to redo them.
  - If a shared rank crosses the top-3 cut, a note names the tied images. Pick whichever you prefer.
- **Top-3 cards:** Filename, Rank Score, Model, Seed, Sampler, Steps, Denoise (if present), Input Prompt.
- **Shared Input Prompt:** read from the PNGs. Editable. Your edit goes into every export.
- **Exports:**
  - **Copy Top-3 Info** puts plain text on your clipboard.
  - **Save Top-3 Report** saves `comfyui_top3_report.md`.
  - **Save Top-3 (.csv)** saves `comfyui_top3.csv`.

## Comparing models

Put several models in one batch, using the same prompt.

- **Model Performance Breakdown:** how each model did in this batch. W–L–T counts only matches against *other* models.
- **Log Batch to Leaderboard:** adds the batch to the **All-Time Model Leaderboard**. One log per run.
- **Clear Leaderboard:** click twice to wipe it.

## Saved automatically

- **Your batch and progress survive a refresh.** Reopen the file and you're back on the same round or results.
  - This covers images, picks, ties, the prompt edit and view settings.
- **Clear Gallery** deletes the saved batch.
- **The leaderboard** is saved too, and persists until you clear it.
- Saving is per browser. A different browser or a private window starts empty.

## Image Metadata

Read from **PNG** files saved by ComfyUI: model, seed, steps, CFG, sampler, scheduler, denoise, LoRAs, noise aug and prompt. A1111/Forge PNGs work too.

Shows **"Not detected"** or **"—"**? The file is a WebP or JPEG, or it was re-saved or sent through a chat app (that strips metadata). Use the original from ComfyUI's output folder.

## Troubleshooting

| Problem | Fix |
|---|---|
| Arrow keys don't vote | Click an empty spot on the page first. |
| Added or removed an image mid-ranking | The ranking resets, since the batch changed. Start again. |
| Prompt is wrong or empty | Type it into the Shared Input Prompt box. |
| No icons | You're offline. Everything else still works. |
| "Could not save this batch" message | Browser storage is full or blocked. Ranking still works; it just won't survive a refresh. |

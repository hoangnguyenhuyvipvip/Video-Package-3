# VIDEO PACKAGE 3 — PRODUCTION PROCESS

### AI-Powered Content Replication Pipeline
**Kpop Aesthetic · Instagram Reels · Automated Production**

---

| Field | Details |
|-------|---------|
| **Source Channel** | @beaonshelf (Instagram) |
| **Content Type** | Short-form vertical video (Reels) |
| **Total Outputs** | 168 images + 164 videos |
| **Pipeline** | Scraping → Analysis → Prompting → Generation |
| **Date** | August 2026 |

---

## Table of Contents

1. [Overview](#1-overview)
2. [Step 1: Data Scraping](#2-step-1-data-scraping)
3. [Step 2: Thumbnail Analysis](#3-step-2-thumbnail-analysis)
4. [Step 3: Image Prompt Engineering](#4-step-3-image-prompt-engineering)
5. [Step 4: Batch Image Generation](#5-step-4-batch-image-generation)
6. [Step 5: Video Action Analysis](#6-step-5-video-action-analysis)
7. [Step 6: Batch Video Generation](#7-step-6-batch-video-generation)
8. [Tools & Technologies](#8-tools--technologies)
9. [Output Summary](#9-output-summary)

---

## 1. Overview

This document outlines the end-to-end production process for **Video Package 3** — an AI-powered content pipeline that replicates the visual style and character actions from an existing Instagram channel into a new, original character-based content series.

The pipeline transforms reference content from **@beaonshelf** into two categories of output:

- **Thumbnail Images** — AI-generated character images matching the composition, style, and aesthetic of the original thumbnails
- **Short-form Videos** — AI-generated character videos replicating the movements, gestures, and actions of the original content

### Pipeline Flow

```
  IG Scraping  →  Visual Analysis  →  Prompt Engineering  →  AI Generation  →  Output
```

**Two parallel tracks** run through this pipeline:

> **🖼 Image Track:** Scrape thumbnails → Analyze visual attributes → Generate image prompts (ChatGPT) → Batch generate images (Codex)

> **🎬 Video Track:** Scrape videos → Analyze character actions → Generate video prompts → Batch generate videos (Claude Code + Google Cloud)

---

## 2. Step 1: Data Scraping

### `STEP 1` — Instagram Data Extraction
*Collecting raw content from the source channel*

### Source

| Property | Value |
|----------|-------|
| **Platform** | Instagram |
| **Account** | @beaonshelf |
| **URL** | https://www.instagram.com/beaonshelf/ |
| **Content Type** | Reels (short-form vertical video) |
| **Total Posts Scraped** | 168 Reels |

### What is Collected

- **First frame / thumbnail image** of each Reel → saved as individual `.jpg` files
- **Reel URL** for each post → stored for reference and traceability
- **Video content** of each Reel → downloaded for action analysis (Step 5)

### Tool Used

A custom scraping agent is deployed to automatically extract all Reels from the target account. The agent navigates the account's Reels tab, captures each post's thumbnail (first frame), downloads the video file, and records the post URL.

### Output

- `first_frames.zip` — 168 thumbnail images (first frame of each Reel)
- Video files — 168 downloaded Reels for action analysis
- Reel URLs — stored in the Excel file (Step 2, column C: Instagram Reel URL)

---

## 3. Step 2: Thumbnail Analysis

### `STEP 2` — Visual Attribute Extraction
*Breaking down each thumbnail into structured visual data*

Each of the 168 scraped thumbnails is analyzed to extract a comprehensive set of visual attributes. This structured data becomes the foundation for generating accurate image prompts later.

### Extracted Attributes

| Category | Description |
|----------|-------------|
| **Shirt/Top Type** | Type of top garment (tee, crop top, hoodie, etc.) |
| **Shirt Pattern & Color** | Pattern style and color palette of the top |
| **Fit Type** | How the garment fits (slim, oversized, fitted, etc.) |
| **Full Outfit Description** | Complete outfit details including accessories |
| **Style & Aesthetic** | Overall visual style (coquette, streetwear, Y2K, etc.) |
| **Composition & Layout** | How elements are arranged in the frame |
| **Shape & Framing** | Body/face framing and crop style |
| **Camera Angle & Distance** | Selfie, mid-shot, wide, high/low angle, etc. |
| **Action / Scenario** | What the subject is doing in the thumbnail |
| **Facial Expression** | Specific expression (smiling, neutral, surprised, etc.) |
| **Specific Gesture** | Hand positions, poses, or body language |
| **Face Angle (L/R)** | Direction the face is turned |
| **Vertical Tilt** | Up/down tilt of the head |
| **Location** | Setting (bedroom, outdoor, studio, etc.) |
| **Background Details** | Specific elements visible behind the subject |
| **Lighting (Day/Night)** | Lighting conditions and time of day |

### Output

- Excel file — **Step 1 sheet, columns C through R**: all 16 visual attributes for each of 168 thumbnails
- Each row corresponds to one Reel, identified by the filename in column A

---

## 4. Step 3: Image Prompt Engineering

### `STEP 3` — AI Image Prompt Generation
*Creating safe, accurate prompts using ChatGPT*

Using the structured visual data from Step 2, each thumbnail's attributes are combined with a pre-established character reference prompt to generate a complete image generation prompt.

### Process

**1. Character Identity Prompt** — A base prompt describing the AI-generated female character's consistent physical features (skin tone, eye color, hair style, facial structure) is pre-defined. This ensures visual consistency across all 168 generated images.

**2. Attribute Integration** — Each thumbnail's 16 extracted attributes (outfit, pose, composition, lighting, etc.) are merged with the character identity prompt to form a complete, detailed image prompt.

**3. Compliance Filtering** — ChatGPT reviews and adjusts each prompt to ensure it does not contain any language that violates image generation platform policies (no explicit, suggestive, or inappropriate content). The character is described as fully clothed, wholesome, and everyday in every prompt.

**4. Prompt Formatting** — Final prompts follow a consistent structure:
```
format/orientation → character identity → wardrobe → style → composition → action → expression → location → lighting
```

### Key Principle

> *Every prompt must produce an image that matches the original thumbnail's composition and style, while using a completely new AI-generated character — without triggering any content policy violations on the generation platform.*

### Output

- Excel file — **Step 1 sheet, column S (Image Prompt)**: 168 complete, policy-compliant image prompts

---

## 5. Step 4: Batch Image Generation

### `STEP 4` — Automated Image Generation via Codex
*Scaling from prompts to 168 finished thumbnails in one batch*

With all 168 image prompts ready in the Excel file, the next step is to generate the actual images at scale using an automated pipeline.

### Process

**1. Prompt Extraction** — All 168 image prompts are extracted from the Excel file (column S) and formatted for batch submission.

**2. Codex Batch Execution** — The prompts are submitted to Codex (OpenAI's agent platform) in a single batch run. Codex processes each prompt sequentially, generating one image per prompt through an image generation model.

**3. Output Collection** — Generated images are collected, numbered (`001.png` through `168.png`), and stored in the Output Images folder.

**4. Quality Review** — Images are reviewed for character consistency, composition accuracy, and overall quality against the original thumbnails.

### Why Codex?

- Handles batch processing of multiple prompts in a single automated run
- Eliminates the need to manually submit 168 individual prompts
- Maintains consistent execution and output format across the full batch

### Output

- `Output Images/` — 168 AI-generated character thumbnail images
- Excel file — **Step 1 sheet, column T**: embedded thumbnail preview of each output image

---

## 6. Step 5: Video Action Analysis

### `STEP 5` — Character Action & Movement Extraction
*Analyzing the first 5 seconds of each Reel for character behavior*

The same scraping agent used in Step 1 is now applied to analyze the video content itself. The focus is on extracting the female character's specific actions, movements, gestures, and expressions during the first 5 seconds of each Reel.

### Analysis Breakdown

For each of the 168 videos, the agent produces:

- **On-screen visibility duration** — How long the character appears before a screen cut/transition
- **Frame-by-frame action breakdown** — Second-by-second description of the character's movements
- **Expression tracking** — Changes in facial expression throughout the clip
- **Gesture details** — Hand positions, head tilts, body language shifts
- **Summary** — Condensed description of the overall action sequence

### Prompt Conversion

The detailed action analysis is then distilled into a simplified video prompt that captures the essential character movement in a concise, generation-ready format. This conversion focuses on:

- Core body movement and posture changes
- Key expression transitions
- Camera-relative positioning
- Removing unnecessary narrative detail while preserving motion accuracy

### Output

- Excel file — **Step 2 sheet, column C (Female Character's Action)**: detailed frame-by-frame analysis
- Excel file — **Step 2 sheet, column D (Video Female Character's Prompt)**: simplified video generation prompt

---

## 7. Step 6: Batch Video Generation

### `STEP 6` — Automated Video Creation
*Claude Code + Google Cloud Console for scalable video generation*

The final production step uses an automated pipeline to generate all output videos from the simplified video prompts created in Step 5.

### Architecture

| Component | Role |
|-----------|------|
| **Claude Code** | Orchestration layer — reads prompts from Excel, manages the generation queue, handles API calls, and collects outputs |
| **Google Cloud Console** | Video generation backend — provides the AI video generation model (Veo / Imagen Video) via API |
| **Thumbnail Images** | Each video uses the corresponding Step 4 output image as the character's visual reference / first frame |

### Process

**1. Prompt Loading** — Claude Code reads all 168 video prompts from the Excel file (Step 2, column D).

**2. API Integration** — Claude Code connects to Google Cloud's video generation API, submitting each prompt along with the corresponding thumbnail image as a visual anchor.

**3. Batch Execution** — Videos are generated in batch, producing short clips (~5 seconds) that match the character's actions described in each prompt.

**4. Output Collection** — Generated videos are numbered (`001_v1.mp4` through `168_v1.mp4`) and stored in the Output Videos folder.

### Output

- `Output Videos/` — 164 AI-generated character videos
- Excel file — **Step 2 sheet, column E**: embedded first-frame thumbnail of each output video
- 4 videos not generated (124, 156, 160, 164) due to source video unavailability

---

## 8. Tools & Technologies

| Tool | Purpose |
|------|---------|
| **Custom Scraping Agent** | Instagram data extraction (thumbnails, videos, URLs) |
| **AI Vision Analysis** | Thumbnail visual attribute extraction (16 categories) |
| **ChatGPT (OpenAI)** | Image prompt engineering with compliance filtering |
| **Codex (OpenAI)** | Batch image generation from prompts |
| **Claude Code (Anthropic)** | Video generation orchestration and Excel automation |
| **Google Cloud Console** | Video generation API backend (Veo / Imagen Video) |
| **Python + openpyxl** | Excel file processing, image embedding, data management |
| **FFmpeg** | Video frame extraction for thumbnails |
| **GitHub + Git LFS** | Output hosting and version control |

---

## 9. Output Summary

### Deliverables

| Deliverable | Details |
|-------------|---------|
| **Video Package 3 Process.xlsx** | Master Excel file with all data, embedded images, and GitHub hyperlinks |
| **Output Images** (168 files) | AI-generated thumbnail images in Kpop aesthetic style |
| **Output Videos** (164 files) | AI-generated character videos matching source actions |
| **Output Videos.zip** | Compressed archive of all videos for easy download |

### GitHub Repository

| Property | Value |
|----------|-------|
| **Repository** | Video-Package-3 |
| **URL** | https://github.com/hoangnguyenhuyvipvip/Video-Package-3 |
| **Excel File** | `Video Package 3 Process.xlsx` (with clickable links) |
| **Images Folder** | `Output Images/` (168 PNG files) |
| **Videos Folder** | `Output Videos/` (164 MP4 files) |
| **Videos Archive** | `Output Videos.zip` (344 MB, Git LFS) |

### Excel File Structure

**Step 1 Sheet (Image Pipeline):**
- Column A: Source image filename
- Column B: Embedded source thumbnail
- Columns C–R: 16 visual attribute categories
- Column S: Full image generation prompt
- Column T: Embedded output image
- Column U: Clickable GitHub link to output image

**Step 2 Sheet (Video Pipeline):**
- Column A: Video number
- Column B: Embedded source thumbnail
- Column C: Detailed character action analysis
- Column D: Simplified video generation prompt
- Column E: Embedded output video thumbnail
- Column F: Clickable GitHub link to output video

---

*End of Process Documentation*

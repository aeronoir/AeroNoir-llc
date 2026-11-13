---
name: phone-video-editor
description: Edit short videos for a creator who only has a phone and works entirely inside this chat. Use whenever the user sends a video, asks for an edit, captions, cutting retakes, or a Reel/TikTok/Short. The user is the director.
---

# Phone Video Editor

The user only has a phone. Everything happens in this chat. Never ask them to do anything technical. They are the director.

## Rules

1. **Ask 3 questions before every edit** (all at once, short):
   - Where is this video going: Instagram, TikTok, or YouTube?
   - What should the viewer do at the end?
   - Captions and graphics, or a clean cut?
2. **Use your own workspace to edit.** Check for the tools you need (ffmpeg, ffprobe, Whisper) and install anything missing yourself. Do the work in the scratchpad folder.
3. **Never change the original.** Always send back a new file with a new name, e.g. `name_edit_v1.mp4`.
4. **Find retakes by transcribing with Whisper** (faster-whisper). If it can't run (the speech model may fail to download), ask the user to paste the auto captions from Instagram, TikTok, or CapCut and use those. Keep only the best take of each sentence. Cut pauses longer than 0.5 seconds.
5. **Make it look like them.** Ask once for their 2 brand colors and a font, save them in `brand.json` next to this file, and never ask again. Read it at the start of every edit.
6. **Export vertical 9:16 (1080x1920)** for Reels and TikTok, at the highest quality the source allows (H.264, high bitrate, AAC 192k, `-movflags +faststart`).
7. **If the video is too big to upload,** explain simply how to trim or split it in their phone first (Photos > Edit > drag the yellow handles, or split in CapCut). Short clips work best.
8. **Be honest.** If the video is too dark or the audio is too rough, say so, and say whether reshooting would look better.
9. **When finished, send the video back** so they can download it, and remind them to watch it once before posting.

## Workflow

Ask 3 questions -> check tools -> read brand.json (ask once if empty) -> check quality (brightness, audio level; be honest) -> transcribe or use pasted captions -> cut retakes and pauses -> captions in brand style -> export 9:16 -> send file + "watch it once before posting."

## Caption recipe (ffmpeg)

Burn captions with `drawtext` (or `subtitles` with an .ass file), brand font, brand text color, brand accent as box or highlight, lower-middle of frame, 2 lines max, safe margins away from app buttons.

## Brand

Read `brand.json` in this folder. Fields: `color_1`, `color_2`, `font`, `font_file`.

# Short-form video hooks 2026: how the biggest creators open a Reel, TikTok or Short

Time of the first cut, editing pace, speech in the first seconds, on-screen text on the first frame and cross-posting of **167 public short videos** from 21 large creators, measured on 2026-11-17. One row per video, measured from the delivered files.

Full write-up with charts: [Short-form video hook study 2026](https://shortformkit.com/short-form-video-hook-study-2026/) (German: [Studie Hooks](https://shortformkit.com/de/studie-hooks-reels-tiktok-shorts-2026/))

## Key findings

| | Instagram Reels | TikTok | YouTube Shorts | All |
|---|---|---|---|---|
| Videos | 57 | 51 | 59 | 167 |
| First cut, median (videos with a cut) | 2.5 s | 2.7 s | 2.5 s | 2.6 s |
| First cut within 1 s | 18 % | 14 % | 10 % | 14 % |
| First cut within 3 s | 47 % | 53 % | 58 % | 53 % |
| No visible cut | 19 % | 8 % | 10 % | 13 % |
| Shot length, median | 2.2 s | 3.1 s | 2.3 s | 2.3 s |
| Cuts per minute, median | 25.5 | 16.9 | 25.4 | 25.2 |
| Sound from the first frame | 95 % | 96 % | 95 % | 95 % |
| Spoken videos | 70 % | 75 % | 81 % | 75 % |
| Speech within 2 s (of spoken) | 90 % | 82 % | 81 % | 84 % |
| Text on the first frame | 54 % | 63 % | 58 % | 58 % |
| Same cut also on another platform (lower bound) | 49 % | 45 % | 47 % | 47 % |

- **The first cut comes after about 2.6 seconds.** Only 14 % of videos cut within the first second, so the common advice "cut in the first second" is not what the biggest creators do.
- **After the opening, the edit is fast:** median shot length 2.3 s, about 25 cuts per minute. TikTok is calmer (3.1 s per shot).
- **They talk early.** 75 % of videos are spoken, and 84 % of those have speech within the first 2 seconds.
- **58 % show edited-in text on the first frame.**
- **At least 47 % of videos ran as the same cut on another platform.**

## Files

- `data/videos.csv`: one row per video
- `data/summary.json`: the aggregated figures above, per platform

| Column | Meaning |
|---|---|
| platform | instagram, tiktok or youtube |
| creator | account name |
| url | public post URL |
| upload_date | YYYYMMDD, when reported |
| views, likes | counts at measurement time, when reported |
| duration | seconds |
| w, h | resolution of the analysed file (pixels) |
| first_cut | time of the first cut in seconds (empty = no visible cut) |
| cuts_first3 | number of cuts in the first 3 seconds |
| cuts_per_min | cuts per minute over the whole video |
| audio_onset | seconds until audio is above -45 dB |
| talking | at least 6 different words in the first 15 seconds |
| speech_2s | at least 2 confirmed words in the first 2 seconds |
| text_first_frame | text added in editing visible at 0.3 s (judged by eye) |
| cross_posted | same video found on another platform of the same creator |
| measured_at | UTC timestamp of the measurement |

## Method

167 public videos (57 Instagram Reels, 51 TikToks, 59 YouTube Shorts) from 21 large creators in entertainment, food, sports, tech and education. For each creator the 3 newest short videos per platform as listed on 2026-11-17 (pinned posts skipped). 170 were collected; 2 could not be downloaded and 1 was a photo slideshow, so 167 remain. Videos were fetched logged out from a residential connection in Switzerland.

- **Cuts:** ffmpeg scene detection (`scdet`, threshold 8); several triggers within 0.4 s count as one cut; checked by eye on contact sheets. Flashes and zooms inside one shot are not cuts.
- **Speech:** whisper large-v3-turbo on the first 2.0 seconds, words confirmed against the transcript of the first 15 seconds. First-word timestamps from Whisper were not reliable enough to publish, so we report "speech within 2 s" instead.
- **Text on the first frame:** the frame at 0.3 s of every video judged by eye. Text added in editing counts; logos, packaging, signs and ad labels do not.
- **Cross-posting:** same creator, length within 0.7 s and mostly the same words (or the same first cut for videos without speech). A lower bound, because only the 3 newest videos per platform were taken.

Limits: big creators are not every creator, and this shows what they do, not what makes a video perform. Read it as a snapshot, not a census.

## License and citation

Data: [CC BY 4.0](LICENSE). Please credit and link:

> Shortform Kit, "Short-form video hook study 2026", measured 2026-11-17. https://shortformkit.com/short-form-video-hook-study-2026/

Related dataset: [Short-form video delivery 2026](https://github.com/shortformkit/short-form-video-delivery-2026) (resolution, codec, bitrate and loudness of 135 Reels, TikToks and Shorts).

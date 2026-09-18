# Project story

This project was made mainly for personal usage to download songs from Youtube because all the web downloaders were filled with ads and need premium subscription for high quality. I later made removed the regex restrictions that made it a Youtube only downloader, not it downloads any media that yt-dlp supports, better command-line process, and published to Github to help anyone who needs an open-source media downloader. Feel free to use this program and modify as you wish.

# MediaDown

A small, homemade video/audio downloader. It's a friendly wrapper around
[`yt-dlp`](https://github.com/yt-dlp/yt-dlp), so it can grab video (MP4) or
audio (MP3) from any site `yt-dlp` supports.

## Supported sites

Downloading is handled by `yt-dlp`, which supports thousands of sites,
including:

- YouTube
- TikTok
- Instagram
- Twitter / X
- Facebook
- Twitch (VODs/clips)
- SoundCloud
- Vimeo
- Reddit

[official supported sites reference](https://github.com/yt-dlp/yt-dlp/blob/master/supportedsites.md).
If a site works with `yt-dlp` on its own, it will work here too.

## Requirements

- Python 3.8+
- [`yt-dlp`](https://pypi.org/project/yt-dlp/)
- [`ffmpeg`](https://ffmpeg.org/download.html) — needed to convert to MP3
- [`curl_cffi`](https://pypi.org/project/curl-cffi/) — needed for sites like
  TikTok that require browser impersonation to avoid bot-detection errors

### Installing requirements

```bash
pip install "yt-dlp[default,curl-cffi]"
```

Then install `ffmpeg` for your OS:

Make sure `ffmpeg` ends up on your system `PATH` — the app checks `PATH`
first (and falls back to a couple of common install locations) and will
warn you on startup if it can't find `ffmpeg` at all.

## Usage

```bash
python MediaDown.py --mp4 <link>   # download as video
python MediaDown.py --mp3 <link>   # download as audio
```

| Argument | Description |
|---|---|
| `--mp4 LINK` | Download the given link as an MP4 video |
| `--mp3 LINK` | Download the given link as an MP3 audio file |

Only one of `--mp4` / `--mp3` is needed per run. Files are saved to the
directory you run the command from, named after the video's title.

## Notes

- If you hit an error on a specific site (e.g. TikTok returning an
  "impersonation" warning or a 403), make sure both `yt-dlp` and
  `curl_cffi` are up to date:
  ```bash
  pip install -U "yt-dlp[default,curl-cffi]"
  ```
- Downloads always skip playlists (`noplaylist`) and only grab the single
  video/audio at the given link.

## License

MIT — see [LICENSE](LICENSE) for details.

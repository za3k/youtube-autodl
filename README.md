**youtube-autodl** is a wrapper around youtube-dl, for downloading youtube videos.

**Current status: pre-alpha!** Use at your own risk.

It downloads your favorite youtube channels and playlists, putting them into folders on your computer, laid out how you want.

youtube-dl is designed to run periodically. Run it once a day yourself, or add it to cron.

Features:
- Browse youtube locally. No ads or distracting "maybe you would also like to watch" sidebars.
- Uses standard files and folders. No fancy browser needed.
- Simple YAML-based configuration with reasonable defaults. Just pick your own favorite channels and organize folders how you want. Check out my [example config file](https://github.com/za3k/youtube-autodl/blob/master/config.yaml).
- Relatively fast refresh. Channels and playlist fetch takes seconds. Video download is as fast your internet connection allows.
- Supports downloading channels, playlists, or individual videos. Search support is planned.
- Supports downloading videos to multiple locations. For example, you might want to:
    - save a video to `to_watch/20220708 BobTech - All About Hats.mpv` to watch and then delete once you've seen it
    - save a video to `channels/BobTech/All About Hats.mpv` and `playlists/BobTech/Clothing Playlist/All About Hats.mkv` for long-term storage.
    - let youtube-autodl save a master copy so it never re-downloads a video
- Downloads each file only once, even if you request it multiple times.
- By default, **youtube-autodl** stores only one actual copy of each file on disk, even if you want the file saved multiple places. Deduplication can be configured to use symlinks, hardlinks, or be turned off.
- Manually specify any youtube-dl options that are missing, either globally or for each playlist.
- yt-dlp support

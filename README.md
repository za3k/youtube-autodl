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

### Installation

**youtube-autodl** requires yt-dlp. In addition, install the following python packages: sqlitedict

## FAQ

Q: I want to re-organize my existing downloads. I hate how I set up folders!
A: You turned on the archive, right? Delete the database (.cache.sqlite), archive/ARCHIVE.txt, and all of youtube-dl's folders *except* the archive. Run youtube-autodl again. It will take a little bit to grab the metadata again, but it should re-organize everything.

Q: I already have a ton of downloaded videos. How do I avoid downloading them again when I start using youtube-autodl?
A: 
 - If you just want to avoid downloading them again, set up or share an ARCHIVE.txt file. The easiest way to do this is to use `youtube-dl --download-archive ARCHIVE.txt` when downloading them in the first place. If you didn't do that, you can probably make one for existing video folders with a bash one-liner and some cleverness.
 - If you want youtube-autodl to actively know about existing videos and make organized copies, set `formats.archive` to point to your existing videos. This way, youtube-dl will see your videos as its "master" copy, and simply realize they're downloaded already. (Note, this means youtube-autodl will add new videos to your existing collection when they are downloaded.)

### About

youtube-dlp is written by Zachary "za3k" Vance. It released into the public domain.

Special thanks to the yt-dlp maintainers, who in addition to writing excellent software, took time to answer my many questions.

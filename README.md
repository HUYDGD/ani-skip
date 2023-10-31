<p align=center>
<br>
<a href="http://makeapullrequest.com"><img src="https://img.shields.io/badge/PRs-welcome-darkorange.svg"></a>
<img src="https://img.shields.io/badge/os-linux-darkorange">
<img src="https://img.shields.io/badge/os-mac-darkorange">
<img src="https://img.shields.io/badge/os-windows-darkorange">
<img src="https://img.shields.io/badge/os-android-darkorange">
<br>
</p>

<h1 align="center">ani-skip<h1>

<p align="center">
<img src="https://media.tenor.com/CHVEROnz6hMAAAAC/asta-black-clover.gif">
</p>

<h3 align="center">
A script to automatically skip anime opening sequences, making it easier to watch your favorite shows without having to manually skip the intros each time.
</h3>

**Important:** There's a chance `ani-skip` may not recognize the anime you're watching. It leverages the [aniskip API](https://api.aniskip.com/api-docs). If an anime's episode(s) are missing, you can contribute or request its inclusion on their [discord server](https://discord.com/invite/UqT55CbrbE). 

<br>

## Troubleshooting Errors

Should you run into problems, first ensure you're using the most recent version:

- For Linux, Mac, and Android: 
  ```bash
  sudo ani-skip -U
  ```

- For Windows: 
  Open Git Bash as an administrator and enter:
  ```bash
  ani-skip -U
  ```

If the issue remains unresolved, please create a new issue.

---
## Usage

<pre>
$ ani-skip
ani-skip ["title"] [ep]
# title -> Precise anime title that can be retrieved during anime selection (e.g. <a href="https://github.com/pystardust/ani-cli">ani-cli</a> anime selection)
# ep -> episode number 
</pre>

> `script-opts` with the `script` flag is produced by ani-skip when metadata for a specific anime's opening sequence exists in the database. It's important to append these flags at the end due to certain mpv nuances.

```sh
$ ani-skip "Black Clover (170 episode)" 10
--script-opts=skip-start_time=140.153,skip-end_time=230.153 '--script=/home/user/.config/mpv/scripts/skip.lua'
$ mpv "black_clover_ep10.mp4" $(ani-skip "Black Clover (170 episode)" 10)
```

> `ani-skip-jq` script utilizes `jq` to parse `myanimelist.net` and `api.aniskip.com` json metadata, make sure it's installed before running it.

```sh
$ ani-skip-jq "Black Clover (170 episode)" 10
--script-opts=skip-start_time=140.153,skip-end_time=230.153 '--script=/home/user/.config/mpv/scripts/skip.lua'
$ mpv "black_clover_ep10.mp4" $(ani-skip-jq "Black Clover (170 episode)" 10)
```

## Install

```sh
git clone https://github.com/synacktraa/ani-skip.git
sudo cp ani-skip/ani-skip /usr/local/bin
mkdir -p ~/.config/mpv/scripts && cp ani-skip/skip.lua ~/.config/mpv/scripts/
rm -rf ani-skip
```

*Note:  `skip.lua` script can be used with any video by simply providing it with the `start_time` and `end_time` of the desired section to be skipped.*

## Dependencies

- grep
- sed
- curl
- lua
- mpv - Video Player
- jq (Optional)

## Checklist

- [x] mpv
- [ ] vlc
- [x] MyAnimeList Id scraper

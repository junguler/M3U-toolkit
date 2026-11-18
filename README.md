# M3U-toolkit

it's all the extra little tools one might need for my [m3u-radio-music-playlists](https://github.com/junguler/m3u-radio-music-playlists) repo shoved into one html file, every tool is a tab at the top, i put them in the order i think you'll reach for them (made with claude)

## the tabs

* merge & dedupe - smash as many playlists together as you want and it throws out the duplicates. it knows `http` and `https` of the same stream are the same stream, and keeps whichever copy has the most info
* edit playlist - one big table where you fix titles, groups, countries and logos by hand or all at once, find and replace, sort, move stuff around, and undo for when you mess up (you will)
* track link health - checks every link and remembers what happened, so after a few runs you can tell which streams are really dead and which just had a bad day, then download a playlist without the dead ones. there's also a node script and a github action in there if you want it to run on its own every week
* validate & fix - finds the stuff that quietly breaks players, like a missing `#EXTM3U`, busted `#EXTINF` lines, a BOM, mixed line endings, links with spaces, and fixes what it safely can
* find stations - search [radio-browser.info](https://www.radio-browser.info/) by name, genre, country, language or bitrate, listen to a preview, and add what you like to a playlist, or tack it onto the end of one you already have
* upgrade to https - checks if an `http` stream also works as `https` and swaps it in, matters because https pages like github pages can't play plain http streams
* split playlist - chops one huge playlist into many by group, country, language, first letter, stream type, bitrate, host, or just N stations per file, everything comes as a zip
* compare versions - give it an old and a new version and it shows what got added, removed or changed, and writes a changelog you can paste in a release note
* playlist stats - how many streams you have, how many duplicates, which hosts show up the most, how much is missing logos or groups, and each missing row has a button that gives you just those stations
* browse & play - point it at a github repo and it lists every playlist in there, open one, search the stations and listen right on the page, and playlists opened from a repo get a button to copy the raw link

every tab takes a local file, an online link (the raw file from github for example) or pasted streams, nothing gets uploaded anywhere

## running it

github pages are static, meaning this code runs on your device, it's one html file with no dependencies, so just make a local copy and you don't need the internet for most of it. only find stations and browse & play need a connection (browse & play uses the github api, you get about 60 requests an hour without logging in)

## some stuff you should know

* a browser can't peek inside most radio streams from another site, so track link health can only tell that the server answered, not that there's really audio. upgrade to https actually tries to play the stream to be sure, and tells you what it couldn't confirm
* if you host this on github pages the tabs that test links can't test `http` streams (the browser blocks them), use a local copy for those or the node script from the track link health tab
* the history in track link health lives in your browser, there's an export button so you don't lose it

that's it, this thing is mainly a side helper for my [m3u-radio-music-playlists](https://github.com/junguler/m3u-radio-music-playlists) repo and it'll be linked there too

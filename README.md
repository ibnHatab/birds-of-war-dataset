# birds-of-war-dataset

## web grabber
 - https://snaptik.app/
 - https://ssstwitter.com/

# oneliners
```
# convert to mp3
for f in ls Snap*mp4; do echo $f; ffmpeg -i $f "${f%.mp4}.mp3"; done
# split into 3 sec segments
for f in Snap*mp3; do ffmpeg  -i $f -f segment -segment_time 3.0 -reset_timestamps 1 "split/${f%.mp3}-%02d.wav"; done
# reindex into dataset
ls -1prt | grep -v "/$" | cat -n | while read n f; do mv -n "${f}" "tt-$(printf "%04d" $n).${f#*.}"; done

# FEX:  tt-{dataset index}.{inputfile}-{split index}.wav
#
# Snaptik.app_730653050347205760.mp4 => Snaptik.app_730653050347205760.mp3 =>
#
# tt-0068.app_7306530503472057605-00.wav
# tt-0067.app_7306530503472057605-01.wav
# tt-0069.app_7306530503472057605-02.wav
# tt-0071.app_7306530503472057605-03.wav
# tt-0070.app_7306530503472057605-04.wav
#

```

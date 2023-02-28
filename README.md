# Use ffmpeg to replace background music

```
#!/bin/bash

if [ ! -n "$1" ]
then
  echo "please input video file at \$1"
  exit
fi

if [ ! -n "$2" ]
then
  echo "please input bgm audio file at \$2"
  exit
fi

if [ ! -n "$3" ]
then
  echo "please set output file at \$3"
  exit
fi

duration=`./ffprobe -v error -show_entries format=duration -of default=noprint_wrappers=1:nokey=1 $1`

./ffmpeg -y -an -i $1 -stream_loop -1 -ss 0 -t $duration -i $2 -c:v copy $3
```

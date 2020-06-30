[![ko-fi](https://www.ko-fi.com/img/githubbutton_sm.svg)](https://ko-fi.com/U7U51VFGK)

#### convert HH:MM:SS to SS
    echo "0:25:30" | awk -F: '{ print ($1 * 3600) + ($2 * 60) + $3 }'

#### add chapters:
Chapter data and other metadatda in [id3tags.txt](id3tags.txt)

    ffmpeg -i in.mp3 -i id3tags.txt -map_metadata 1 -c:a copy -id3v2_version 3 -write_id3v1 1 out.mp3

#### use script [chptr](chptr):

Put chapter data in a file (in the example below file is named
_[chapters](chapters)_):

    0:0:14  0:2:15  глава едно
    0:2:16  0:4:10  глава две
    0:4:11  0:6:40  глава три

Format is:

    start_time   end_time    chapter_title

Values are *tab* delimited.
Run script as below:

    ./chptr title="my podcast" artist="the artist formerly known as Prince" \
    pubdate="2019" copyright="cc-by" \
    track="02" mp3=myfile.mp3 meta=chapters
    
Arguments:

    title - episode tile
    artist - podcast name
    copyright - copyright notice 
    track - episode number
    pubdate - publication date
    mp3 - audio file to be chaptered
    meta - name of the file containing chapter data

Order of the arguments does not matter.
Look for output file with_chapters.mp3

   

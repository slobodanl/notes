_Written by: Reza Shams Amiri_
# Best video players

## YouTube players
Youtube can be played by any of these programs:
mplayer, mpv, vlc, and mpsyt(mps-youtube)
     
1. **mpsyt**
   ```bash
   sudo apt install mps-youtube
   ```
   then `mpsyt playurl <url>`

1. **VLC**  
   Use `cvlc --no-video <URL>` or `cvlc --vout none <URL>`
1. **mplayer** and **mpv** [see ref][audio-youtube]  
   `yturl` gets direct media URLs to YouTube media, freeing you having to view them in your browser.  
   First install `yturl` using:
    ``` sh
    sudo pip install -U yturl

    # Or for installing latest github version:

    sudo pip install -U git+https://github.com/cdown/yturl.git@develop
    ```
    then you can use 
    ``` sh
    <your-preferred-player> "$(yturl 'http://www.youtube.com/watch?v=8TCxE0bWQeQ')"
    ```
    **mplayer**:  
    ``` sh
    mplayer -novideo "$(yturl <url>)"
    ```
    **mpv**:  
    ``` sh
    mpv --no-video "$(yturl <url>)"
    ```

* * *
Creation date: _2018-11-09_

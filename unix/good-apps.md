# Good Unix Apps
Here are some good unix apps:
-----------------------------------------

## Bundles

- [75 Most Used Essential Linux Applications of 2018][7MUELAO2]
    Among them I found these useful:
    1. **stacer**: for cleaning up cache and hard
    2. [bleachbit][GBBBSCFWAL]: BleachBit system cleaner for Windows and Linux
    3. [Taskwarrior][TUE]: Manages your TODO list from the command line.

- [awesome-cli-apps][awsome-cli]
   A curated list of command line apps.

   ``` yaml
   See what's available at https://github.com/agarrharr/awesome-cli-apps
   ```

- [Awesome Linux Software][awsome-linux]
   A list of awesome applications, software, tools and other materials for Linux distros.
   ``` yaml
   See what's available at https://github.com/LewisVo/Awesome-Linux-Software
   ```

- [ArchLinux - List of applications](https://wiki.archlinux.org/index.php/List_of_applications)
   ``` yaml
   See what's available at https://wiki.archlinux.org/index.php/List_of_applications
   ```
- [The really big list of really interesting Open Source projects.](https://medium.com/@likid.geimfari/the-list-of-interesting-open-source-projects-2daaa2153f7c)
   Here are you can see the really big list of really interesting Open Source 
   projects on language such as Elixir, Erlang, Haskell, Clojure, Python, Ruby,
   Lua, JS, Go, C++, Swift, Bash, R and etc.


![](https://cdn-images-1.medium.com/max/1500/0*cTQWHAgxA1ikNujZ.png)

``` yaml
See what's available at https://medium.com/@likid.geimfari/the-list-of-interesting-open-source-projects-2daaa2153f7c
```
---

## Shell

- [ShellCheck][shellcheck]
   lint tool for shell scripts
   ``` yaml
   s apt install shellcheck
   ```

---

## Ascii / Ascii Art / Ansi
- [termpix](https://github.com/hopey-dishwasher/termpix)

   Display images in an ANSI terminal  
   ![](https://cloud.githubusercontent.com/assets/4640028/13419797/fa51cb88-dfd4-11e5-87c3-f8620cd67557.png)
   ``` bash
   cargo install --git https://github.com/hopey-dishwasher/termpix
   ```

- [Hollywood][hollywood]

  fill your console with Hollywood melodrama technobabble  
  ![](http://2.bp.blogspot.com/-o0ExO2Cmf84/VJGdBu72YKI/AAAAAAAA5vI/9uL8xWRCpRY/s1600/Screenshot%2Bfrom%2B2014-12-17%2B09%3A10%3A47.png)

  ``` sh
  s apt install hollywood wallstreet
  ```
  also have a look at [Command Line Fu][cmdfu] site.

## Desktop

- [Kupfer][kupfer]  
  Kupfer a dmenu replacement  
  ![](https://kupferlauncher.github.io/kupfer-launch.png)    
  ``` sh
  sudo install kupfer
  ```

- [XFCE app finder][appfinder]  
  XFCE App finder replacing start menu  
  
  ``` sh
  sudo apt install xfce4-appfinder
  ```
# Paint, Image/Graphic applications

   1. Krita
   2. Gimp

# On screen paint

   1. [GitHub - bk138/gromit-mpx][GBGMGMIAMPGPOTOGDATIEGAWSPAOAIALFTIPSIUTXEWA]
      ```
      sudo apt-get install gromit-mpx
      ```
      1. <kbd>F9</kbd> Start/stop annotation
      2. <kbd>shift</kbd><kbd>F9</kbd> Clear annotations
      3. Erase: right click drag
      4. Green (arrow): Middle click drag

# Image previewers

   1. [hiptext](https://github.com/jart/hiptext)
   1. [libsixel](https://github.com/saitoha/libsixel)
   1. [w3mimgdisplay](/usr/lib/w3m/w3mimgdisplay)

# Utilities  

   1. **peco** : quickly filter the output of commands. Consider it to be the interactive version of grep
   2. **ncdu** : terminal storage analyzer 
   3. **hub**  : [hub](https://hub.github.com/) Avoid going to GitHub for pull requests and forks! Perform most of GitHub’s operations from the comfort of the command line.
   4. **tldr** : Simplified man pages. Usage: `tldr wget`
   5. **shellinabox**: use it to perform ssh over http, see [this page for more info][HWTCSIABAWBSTTARLS]

# Font previewers
1. **FontBase**: [https://fontba.se/downloads/linux#][FDFL]
   After downloading the `AppImage` file just make it executable and move it to `/opt` folder and run it.
   ![FontBase.png](/img/unix/FontBase.png)
    After installing you should symlink your already installed font folders to FontBase/Providers folder:
    ``` sh
    sudo ln -s /usr/share/fonts ~/FontBase/Providers/UserShareFonts
    sudo ln -s ~/.fonts ~/FontBase/Providers/HomeFonts
    ```

1. **Fontmatix**: see [Install-Fontmatrix.Md][IFM] for installation

   ![](http://i.imgur.com/y1Nf2Ck.png)

1. [15 Best Linux Font Tools and How to Install Linux Fonts on Ubuntu][1BLFTAHTILFOU]

# Notification Daemons
  1. **dunst**
  2. **twmn**
  3. [eventd](https://www.eventd.org/)
  4. [State of the art](https://www.eventd.org/state-art.html)

# Terminal Markdown Viewer  
1. [patat][patat]: Terminal-based presentations using Pandoc  
   resentations Atop The ANSI Terminal  
   ![](https://github.com/jaspervdj/patat/raw/master/extra/screenshot.png?raw=true)  
   ``` sh
   sudo apt install patat
   ```

1. [mdv][mdv]: Markdown viewer  
   ![](https://github.com/axiros/terminal_markdown_viewer/raw/master/samples/5.png)  
   ``` sh
   sudo -H pip3.6 install mdv
   ```

1. [mdless](https://github.com/ttscoff/mdless):  
   mdless is a utility that provides a formatted and highlighted view of Markdown files in Terminal.  
   ![](https://github.com/ttscoff/mdless/raw/develop/screenshots/mdless.png)  
   ``` sh
   sudo gem install mdless
   ```

1. [mdp](https://github.com/visit1985/mdp): Markdown presentations tool  
   A command-line based markdown presentation tool.  
   ![](https://cloud.githubusercontent.com/assets/2237222/5810237/797c494c-a043-11e4-9dbd-959cab4055fa.gif)  

1. [CommonMark-py][cmpy]  
   Python markdown parser and renderer  
   ``` sh
   pip install commonmark
   ```
   Either use it in python scripts or use the cli by `cmark`

1. [bat][https://github.com/sharkdp/bat]  
   bat supports syntax highlighting for a large number of programming and markup languages  
   ![](https://camo.githubusercontent.com/9d3d89364f2cc83ace8f29646a6236bc15ea1da0/68747470733a2f2f696d6775722e636f6d2f724773646e44652e706e67)  

# Desktop Markdown editor:

1. typora

# Documentation

1. [sphinx](http://www.sphinx-doc.org)  
   Sphinx is a tool that makes it easy to create intelligent and beautiful documentation
   It was originally created for the Python documentation, and it has excellent 
   facilities for the documentation of software projects in a range of languages. 
   Of course, this site is also created from reStructuredText sources using Sphinx! 

   ![](http://www.milos.curuvija.com/_images/sphinx_google_analytics_verify1.png)  
   ![](https://i.github-camo.com/f3321d2404e853746ba2bc978bc13537feb14634/68747470733a2f2f7261772e67697468756275736572636f6e74656e742e636f6d2f646c646c2f737068696e782d707265766965772f6d61737465722f646f63732f64656d6f2e676966)  

# Download manager  

1. uget  

# Keyboard - keycode  

## finding symbols definition

``` sh
/usr/include/X11/XF86keysym.h
/usr/include/xkbcommon/xkbcommon-keysyms.h                  <== good for i3
```

## finding keycode by pressing them

   1. screenkey: shows on screen what keys have been pressed
   1. xev:  
      - `xev -input keyboard`
      - `xev | awk -F'[ )]+' '/^KeyPress/ { a[NR+2] } NR in a { printf "%-3s %s\n", $5, $8 }'`
   1. showkey:  
      - `showkey -a`
   1. xinput:  
      - `xinput list`  # then using the ids
        `xinput test 14`
   1. `sudo evtest` # lists all your devices
   1. `xmodmap -pke` # list all keycodes  

# Editors
## micro
Terminal editor for linux (10mb) [(github page)][GZMAMAITBTE]
``` sh
# installation
curl https://getmic.ro | bash
```

# MidiPlayer
You can use `Audacious`:
``` sh
sudo apt install audacious
```
See [MIDI - ArchWiki][MA] for instructions, you need to install `soundfont-fluid`:
``` sh
sudo apt-get install fluidsynth
sudo apt-get install fluid-soundfont-gm
```
Then point Audacious to use it by going to `File`  `Preferences`  `Plugins`  `Input`  `AMIDI-Plug`  `Preferences` and adding `/usr/share/sounds/sf2/FluidR3_GM.sf2` to it.

Some nice websites to download MIDI files:
- [Classical MIDI Files :: MIDIWORLD.COM][CMFDFFMC]


-----------------------------------------
2017-11-07 01:18:46

[awsome-linux]: https://github.com/LewisVo/Awesome-Linux-Software
[awsome-cli]: https://github.com/agarrharr/awesome-cli-apps
[cmdfu]: http://www.commandlinefu.com/commands/view/6663/pretend-to-be-busy-in-office-to-enjoy-a-cup-of-coffee
[shellcheck]: https://www.cyberciti.biz/programming/improve-your-bashsh-shell-script-with-shellcheck-lint-script-analysis-tool/
[hollywood]: http://blog.dustinkirkland.com/2014/12/hollywood-technodrama.html
[mdv]: https://github.com/axiros/terminal_markdown_viewer
[cmpy]: https://github.com/rtfd/CommonMark-py
[kupfer]: https://github.com/kupferlauncher/kupfer
[appfinder]: http://docs.xfce.org/xfce/xfce4-appfinder/usage
[patat]: https://github.com/jaspervdj/patat
[7MUELAO2]: https://www.fossmint.com/most-used-linux-applications/
[GBBBSCFWAL]: https://github.com/bleachbit/bleachbit
[TUE]: https://taskwarrior.org/docs/examples.html
[GZMAMAITBTE]: https://github.com/zyedidia/micro
[MA]: https://wiki.archlinux.org/index.php/MIDI
[CMFDFFMC]: https://www.midiworld.com/classic.htm
[FDFL]: https://fontba.se/downloads/linux#
[1BLFTAHTILFOU]: https://www.ubuntupit.com/15-best-linux-font-tools-and-how-to-install-linux-fonts-on-ubuntu/
[IFM]: /install/fontmatrix
[HWTCSIABAWBSTTARLS]: https://www.tecmint.com/shell-in-a-box-a-web-based-ssh-terminal-to-access-remote-linux-servers/
[GBGMGMIAMPGPOTOGDATIEGAWSPAOAIALFTIPSIUTXEWA]: https://github.com/bk138/gromit-mpx
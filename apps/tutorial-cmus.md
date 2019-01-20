# Cmus Tutorial

## Change view:

Use number row 0 - 9 to change the view:

| key | description |
| --- | ----------- |
| <kbd>1</kbd> | Library |
| <kbd>2</kbd> | Sorted library |
| <kbd>3</kbd> | Playlist view |
| <kbd>4</kbd> | Play queue |
| <kbd>5</kbd> | **File browser** ( you need to :cd to the folder, `i` toggles hidden files ) |
| <kbd>6</kbd> | Filters |
| <kbd>7</kbd> | **Settings** |

## Playback control:

| key | description |
| --- | ----------- |
| <kbd>c</kbd> | play/pause |
| <kbd>v</kbd> | stop |
| <kbd>b</kbd> | next track |
| <kbd>z</kbd> | previous track |
| <kbd>s</kbd> | toggle shuffle |
| <kbd>Shift</kbd> + <kbd>c</kbd> | toggle continue |
| <kbd>r</kbd> | toggle repeat |
| <kbd>Control</kbd>  +  <kbd>r</kbd> | toggle repeat current |
| <kbd>f</kbd> | toggle display follows now-playing |
| <kbd>x</kbd> | restart tracl |
|  |  |
| <kbd>+</kbd> / <kbd>-</kbd> | volume control |
| <kbd>/</kbd> | search |
| <kbd>i</kbd> | jump to track (depends on the view, in FILEBROWSER it toggles hidden files) |
|  |  |
| <kbd>.</kbd> | skip 1m forward |
| <kbd>,</kbd> | skip 1m backward |

## Add/Remove tracks:

| key | description |
| --- | ----------- |
| <kbd>a</kbd> | add track/folder from Browser view |
| <kbd>e</kbd> | appened track to Queue |
| <kbd>shift</kbd> + <kbd>e</kbd> | prepend track to Queue |
| <kbd>y</kbd> | add track to playlist |
| <kbd>shift</kbd> +<kbd>d</kbd> | remove track from the current view |

## Adding a new music to an existing playlist
1. Press <kbd>3</kbd> to go to the playlist view
    1. Switch between panes by pressing <kbd>tab</kbd>
    2. Select your playlist by pressing <kbd>space</kbd>
2. After your playlist is selected (having a `*` before the name), goto the Filebrowser view by pressing <kbd>5</kbd>
3. Browse to your music
4. Press <kbd>y</kbd> and the music will be added to your slected playlist

If you want the change to be persistence, you need to issue `:save` to save your setting before quiting{.note}

## Shuffle a playlist and add it to the queue

1. Press <kbd>4</kbd> for going to the `Play Queue`
    1. Optionally type `:clear` to clear the queue
2. Press <kbd>3</kbd> for going to the `Playlist view`
    1. Use <kbd>tab</kbd> for changing the pane
3. Go over the playlist that you want to play, and press <kbd>e</kbd> for queuing it in the `Play Queue`.
    1. If you want to shuffle them make sure before adding them you have pressed <kbd>s</kbd>.
       _As a result of shuffle being turned on you should see an `S` in the lower right corner of the screen_{.info}
4. Press <kbd>C</kbd> to start/stop playing your `Play Queue`
5. Press <kbd>b</kbd> for next item in the queue

_If your song stops after each item and you need to manually start the next song, probably you haved turned off the `Continue` option. To set it press <kbd>c</kbd> and you should see a 'C' in the lower right corner of the screen close to `S` if shuffle mode is on_{.note}

## Adding new music to a new playlist:

1. goto playlist view: press <kbd>3</kbd>
2. create playlist: `:pl-create <name>`
3. select playlist by arrow-keys then press <kbd>space</kbd> to activate it
4. switch to filebrowser: press <kbd>5</kbd>
5. change folder to your music folder: `:cd <folder>`
6. select music files by pressing <kbd>space</kbd>
7. add the selected files to your active playlist by pressing: <kbd>y</kbd>

- - -

2018-06-06 12:14:35
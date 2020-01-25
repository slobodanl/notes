_Written by: Reza Shams Amiri_
# I3fyra analysis
`i3fyra` uses three main components:
1. `i3gw` : i3 ghost window
   _i3gw_ will create a ghost container by issuing:
   ``` sh
   w=$(i3-msg open | sed 's/[^0-9]//g')
   i3-msg -q "[con_id=$w]" floating disable, mark "$tmark"
   ```
   Then it will disable floating on that window and will set a mark on it
   The advantage of marked containers are that then we can issue others commands to them for example:
   ``` sh
   i3gw ContainerA
   
   i3-msg -t get_marks
   # [ "ContainerA" ]
   
   i3-msg "[con_mark=ContainerA]" split v, layout tabbed,focus;terminal
   i3-msg "[con_mark=ContainerA]" kill
   
   # or
   $ i3gw ContainerB
   $ i3list | grep TWC
   i3list[TWC]=93859350528176 	# Target Window con_id
   
   $ i3-msg "[con_id=93859350528176]" move to mark ContainerA
   ```
1. `i3var` : gets/sets properties on marked windows
   _i3var_ can be used to set or get properties of a marked window (`con_mark`). The marked windows can be used to instruct i3 to do operations on those windows by id
   ``` sh
   $ i3var set "ContainerA" "Splitted"
   $ i3-msg -t get_marks
   [ "ContainerA=Splitted" ]
   
   $ i3var get "ContainerA"
   Splitted
   ```
1. `i3list`

   

* * *
Creation date: _2020-01-25_

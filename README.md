# VIM Cheatsheet - Working with multiple files / Programming

### Buffers

    :e[dit] {file}                      - edit {file} in a new buffer
    :fin[d] {file}                      - search and open {file}
    :b[uffer]{id}                       - move to buffer using {id}
    :bn[ext], :bp[rev]                  - go to the next/previous buffer
    :bf[irst], :bl[ast]                 - go to first/last buffer
    :bd[elete]                          - delete current/active buffer (close file)
    :1,10bd[elete]                      - delete buffers from ID 1 to 10
    :%bd[elete]                         - delete all buffers
    :ls or :buffers                     - show all buffers
    :sb{id}                             - open buffer{id} as a horizontal split
    :vert[ical] sb{id}                  - open buffer{id} as a vertical split
    :badd {file}                        - add {file} to the buffer list
    :ball                               - open all buffers in horizonal splits
    :vert ball                          - open all buffers in vertical splits
    :bufdo {cmd}                        - execute {cmd} in each buffer in the list. eg: apply macro 'a' to each buffer :bufdo normal @a
    CTRL-^                              - switch to the alternate buffer. (indicated in buffer list with symbol #)
    {id}CTRL-^                          - switch to a specific buffer with {id}.

### Arguments

    :ar[gs]                             - display the arglist
    :arga[dd] {file(s)}                 - add {file(s)} to the arglist
    :ar[gs] **/*.yml                    - add all yaml files from CWD and child folders
    :argd[elete] {file(s)}              - to remove {file(s)} from the arglist
    :argd[elete] *                      - remove all files from the arglist
    :argdo {cmd}                        - execute {cmd} on every file in the arglist
    :argdo update                       - save all changes to arglist
    :argdo undo                         - undo changes to your arglist
    :n[ext]                             - edit next file in the arglist
    :N[ext] or :prev                    - edit previous file in the arglist
    :fir[st]                            - edit first file in the arglist
    :la[st]                             - edit last file in the arglist

### Windows

    :sp[lit] {file} or :new {file}      - open {file} in a new buffer and horizontally split window
    :vs[plit] {file} or :vnew {file}    - open {file} in a new buffer and vertically split window
    :on[ly]!                            - close all windows except current
    CTRL-w o                            - close all windows except current
    CTRL-w s                            - split active window horizontally
    CTRL-w v                            - split active window vertically
    CTRL-w w                            - switch windows
    CTRL-w p                            - switch to previous window
    CTRL-w n                            - open new buffer in horizantal split
    CTRL-w q                            - quit a window
    CTRL-w j or CTRL-w <Dn>             - switch to windows below
    CTRL-w k or CTRL-w <Up>             - switch to window above
    CTRL-w h or CTRL-w <Left>           - switch to window left
    CTRL-w l or CTRL-w <Right>          - switch to window right
    CTRL-w r                            - rotate the windows clockwise
    CTRL-w R                            - rotate the windows counter-clockwise
    CTRL-w x                            - exchange windows, horizontal
    CTRL-w X                            - exchange windows, vertical
    CTRL-w _                            - maximize window height of current split
    CTRL-w |                            - maximize window width of current split
    CTRL-w =                            - normalize all split sizes
    CTRL-w T                            - break out current window into new tab
    :res[size] {num}                    - resize active horizontal window by {num} rows
    :vert[ical] res[size] {num}         - resize active vertical window by {num} rows
    {buffer_id}CTRL-w ^                 - split windows with the buffer of {id}
    :windo {cmd}                        - execute {cmd} for all windows
    :windo difft[his]                   - start diff mode in all open windows
    :windo diffo[ff]                    - stop diff mode for all open windows
    :sf {file}                          - split window and :find {file}
    :vert[ical] sf {file}               - split window vertically and :find {file}

### Tabs

    :tabe[dit] {file}                   - open existing {file} in new tab
    :tabe[dit] %                        - move the active window into its own tab
    :tabn {file}                        - open {file} in a new tab
    :tabs                               - list tabs
    gt or :tabn[ext]                    - move to the next tab
    gT or :tabp[rev]                    - move to the previous tab
    {n}gt                               - move to tab number {n}
    :tabmove {n}                        - move current tab to {n}th position (indexed from 0)
                                          if no position provided, moves to last position
    :tabc[lose]                         - close the current tab and all its windows
    :tabo[nly]                          - close all tabs except for the current one
    :tabd[o] {cmd}                      - execute {cmd} in each tab page

### Jump list

    CTRL-o, CTRL-i                      - go to the previous (older), next (is near o) cursor position
    :jumps                              - to display jump list
    :clearjumps                         - clear the jump list
    gf                                  - go to file in cursor

### Change list

    :changes                            - Show change list
    g;                                  - jump to the next change
    g,                                  - jump to the previous change

### Quickfix list

    # commands that populate Quickfix list
    :vim[grep] /pattern {file}          - search using Vim's native functionality
    :gr[ep]                             - search via exteran program specified by grepprg setting
    :helpgr[ep]                         - search help text files
    :mak[e]                             - call the program specified by the makeprg setting (default is make)
    :cex[pr] {expression}               - use {expression} to populate to list
    :cex[pr] []                         - clear the quickfix list

    # vimgrep examples
    :vim /foo/g %                       - search in current active buffer only
    :vim /foo/g fo.txt ab.txt           - search fo.txt and ab.txt for foo
    :vim /foo/g *.txt                   - search *.txt for foo
    :vim /foo/g **/*                    - search recursive current directory and below
    :vim /foo/g **/*.txt                - search recursive current directory and below in all *.txt file(s)
    :vim /foo/g ##                      - search files in arglist
    :vim /foo/gj ##                     - search files in arglist, do not jump to first match
    :vim /foo/gf ##                     - search files in arglist, fuzzy match the pattern

    # commands to use Quickfix list
    :cw[indow]                          - open the quickfix window if it's not empty
    :cope[n]                            - open quickfix window
    :ccl[ose]                           - close quifxix window
    :cn[ext], :cp[rev]                  - jump to next/previous error
    :cc {n}                             - jump to the {n} line in the quickfix window
    :cnf[ile], :cpf[file]               - jump to first error in the next/previous file
    :cab[ove], :cbe[ow]                 - jump to the error above/below the current line
    :col[der], :cnew[er]                - go to the older/newer quickfix list
    :chi[story]                         - Show the list of quickfix lists
    :cfir[st], :cla[st]                 - go to first/last location
    :cdo {cmd}                          - execute {cmd} in each valid entry in the quickfix list
    :cfdo {cmd}                         - execute {cmd} in each file in the quickfix list
    :colder, :cnewer                    - go to older/newer quickfix list

### Go to variable definition

    *                                   - search for the exact word under the cursor
    g*                                  - same as *, but allows for partial matches
    #                                   - search for the exact word under the cursor, reverse direction
    g#                                  - same as #, but allows for partial matches, reverse direction
    gd                                  - go to local variable
    gD                                  - go to global variable definition

### Tags

    CTRL-]                              - jump to tag under cursor
    gCTRL-]                             - prompt user to select from multiple matches
    :t[ag] {tag}                        - jump to tag {tag}
    :t[ag] {tag} {file}                 - jump to tag {tag} in file {file}
    :t[ag] {tag} {file} {line}          - jump to tag {tag} in file {file} at line {line}
    :tj[ump] {keyword}                  - prompt uer select from multiple matches for {keyword}
    :popup or <CTRL-t>                  - reverse through tag history
    :tn[ext]                            - jump to next matching tag
    :tp[rev]                            - jump to previous matching tag
    :tfirst                             - jump to first matching tag
    :tlast                              - jump to last matching tag
    :tselect                            - prompt user to choose an item from the tag match list

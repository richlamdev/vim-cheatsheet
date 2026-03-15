# VIM Cheatsheet - Working with multiple files

### Buffers - Open / Close / Save

    :e[dit] {file}                        - load {file} into a buffer (replaces current window's buffer)
    :ene[w]                               - create a new empty buffer, within the current window
    :fin[d] {file}                        - search and open {file}
    :badd {file}                          - add {file} to the buffer list without opening

    :w[rite]                              - save current buffer
    :w {file}                             - save current buffer as {file} (does not change buffer name)
    :sav[eas] {file}                      - save current buffer as {file} and switch buffer to it
    :wa[ll]                               - save all buffers
    :up[date]                             - update current buffer

    :r[ead] {file}                        - insert {file} below cursor
    :r[ead] !{cmd}                        - insert output of {cmd} into current buffer

    :e[dit]!                              - reload buffer, discard changes
    :f[ile]                               - show current buffer name
    :f[ile] {name}                        - change current buffer name (no write)

    :bd[elete]                            - delete current/active buffer (close file)
    :{n},{m}bd[elete]                     - delete buffers from {n} to {m}
    :%bd[elete]                           - delete all buffers

    :bufdo {cmd}                          - execute {cmd} in each buffer in the list. eg: apply macro 'a' to each buffer :bufdo normal @a
    :buddo norm[al] @a                    - apply macro 'a' to each buffer

### Buffers - Navigate

    :ls or :buffers                       - show all buffers
    :b[uffer]{id}                         - move to buffer using {id}
    :bn[ext], :bp[rev]                    - go to the next/previous buffer
    :bf[irst], :bl[ast]                   - go to first/last buffer
    CTRL-^                                - switch to the alternate buffer. (marked in buffer list with symbol #)
    {id}CTRL-^                            - switch to buffer {id}.

    :sb{id}                               - open buffer{id} as a horizontal split
    :vert[ical] sb{id}                    - open buffer{id} as a vertical split
    :ball                                 - open all buffers in horizonal splits
    :vert ball                            - open all buffers in vertical splits

### Arguments

    :ar[gs]                               - display the arglist
    :ar[gs] {file(s)}                     - replace arglist with {file(s)}
    :arga[dd] {file(s)}                   - add {file(s)} to the arglist
    :ar[gs] **/*.yml                      - add all yaml files from CWD and child folders
    :argd[elete] {file(s)}                - to remove {file(s)} from the arglist
    :argd[elete] *                        - remove all files from the arglist
    :argdo {cmd}                          - execute {cmd} on every file in the arglist
    :argdo update                         - save all changes to arglist
    :argdo undo                           - undo last change in each arg buffer
    :n[ext]                               - edit next file in the arglist
    :N[ext] or :prev                      - edit previous file in the arglist
    :wn[ext]                              - write current file, edit next arg
    :wN[ext] or :wprev                    - write current file, edit previous arg
    :fir[st] or :rew[ind]                 - edit first file in the arglist
    :la[st]                               - edit last file in the arglist
    :argdo %s/old/new/ge | update         - replace "old" with "new" in each file in the arglist and save

### Windows

    :sp[lit] {file} or :new {file}        - open {file} in a new buffer and create horizontal split
    :vs[plit] {file} or :vnew {file}      - open {file} in a new buffer and create vertical split

    :on[ly]!                              - close all windows except current
    CTRL-w o                              - close all windows except current
    CTRL-w s                              - split active window horizontally
    CTRL-w v                              - split active window vertically
    CTRL-w w                              - cycle through windows
    CTRL-w p                              - switch to previous window
    CTRL-w n                              - open a new empty window (horizontal split)
    CTRL-w q                              - quit a window

    CTRL-w j or CTRL-w <Dn>               - switch to window below
    CTRL-w k or CTRL-w <Up>               - switch to window above
    CTRL-w h or CTRL-w <Left>             - switch to window left
    CTRL-w l or CTRL-w <Right>            - switch to window right

    CTRL-w H                              - move window to far left
    CTRL-w J                              - move window to bottom
    CTRL-w K                              - move window to top
    CTRL-w L                              - move window to far right
    CTRL-w r                              - rotate the windows clockwise
    CTRL-w R                              - rotate the windows counter-clockwise
    CTRL-w x                              - exchange windows, horizontal
    CTRL-w X                              - exchange windows, vertical
    CTRL-w _                              - maximize window height of current split
    CTRL-w |                              - maximize window width of current split
    CTRL-w =                              - normalize all split sizes
    CTRL-w T                              - break out current window into new tab

    :res[size] {num}                      - resize active horizontal window by {num} rows
    :vert[ical] res[size] {num}           - resize active vertical window by {num} columns
    {buffer_id}CTRL-w ^                   - split window and edit buffer {id}

    :windo {cmd}                          - execute {cmd} for all windows
    :windo difft[his]                     - start diff mode in all open windows
    :windo diffo[ff]                      - stop diff mode for all open windows
    :sf {file}                            - split window and :find {file}
    :vert[ical] sf {file}                 - split window vertically and :find {file}

### Tabs

    :tabe[dit] {file}                     - open {file} in a new tab
    :tabnew {file}                        - open {file} in a new tab
    :tabe[dit] %                          - open current buffer in a new tab
    :tabs                                 - list tabs
    gt or :tabn[ext]                      - move to the next tab
    gT or :tabp[rev]                      - move to the previous tab
    :tabfir[st]                           - move to first tab
    :tabl[ast]                            - move to last tab
    {n}gt                                 - move to tab number {n}
    :tabmove {n}                          - move current tab to {n}th position (indexed from 0)
                                            if no position provided, moves to last position
    :tabc[lose]                           - close the current tab and all its windows
    :tabo[nly]                            - close all tabs except for the current one
    :tabd[o] {cmd}                        - execute {cmd} in each tab page


### Jump list

    CTRL-o                                - jump to older cursor position
    CTRL-i                                - jump to newer cursor position
    :jumps                                - to display jump list
    :clearjumps                           - clear the jump list
    gf                                    - edit file name under cursor

### Change list

    :changes                              - display change list
    g;                                    - jump to the previous (older) change
    g,                                    - jump to the next (newer) change

### Quickfix list

    # commands that populate Quickfix list
    :vim[grep] /pattern {file}            - search using Vim's internal grep
    :gr[ep]                               - search via external program specified by grepprg setting
    :helpgr[ep]                           - search help text files
    :mak[e]                               - call the program specified by the makeprg setting (default is make)
    :cex[pr] {expression}                 - use {expression} to populate to list
    :cex[pr] []                           - replace quickfix list with empty list (clear quickfix list)

    # vimgrep examples
    :vim /foo/g %                         - search in current active buffer only
    :vim /foo/g fo.txt ab.txt             - search fo.txt and ab.txt for foo
    :vim /foo/g *.txt                     - search *.txt for foo
    :vim /foo/g **/*                      - search recursive current directory and below
    :vim /foo/g **/*.txt                  - search recursive current directory and below in all *.txt file(s)
    :vim /foo/g ##                        - search files in arglist
    :vim /foo/gj ##                       - search files in arglist, do not jump to first match
    :vim /foo/gf ##                       - search files in arglist, fuzzy match the pattern

    # commands to use Quickfix list
    :cw[indow]                            - open the quickfix window if it's not empty
    :cope[n]                              - open quickfix window
    :ccl[ose]                             - close quickfix window
    :cn[ext], :cp[rev]                    - jump to next/previous error
    :cc {n}                               - jump to quickfix entry {n}
    :cnf[ile], :cpf[file]                 - jump to first error in the next/previous file
    :cab[ove], :cbe[ow]                   - jump to the error above/below the current line
    :col[der], :cnew[er]                  - go to the older/newer quickfix list
    :chi[story]                           - Show the list of quickfix lists
    :cfir[st], :cla[st]                   - go to first/last location
    :cdo {cmd}                            - execute {cmd} in each valid entry in the quickfix list
    :cdo %s/old/new/gc | update           - replace "old" with "new" in each entry in the quickfix list and save
    :cfdo {cmd}                           - execute {cmd} in each file in the quickfix list
    :cfdo %s/old/new/gc | update          - replace "old" with "new" in each file in the quickfix list and save

### Go to symbol / word under cursor

    *                                     - search for the exact word under the cursor
    g*                                    - search for partial matches of word under cursor
    #                                     - search for the exact word under the cursor (reverse)
    g#                                    - search for partial matches of word under cursor (reverse)
    gd                                    - go to local declaration of identifier under cursor
    gD                                    - go to global declaration of identifier under cursor

### Tags

    CTRL-]                                - jump to tag under cursor
    gCTRL-]                               - prompt user to select from multiple matching tags
    :t[ag] {tag}                          - jump to tag {tag}
    :t[ag] {tag} {file}                   - jump to tag {tag} in file {file}
    :t[ag] {tag} {file} {line}            - jump to tag {tag} in file {file} at line {line}
    :tj[ump] {keyword}                    - prompt user to select from matching tags for {keyword}
    :CTRL-t                               - jump back in tag stack
    :tn[ext]                              - jump to next matching tag
    :tp[rev]                              - jump to previous matching tag
    :tfirst                               - jump to first matching tag
    :tlast                                - jump to last matching tag
    :tselect                              - prompt user to select from matching tags

### Global commands
    :g/pattern/#                          - list all lines matching pattern with line numbers
    :g/pattern/{cmd}                      - executes {cmd} on all lines matching pattern
    :g/pattern/m0                         - move matching lines to the top of the file
    :g/pattern/t$                         - move matching lines to the end of the file
    :g/pattern/d _                        - delete all lines containing pattern without affecting registers (use blackhole register _ )
    :g!/pattern/d or :v/pattern/d         - delete all lines not matching pattern (inverse match)
    q a q:g/pattern/y A                   - copy all lines matching a pattern to register 'a'.

    :bufdo g/pattern/d                    - delete all lines matching 'pattern' in all buffers
    :bufdo g/pattern/s/old/new/g          - replace 'old' with 'new' on matching lines in all buffers
    :argdo g/pattern/d | update           - delete all lines matching 'pattern' in each file and save
    :argdo g/pattern/s/old/new/g | update - replace 'old' with 'new' on matching lines in each file and save
    :cdo g/pattern/d                      - delete all lines matching 'pattern' in all quickfix entries
    :cdo g/pattern/s/old/new/g            - replace 'old' with 'new' on matching lines in all quickfix entries

### Marks

    # Setting marks
    m{a-z}                                - set a local mark {a-z} at the cursor position
    m{A-Z}                                - set a global mark {A-Z} (accessible across files)

    # Jumping to marks
    '{a-z}                                - jump to the beginning of the line of local mark {a-z}
    `{a-z}                                - jump to exact cursor position of local mark {a-z}
    '{A-Z}                                - jump to line of global mark {A-Z} in its file
    `{A-Z}                                - jump to exact position of global mark {A-Z} in its file

    # Navigation shortcuts
    ''                                    - jump to position before last jump

    # Viewing / deleting marks
    :marks                                - display all current marks
    :delmarks {a-zA-Z}                    - delete specified marks
    :delmarks!                            - delete all global marks

    # Examples
    ma                                    - set mark 'a' at cursor
    `a                                    - jump to mark 'a'


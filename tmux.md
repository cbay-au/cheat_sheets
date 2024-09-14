^ = alt a

==========================================          ==========================================
             TMUX COMMAND                                        WINDOW (TAB)
==========================================          ==========================================

List    tmux ls                                     List         ^b w
New          new -s <session>                       Create       ^b c
Attach       att -t <session>                       Rename       ^b , <name>
Rename       rename-session -t <old> <new>          Last         ^b l               (lower-L)
Kill         kill-session -t <session>              Close        ^b &

==========================================          Goto #       ^b <0-9>
             CONTROLS                               Next         ^b n
==========================================          Previous     ^b p
                                                    Choose       ^b w <name>
Detach       ^a d
List         ^a =                                   ==========================================
Buffer       ^a <PgUpDn>                                         PANE (SPLIT WINDOW)
Command      ^a : <command>                         ==========================================

Copy         ^a [ ... <space> ... <enter>           Show #       ^b q
 Moving         vim/emacs key bindings              Split Horiz  ^b "                --------
 Start          <space>                             Split Vert   ^b %                   |
 Copy           <enter>                             Pane->Window ^b !
Paste        ^b ]                                   Kill         ^b x
refresh conf ^r

==========================================          Reorganize   ^b <space>
             SESSION (Set of Windows)               Expand       ^b <alt><arrow>
==========================================          Resize       ^b ^<arrow>
                                                    Resize x n   ^b <n> <arrow>
New          ^a :new     ^b :new -s <name>
Rename       ^a $                                   Select       ^b <arrow>
List         ^a s                                   Previous     ^b {
Next         ^a (                                   Next         ^b }
Previous     ^a )                                   Switch       ^b o                  other
                                                    Swap         ^b ^o
                                                    Last         ^b ;

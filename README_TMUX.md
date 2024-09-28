

Key bindings
-----------
So `~/.tmux.conf` overrides default key bindings for many action, to make them more reasonable, easy to recall and comforable to type.

Let's go through them. 

If you are an iTerm2 user, third column describes the keybinding of similar  "action" in iTerm2. It's possible to reuse very same keys you already get used to and tell iTerm2 to execute analogous tmux actions. See [iTerm2 and tmux integration](#iterm2-and-tmux-integration) section below.

<table>
    <tr>
        <td nowrap><b>tmux key</b></td>
        <td><b>Description</b></td>
        <td><b>iTerm2 key</b></td>
    </tr>
    <tr>
        <td nowrap><code>C-a</code></td>
        <td>Default prefix, used instead of "C-b". Same prefix is used in screen program, and it's easy to type. The only drawback of "C-a" is that underlying shell does not receive the keystroke to move to the beginning of the line.
        </td>
        <td>-</td>
    </tr>
    <tr>
        <td nowrap><code>&lt;prefix&gt; C-e</code></td>
        <td>Open ~/.tmux.conf file in your $EDITOR</td>
        <td>-</td>
    </tr>
    <tr>
        <td><code>&lt;prefix&gt; C-r</code></td>
        <td>Reload tmux configuration from ~/.tmux.conf file</td>
        <td>-</td>
    </tr>
    <tr>
        <td><code>&lt;prefix&gt; r</code></td>
        <td>Rename current window</td>
        <td>-</td>
    </tr>
    <tr>
        <td><code>&lt;prefix&gt; R</code></td>
        <td>Rename current session</td>
        <td>-</td>
    </tr>
    <tr>
        <td><code>&lt;prefix&gt; _</code></td>
        <td>Split new pane horizontally</td>
        <td>⌘⇧D</td>
    </tr>
    <tr>
        <td><code>&lt;prefix&gt; |</code></td>
        <td>Split new pane vertically</td>
        <td>⌘D</td>
    </tr>
    <tr>
        <td><code>&lt;prefix&gt; &lt;</code></td>
        <td>Select next pane</td>
        <td>⌘[</td>
    </tr>
    <tr>
        <td><code>&lt;prefix&gt; &gt;</code></td>
        <td>Select previous pane</td>
        <td>⌘]</td>
    </tr>
    <tr>
        <td><code>&lt;prefix&gt; ←</code></td>
        <td>Select pane on the left</td>
        <td>⌘⌥←</td>
    </tr>
    <tr>
        <td><code>&lt;prefix&gt; →</code></td>
        <td>Select pane on the right</td>
        <td>⌘⌥→</td>
    </tr>
    <tr>
        <td><code>&lt;prefix&gt; ↑</code></td>
        <td>Select pane on the top</td>
        <td>⌘⌥↑</td>
    </tr>
    <tr>
        <td><code>&lt;prefix&gt; ↓</code></td>
        <td>Select pane on the bottom</td>
        <td>⌘⌥↓</td>
    </tr>
    <tr>
        <td><code>&lt;prefix&gt; C-←</code></td>
        <td>Resize pane to the left</td>
        <td>^⌘←</td>
    </tr>
    <tr>
        <td><code>&lt;prefix&gt; C-→</code></td>
        <td>Resize pane to the right</td>
        <td>^⌘→</td>
    </tr>
    <tr>
        <td><code>&lt;prefix&gt; C-↑</code></td>
        <td>Resize pane to the top</td>
        <td>^⌘↑</td>
    </tr>
    <tr>
        <td><code>&lt;prefix&gt; C-↓</code></td>
        <td>Resize pane to the bottom</td>
        <td>^⌘↓</td>
    </tr>
    <tr>
        <td><code>&lt;prefix&gt; &gt;</code></td>
        <td>Move to next window</td>
        <td>⌘⇧]</td>
    </tr>
    <tr>
        <td><code>&lt;prefix&gt; &lt;</code></td>
        <td>Move to previous window</td>
        <td>⌘⇧[</td>
    </tr>
    <tr>
        <td><code>&lt;prefix&gt; Tab</code></td>
        <td>Switch to most recently used window</td>
        <td>^Tab</td>
    </tr>

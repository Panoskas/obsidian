### NeoVim Keybindings Cheat Sheet

This cheat sheet covers essential keybindings for **NeoVim** to help you navigate and edit efficiently. It’s divided into **basic navigation**, **editing**, **searching**, and **advanced** commands.

---

### Basic Navigation
| Keybind | Description |
|---------|-------------|
| `h` `j` `k` `l` | Move left, down, up, right (respectively) |
| `gg`            | Jump to the first line of the file |
| `G`             | Jump to the last line of the file |
| `^`             | Move to the first non-blank character of the line |
| `$`             | Move to the end of the line |
| `w`             | Move forward by one word |
| `b`             | Move backward by one word |
| `Ctrl + u`      | Scroll up half a page |
| `Ctrl + d`      | Scroll down half a page |

---

### Basic Editing
| Keybind | Description |
|---------|-------------|
| `i`             | Insert mode before cursor |
| `I`             | Insert mode at the beginning of the line |
| `a`             | Insert mode after cursor |
| `A`             | Insert mode at the end of the line |
| `o`             | Insert a new line below the current line |
| `O`             | Insert a new line above the current line |
| `x`             | Delete the character under the cursor |
| `dw`            | Delete to the start of the next word |
| `dd`            | Delete the entire current line |
| `D`             | Delete from the cursor to the end of the line |
| `u`             | Undo the last action |
| `Ctrl + r`      | Redo the last undone action |
| `yy`            | Yank (copy) the entire line |
| `p`             | Paste after the cursor |
| `P`             | Paste before the cursor |
| `r`             | Replace the character under the cursor |

---

### Visual Mode
| Keybind | Description |
|---------|-------------|
| `v`             | Enter visual mode to select characters |
| `V`             | Enter visual line mode to select whole lines |
| `Ctrl + v`      | Enter visual block mode to select columns |
| `y`             | Yank (copy) the selected text |
| `d`             | Delete the selected text |
| `c`             | Change the selected text |
| `>`             | Indent the selected text |
| `<`             | Unindent the selected text |
| `gv`            | Reselect the last visual selection |

---

### Search and Replace
| Keybind | Description |
|---------|-------------|
| `/`             | Search forward |
| `?`             | Search backward |
| `n`             | Repeat the search in the same direction |
| `N`             | Repeat the search in the opposite direction |
| `:%s/foo/bar/g` | Replace all instances of "foo" with "bar" in the file |
| `:noh`          | Clear search highlights |

---

### Buffers and Windows
| Keybind | Description |
|---------|-------------|
| `:bn`            | Go to the next buffer |
| `:bp`            | Go to the previous buffer |
| `:bd`            | Close the current buffer |
| `Ctrl + w + s`   | Split the window horizontally |
| `Ctrl + w + v`   | Split the window vertically |
| `Ctrl + w + w`   | Switch between windows |
| `Ctrl + w + q`   | Quit the current window |

---

### Tabs
| Keybind | Description |
|---------|-------------|
| `:tabnew`        | Open a new tab |
| `gt`             | Go to the next tab |
| `gT`             | Go to the previous tab |
| `:tabc`          | Close the current tab |

---

### Advanced
| Keybind         | Description                                          |     |
| --------------- | ---------------------------------------------------- | --- |
| `:e <filename>` | Open a file                                          |     |
| `:w`            | Save the current file                                |     |
| `:q`            | Quit NeoVim                                          |     |
| `:wq`           | Save and quit NeoVim                                 |     |
| `:x`            | Save and quit (only if changes were made)            |     |
| `Ctrl + z`      | Suspend NeoVim                                       |     |
| `:!<command>`   | Run an external command (e.g., `:!ls` to list files) |     |

### Marks and Jumps
| Keybind | Description |
|---------|-------------|
| `m<letter>`       | Set mark at current position (e.g., `ma`) |
| `'<letter>`       | Jump to mark (e.g., `'a`) |
| `` ` <letter>``   | Jump to exact position of mark |
| `Ctrl + o`        | Jump back to the previous location |
| `Ctrl + i`        | Jump forward to the next location |

---

This covers the most essential NeoVim keybindings for day-to-day use. For more advanced features and custom keybindings, you can explore the **`.vimrc`** or **`init.lua`** configuration file.


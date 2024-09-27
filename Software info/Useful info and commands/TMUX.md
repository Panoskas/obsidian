# **Tmux Cheat Sheet**

## **1. Sessions**

### **Creating and Managing Sessions**
- **Start a new session**  
  **Shell**: `tmux new`  
  **Shell**: `tmux new-session`
  
- **Start or attach to a session named _mysession_**  
  **Shell**: `tmux new-session -A -s mysession`

- **Start a session with the name _mysession_**  
  **Shell**: `tmux new -s mysession`  
  **Tmux Command**: `new -s mysession`

- **Kill the current session**  
  **Tmux Command**: `kill-session`

- **Kill a specific session named _mysession_**  
  **Shell**: `tmux kill-session -t mysession`

- **Kill all sessions except the current one**  
  **Shell**: `tmux kill-session -a`

- **Kill all sessions except _mysession_**  
  **Shell**: `tmux kill-session -a -t mysession`

### **Switching and Navigating Sessions**
- **Rename the current session**  
  **Shortcut**: `Ctrl + b` → `$`

- **Detach from the current session**  
  **Shortcut**: `Ctrl + b` → `d`

- **Detach other clients from the session**  
  **Tmux Command**: `attach -d`

- **Show all sessions**  
  **Shell**: `tmux ls`  
  **Shortcut**: `Ctrl + b` → `s`

- **Attach to the last session**  
  **Shell**: `tmux attach`

- **Move to the previous session**  
  **Shortcut**: `Ctrl + b` → `(`

- **Move to the next session**  
  **Shortcut**: `Ctrl + b` → `)`

---

## **2. Windows**

### **Creating and Managing Windows**
- **Start a new session with a window named _mywindow_**  
  **Shell**: `tmux new -s mysession -n mywindow`

- **Create a new window**  
  **Shortcut**: `Ctrl + b` → `c`

- **Rename the current window**  
  **Shortcut**: `Ctrl + b` → `,`

- **Close the current window**  
  **Shortcut**: `Ctrl + b` → `&`

- **List all windows**  
  **Shortcut**: `Ctrl + b` → `w`

### **Switching and Navigating Windows**
- **Move to the previous window**  
  **Shortcut**: `Ctrl + b` → `p`

- **Move to the next window**  
  **Shortcut**: `Ctrl + b` → `n`

- **Switch to a specific window by number**  
  **Shortcut**: `Ctrl + b` → `[0-9]`

- **Toggle the last active window**  
  **Shortcut**: `Ctrl + b` → `l`

---

## **3. Panes**

### **Splitting and Managing Panes**
- **Split the current pane vertically (side-by-side layout)**  
  **Tmux Command**: `split-window -h`  
  **Shortcut**: `Ctrl + b` → `%`

- **Split the current pane horizontally (stacked layout)**  
  **Tmux Command**: `split-window -v`  
  **Shortcut**: `Ctrl + b` → `"`

- **Close the current pane**  
  **Shortcut**: `Ctrl + b` → `x`

- **Toggle pane zoom** (maximizes a pane within the window)  
  **Shortcut**: `Ctrl + b` → `z`

### **Switching and Navigating Panes**
- **Move to the next pane**  
  **Shortcut**: `Ctrl + b` → `o`

- **Show pane numbers** (allows selecting a pane by number)  
  **Shortcut**: `Ctrl + b` → `q`

- **Switch to pane by number**  
  **Shortcut**: `Ctrl + b` → `q` → `[0-9]`

- **Move the current pane left**  
  **Shortcut**: `Ctrl + b` → `{`

- **Move the current pane right**  
  **Shortcut**: `Ctrl + b` → `}`

---

## **4. Copy Mode**

### **Navigating and Scrolling in Copy Mode**
- **Enter copy mode**  
  **Shortcut**: `Ctrl + b` → `[`  

- **Scroll up**  
  **Shortcut**: `↑`

- **Scroll down**  
  **Shortcut**: `↓`

- **Go to the top line**  
  **Shortcut**: `g`

- **Go to the bottom line**  
  **Shortcut**: `G`

- **Quit copy mode**  
  **Shortcut**: `q`

---

## **5. Additional Commands**

- **Synchronize panes (send input to all panes simultaneously)**  
  **Tmux Command**: `setw synchronize-panes`

- **Reorder windows, renumbering them sequentially**  
  **Tmux Command**: `move-window -r`

---

## Tmux Ressurect

- `prefix + Ctrl -s` --> save
- `prefix + Ctrl -r` --> restore
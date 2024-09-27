### Create soft link

Creating a soft link inside /usr/local/bin typically means you're making a command or program accessible system-wide for all users. Here's what this implies:

1. Command accessibility: Programs in /usr/local/bin are in the system's default PATH, so they can be run from any directory without specifying the full path.

2. User-installed software: /usr/local/bin is often used for software installed by system administrators or users, separate from the package manager.

3. Custom scripts: It's a common location for placing custom scripts or commands you want available to all users.

4. Preserving original location: The soft link allows the actual program to reside elsewhere while making it accessible as if it were in /usr/local/bin.

5. Easy updates: You can update the original program without changing the link, maintaining consistent access.

6. Non-root software management: Unlike /usr/bin, /usr/local/bin is typically writable by system administrators without root access.

For example, if you have a script in your home directory that you want available system-wide, you might create a soft link like this:

```
sudo ln -s /home/yourusername/myscript.sh /usr/local/bin/myscript
```

This would allow any user to run 'myscript' from any directory.

Would you like me to explain more about the implications or provide additional examples?

1. Go to project u want to create soft link
2. `ln -s path_to_projects`  (abs path)   `name`\
		e.g. 
		`ln -s /home/panagiotis.kastrounis/Documents/Dialectica/Troia/olympus-management-script/olympus.sh ../olympus.sh
`
1. go to `/usr/local/sbin`
		e.g. 
		`sudo ln -s /home/panagiotis.kastrounis/Documents/Dialectica/Troia/olympus.sh olympus`


### Remove a non empty dir

`sudo rm -rf <dir>`

### Kill a frozen app

`xkill`

### Other

𝐩𝐰𝐝 - Print working directory. 📂
𝐥𝐬 - List directory contents. 📋
𝐜𝐝 - Change directory. 📁
𝐭𝐨𝐮𝐜𝐡 - To create a file without any content. 📄
𝐜𝐚𝐭 - Concatenate and display file content. 🐱
𝐜𝐩 - Copy files or directories. 📁📂
𝐦𝐯 - Move or rename files or directories. 🔄
𝐫𝐦 - Remove files or directories. 🗑️
𝐦𝐤𝐝𝐢𝐫 - Create a new directory. 📁
𝐫𝐦𝐝𝐢𝐫 - Remove an empty directory. 📁🗑️
𝐞𝐜𝐡𝐨 - Display a line of text or a variable value. 📢
𝐧𝐚𝐧𝐨 - A simple text editor. ✏️
𝐯𝐢 - A powerful text editor. ✒️
𝐜𝐡𝐦𝐨𝐝 - Change file or directory permissions. 🔐
𝐜𝐡𝐨𝐰𝐧 - Change file or directory owner and group. 👤
𝐟𝐢𝐧𝐝 - Search for files in a directory hierarchy. 🔍
𝐠𝐫𝐞𝐩 - Search text using patterns. 🔎
𝐦𝐚𝐧 - Display the manual for a command. 📖
𝐩𝐬 - Display information about running processes. 🔄
𝐤𝐢𝐥𝐥 - Terminate processes by PID. ⚰️
𝐭𝐨𝐩 - Display and update sorted information about processes. 📊
𝐝𝐟 - Report file system disk space usage. 💾
𝐝𝐮 - Estimate file space usage. 📏
𝐟𝐫𝐞𝐞 - Display memory usage. 🧠
𝐮𝐧𝐚𝐦𝐞 - Print system information. ℹ️
𝐮𝐩𝐭𝐢𝐦𝐞 - Tell how long the system has been running. ⏳
𝐰𝐡𝐨𝐚𝐦𝐢 - Display the current user. 👤
𝐬𝐮𝐝𝐨 - Execute a command as another user, typically the superuser. 🛡️
𝐚𝐩𝐭-𝐠𝐞𝐭 - Package handling utility for Debian-based distributions. 📦
𝐲𝐮𝐦 - Package manager for RPM-based distributions. 🍲
𝐭𝐚𝐫 - Archive files. 🗃️
𝐳𝐢𝐩 - Package and compress (archive) files. 📦
𝐮𝐧𝐳𝐢𝐩 - Extract compressed files. 📂
𝐰𝐠𝐞𝐭 - Retrieve files from the web. 🌐
𝐜𝐮𝐫𝐥 - Transfer data from or to a server. 🔄
𝐬𝐬𝐡 - OpenSSH client (remote login program). 🚪
𝐬𝐜𝐩 - Secure copy (remote file copy program). 🔒
𝐫𝐬𝐲𝐧𝐜 - Remote file and directory synchronization. 🔄
𝐡𝐨𝐬𝐭𝐧𝐚𝐦𝐞 - Show or set the system's host name. 🏠
𝐩𝐢𝐧𝐠 - Send ICMP ECHO_REQUEST to network hosts. 📶
𝐧𝐞𝐭𝐬𝐭𝐚𝐭 - Print network connections, routing tables, interface statistics, masquerade connections, and multicast memberships. 🌐
𝐢𝐟𝐜𝐨𝐧𝐟𝐢𝐠 - Configure a network interface. 🌐
𝐢𝐩 - Show/manipulate routing, devices, policy routing, and tunnels. 🌐
𝐢𝐩𝐭𝐚𝐛𝐥𝐞𝐬 - Administration tool for IPv4 packet filtering and NAT. 🛡️
𝐬𝐲𝐬𝐭𝐞𝐦𝐜𝐭𝐥 - Control the systemd system and service manager. 🔄
𝐣𝐨𝐮𝐫𝐧𝐚𝐥𝐜𝐭𝐥 - Query and display messages from the journal. 📜
𝐜𝐫𝐨𝐧𝐭𝐚𝐛 - Schedule periodic background jobs. ⏰
𝐬𝐮𝐝𝐨 𝐬𝐮 - Allows us to switch to a different user and execute one or more commands in the shell without logging out from our current session. 🛡️
𝐦𝐨𝐮𝐧𝐭 - Mount a file system. 📂
𝐮𝐦𝐨𝐮𝐧𝐭 - Unmount a file system. 📂
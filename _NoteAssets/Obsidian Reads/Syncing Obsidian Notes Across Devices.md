---
tags:
  - openSource
  - proprietarySoftware
  - tool
author:
  - jacgit18
  - chatgpt
Purpose: This documentation discusses using Syncthing to sync notes in  Obsidian across devices.
Status: Done
Started: 2022-12-01
EditDate: 2024-02-03
Relates: 
dg-publish: false
---
When using Syncthing to sync your Obsidian notes across devices, there are a few things you can avoid syncing to minimize the chances of sync conflicts:

1. **Cache and temporary files**: Obsidian creates temporary files and caches data to improve performance. Exclude the cache and temporary directories from syncing to avoid conflicts caused by these files. In Obsidian's settings, you can specify the location of the cache and vault folders, and you can exclude the cache folder from syncing.

2. **Plugin data**: If you use plugins in Obsidian that generate data or store temporary files, exclude those plugin-specific directories from syncing. Check the documentation of the plugins you use to identify any directories that can be excluded.

3. **Large binary files**: If you have large binary files (e.g., videos, images, or other media) within your Obsidian vault, consider excluding them from syncing. Syncing large files can consume significant bandwidth and increase the likelihood of conflicts. Instead, consider storing such files separately and linking to them within your notes.

4. **External folders**: Obsidian allows you to link external folders to your vault. If you link a folder that contains frequently changing or dynamically generated content (such as logs or temporary files), it's advisable to exclude that folder from syncing to avoid conflicts.

5. **Nested vaults**: If you have a nested vault within your main Obsidian vault (a vault within a vault), syncing both vaults simultaneously can cause conflicts. Ensure that you're not syncing the nested vault if you want to avoid potential conflicts.

Remember to review the Syncthing documentation to understand how to configure file exclusion or folder synchronization rules according to your specific setup. Regularly backing up your Obsidian vault is also a good practice to safeguard against any data loss or sync issues.



Sure! Here are the common directories you may find in an Obsidian vault:

1. **Vault root directory**: This is the main directory where your Obsidian vault is located. It typically contains various files and folders related to your notes and configuration.

2. **`\.obsidian` directory**: This directory stores the configuration files for your Obsidian vault. It may contain files such as `config` (main configuration file), `plugins` (list of installed plugins), and `workspace` (workspace layout settings).

3. **`vault` directory**: The `vault` directory typically contains your actual note files. This is where you'll find your Markdown files (.md) or any other file formats you've chosen for your notes.

4. **`attachments` directory**: If you use Obsidian's file attachments feature to store files within your vault, the `attachments` directory will contain those files. These could be images, PDFs, or any other files attached to your notes.

5. **`plugins` directory**: When you install plugins in Obsidian, they are usually stored in a `plugins` directory. Each plugin may have its own subdirectory within this folder.

6. **`trash` directory**: When you delete notes or files within Obsidian, they are moved to the `trash` directory. This directory holds the deleted items until you decide to permanently delete them or restore them.

Remember that the exact directory structure may vary depending on your operating system and how you've set up your Obsidian vault. It's recommended to double-check your specific vault configuration to confirm the directory names and locations.


sudo systemctl start syncthing@jac  
  
sudo systemctl enable syncthing@jac  
  
  
If you have a device with other devices connected and want to connect a third device that you want to give access to that device and the devices it's connected to check introducer  
  
  
  
https://youtu.be/PSx-BkMOPF4



[Unit]  
Description=SyncThing Continuous File Synchronization  
  
[Service]  
ExecStart=/path/to/syncthing  
Restart=always  
User=your_username  
Environment=HOME=/home/your_username  
  
[Install]  
[WantedBy=multi-user.target](http://wantedby%3Dmulti-user.target/)  
  
  
sudo apt update  
sudo apt install syncthing  
syncthing  

Enable Syncthing for the current user 
systemctl --user enable syncthing 
systemctl --user start syncthing

clear  
sudo nano /etc/systemd/system/syncthing.service  
sudo systemctl daemon-reload  
sudo systemctl enable syncthing  
sudo systemctl start syncthing
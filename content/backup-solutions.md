---
aliases:
- "/Backup_Solutions"
---

# Backup Solutions
Backing up Luanti data can be a real pain due to the size and complexity of some worlds and mods. We have written this guide to provide you with some information regarding backing up data.

World Backups
-------------

[Worlds](https://wiki.luanti.org/Worlds "Worlds") will usually be contained in the Luanti data directory under the `worlds` directory.

Inside, one can see the individual worlds. For the structure of the worlds directory, see \[[the relevant wiki page](https://wiki.minetest.net/Worlds#World_directory_content)\].

To back up a world, these are some solutions:


World Backup Solutions


* Solution: Copying the directoy
  * Details: By taking the world directory and copying it somewhere else, a simple backup may be achieved.
  * Strengths and weaknesses: Will double the space taken by the world and is not very efficent
* Solution: Git
  * Details: Using a git repository to contain the world
  * Strengths and weaknesses: Again, git will take the world and save it under the .git directory for keepeing. It can be good for documenting changes but is not reccomended for most usecases
* Solution: Compression
  * Details: Using a compression algorithm to make the world smaller
  * Strengths and weaknesses: Makes a smaller file, reducing total space taken, but can be slow or memory-intensive on some devices.


Mod Backups
-----------

Due to the constantly-changing nature of mods (which both makes them securer and insecurer), creating a backup is not reccomended. Mods will eventually grow out of date and you will both miss out on the latest features and security fixes.

Mods can be backed up in the same way as worlds, or you could use the following script:

One can write down git repositories in a file and use the following script to download them again:

```
import os

# Read the file containing the list of repositories
with open('repositories.txt') as f:
    repositories = f.readlines()

# Loop through the repositories and clone each one
for repo in repositories:
    # Remove any whitespace or newlines from the repository URL
    repo = repo.strip()

    # Clone the repository using Git
    os.system(f'git clone {repo}')
```


This approach can work quite well if you want the latest features and to be able to update things.

User Data
---------

Other user data is important.

`minetest.conf` in the root directory will contain all the setting you changed, and the `screenshots` directory contains any photos you made.
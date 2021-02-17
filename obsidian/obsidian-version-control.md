---
Title: Obsidian version control 
Description: cronjob to sync obsidian with git
Date: 16-02-2021
Tags: #obsidian
References: [[obsidian-sync-script]]
Editor: markdown
---

# Obsidian version control 

1. Create a new repository on Github.  
2. Add .gitignore to ignore obsidian files. 
3. write script that performs sync. (also make it executable)


### obsidian_sync file 
Make shell script in `.local/bin/` (linux and Mac only)
```bash
touch obsidian_sync
chmod +x obsidian_sync
```

script that sync local repo with remote repo:
```bash
#!/usr/bin/env sh

OBSIDIAN_PATH = "THE ABSOLUTE PATH TO YOUR LOCAL ZETTELKASTEN REPO"
cd "$OBSIDIAN_PATH"
git pull # Check if there are no changes from other machines.

CHANGES_EXIST="$(git status --porcelain | wc -l)"

if [ "$CHANGES_EXIST" -eq 0 ]; then
	exit 0
fi

git pull
git add .
git commit -q -m "Last sync: $(date + "%d-%m-%Y %H:%M:%S")"
git push -q
```

### Cron job 
cronjob that runs every 30 minutes. ([[cronie]])
```bash 
*/30 * * * * /home/emiel/.local/bin/obsidian_sync >/dev/null 2>&1
```

[link to article](https://medium.com/analytics-vidhya/how-i-put-my-mind-under-version-control-24caea37b8a5), if still available.

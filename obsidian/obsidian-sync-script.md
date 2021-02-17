# Obsidian sync script 


```bash
#!/usr/bin/env sh

OBSIDIAN_PATH="/home/emiel/zettelkasten"
cd "$OBSIDIAN_PATH"

git pull

CHANGES_EXIST="$(git status --porcelain | wc -l)"

if [ "$CHANGES_EXIST" -eq 0 ]; then
	exit 0
fi

git pull
git add .
git commit -q -m "Last sync: $(date +"%d-%m-%Y %H:%M:%S")"
git push -q
```

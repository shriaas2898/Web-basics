# Useful linux commands
## Rename files by replacing characters
```bash
for f in *old*; do mv -v "$f" "$(echo "$f" | sed 's/old/new/g')"; done
```
## View contents on a specific line without opening the file
```bash
head -line_num filename | tail -1 filename
```
## View all the occurence of a phrase in a file
```bash
cat filename | grep "phrase"
```
**Tip:** Use `-n` with `cat` or `grep` to print line numbers along with the content.

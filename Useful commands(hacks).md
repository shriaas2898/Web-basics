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
## Delete all the tables in MYSQL matching some pattern:
Step 1:
`SELECT CONCAT("DROP TABLE ", 
GROUP_CONCAT(table_name), ";") FROM information_schema.tables WHERE 
table_schema = "<your db name>" AND table_name LIKE "some_pattern";`

Which will give you the drop command, something like:
`DROP TABLE user_value1, user_value2,......user_value1000;`

Step 2: Just paste the above command and done!

Reference: https://natchiar.wordpress.com/2010/07/28/drop-multiple-table-with-regular-expressions/ 

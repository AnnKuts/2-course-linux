`cat`
`cut`
`tail`
`less`
`head`
`join`
`paste`
`nl`
`grep`
`sed`
`wc`
`sort`
`uniq`
`split`

- `cat` - concatenate or link files together or show contens of the file

  to show contents of files:
  `cat test.txt`

  to concatenate files into one output:
  `cat test.txt test1.txt`

  to create new file from concatenated files
  `cat test.txt test1.txt > combined.txt`

  `-n` shows line numbers
  `cat -n test.txt` - number lines and even empty

  `cat combined.txt | grep --color cats`  search by word cats and highlight it

  `cat /etc/ssh/sshd_config`
  show entire file

  `cat syslog | wc -l` - word count file
- `cut` - remove sections from each line of files

  `cut -b 1 message.txt` print the first character of the file

  `-b` select by bytes
  `-c` select by character
  `-d` select by delimeter
  `-f` select by field

  `cut -b 7,8,9,10,11 message.txt` of  `cut -b 7-11 message.txt`

  The reason why entire line printed we haven't set delimeter, by default it is tabs we haven't added, so there's only one field
  `cut -d " " -f 1,2 message.txt` from tab by default we made a delimeter space so its gonna answer Learn Linux

  `cat /etc/passwd `contains a list of user accounts

  `cut -d ":" -f 1 ets/passwd`
  only seeing the username

- head - display the first few lines (or bytes) of one or more text files. by default, it outputs the first 10 lines of a file, making it invaluable for quickly previewing content without opening large files entirely

  `head /var/log/syslog` there are some logs! u can use just some other path

  `head /var/log/syslog | wc -l `(lines) show 10 lines of commands

  `head -n 25 syslog` - 25 files of syslog file

  `cat syslog | grep ssh | head`
- tail - does the same as head
  `tail /var/log/syslog`

  `tail -n 25 syslog` - 25 files of syslog file

  specific for tail command: `tail -f /var/log/syslog` follow logs in real time

- `less` - is used to view, not edit, large files or command output interactively. to exit if it is in 1 page we can use -F

  Inside `less`, you can use keyboard shortcuts:
    - `Space` → move forward one page.
    - `b` → move back one page.
    - `↑` / `↓` → scroll line by line.
    - `/word` → search forward for "word".
    - `n` → next search result.
    - `q` → quit.

- `join` - It merges two sorted text files line by line, matching fields with the same value by key field
- `paste` - merge by line number

- `nl`(number lines) - numbers lines in the list
    - `ln` → left aligned

    - `rn` → right aligned (default)

    - `rz` → right aligned, padded with zeros

  `nl -i 5 file.txt` - numbers increase by 5 (1, 6, 11, …).

  `nl -v 100 file.txt` -starts numbering at 100 instead of 1.

- `grep` - include
    - `i` → ignore case (Linux = linux = LINUX)
    - `-n` → show line numbers with matches
    - `-v` → invert match (show lines **without** the pattern)
    - `-c` → count matching lines
    - `-e` -> regular regex
    - `-E` - extended regex
    - `-r` or `-R` → recursive search in directories
    - `-l` → list only filenames with matches
    - **`-L`** → list only filenames **without** matches
    - **`-w`** → match whole words only
    - **`-x`** → match whole lines only
    - **`-o`** → print only the matching part of a line
    - `-A NUM` → show NUM lines **after** the match
    - `-B NUM` → show NUM lines **before** the match
    - `-C NUM` → show NUM lines **before and after** the match
- `sed` -  for automated text editing search, replace, delete, insert, transform.
    - `s/old/new/g` → substitute (replace all in line)
    - `Nd` → delete line N (`2d` = delete line 2)
    - `Np` → print line N (`-n` with `p` = only that line)
    - `Ni text` → insert text before line N
    - `Na text` → append text after line N
    - `Nc text` → change line N completely
    - `-i` → edit file in-place
- `wc` - word count
    - **`-l`** → count lines
    - **`-w`** → count words
    - **`-c`** → count bytes
    - **`-m`** → count characters (differs from `-c` in multibyte encodings like UTF-8)
    - **`-L`** → length of the longest line
- `sort` - sort lines in a file or input
    - `-r` → reverse order
    - `-n` → numeric sort (instead of alphabetic)
    - `-k N` → sort by column N
    - `-u` → sort and remove duplicates
- `uniq` - removes **duplicate adjacent lines** (input must be sorted first for best results).

    - `-c` → count duplicates
    - `-d` → show only duplicates
    - `-u` → show only unique lines


	`sort names.txt | uniq -c` → shows unique names with counts.

- `split` - splits a file into smaller parts,
    - `-l N` → split by N lines per file
    - `-b SIZE` → split by size (e.g., `-b 1M` = 1 MB chunks)
    - `-d` → use numeric suffixes instead of letters

  `split -l 1000 bigfile.txt part_
  → splits bigfile.txt into files of 1000 lines each, named part_aa, part_ab, etc.




щоб видалити всі пропуски то буде
`sed 's/[[:space:]]//g' file.txt`

або

`sed 's/ //g' file.txt`

### Пояснення

- `s` → substitute (заміна)

- `,` → що шукаємо (одна кома)

- `,,` → на що міняємо (дві коми)

- `g` → робити заміну глобально (для всіх входжень у рядку, а не лише першої)

`grep -e '^Bu' city.txt`

    - `^` → означає **початок рядка**.

- `Bu` → просто символи `B` і `u`.

`grep -e '8$' city.txt`

- `8` → звичайна цифра 8.

- `$` → означає **кінець рядка**.
---
grep -i -e 'austria' city.txt
-i ignore case


wc -m test.txt
head -n 9 pass.txt
`cut -d ":" -f 1 ets/passwd`

sed `s/old/new/g`

grep -vE "Spain|Vienna" filename
split -l 3 -d city.txt part
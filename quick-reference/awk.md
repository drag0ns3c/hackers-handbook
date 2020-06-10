# AWK

Awk is a programming language for manipulating streams.

### Basic syntax

The following syntax covers the basic usage of `awk`.

```text
awk '{expression}' filename
```

### Printing columns

Awk separates lines by the space character and gives access to values using the `$n` syntax.

`$0` is the entire line.

```text
ls -l ~ | awk '{print $1 " " $9}'
```

The above prints out the file/directory permissions and names in the home folder.

### Changing the delimiter

```text
cat test
1,John,Doe
2,Jane,Doe
3,Bill,Gates

$ awk -F, '{print $2}' test
John
Jane
Bill
```

The above command changes the field separator to a comma and prints out the first name.

### Add a condition

```text
awk -F, '$1 ~ /2/ {print $1 " " $2}' test
```

The above command tests the first column matches `2` before printing out the first and last names.

### Sorting a file by column

We can introduce the `sort` command to print out the names in alphabetical order \(by surname\).

```text
awk -F, '{print $3 " " $2 " " $1}' test | sort | awk '{print $3","$2","$1}'
2,Jane,Doe
1,John,Doe
3,Bill,Gates
```


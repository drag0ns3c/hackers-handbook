# Sed

Sed is a stream editor. The basic syntax is `sed s/regexp/replacement/`.

### Replace words in a file

The following example replaces the word **hello** with **goodbye** and writes the changes to new file

```text
sed 'g/hello/goodbye/g' filename > outfile
```

You can also use `gi` to ignore the case.

### Replace multiple spaces with one space

```text
sed 'g/  */ /g' filename
```

### Replacing words within a range

Use the syntax `{from line number},{to line number}` to limit the operation

```text
sed '20,40 g/hello/goodbye/gi' filename
```

### Remove comments from files

The following example will remove blank lines and lines beginning with `#` from a file.

```text
sed '/^#\|^$\| *#/d' filename
```

### In place editing

The example so far will print out the result to STDOUT. You can also use the `-i` flag to edit the file in place.

You can combine this to create a backup of the original file.

```text
sed -i'.backup' 's/search/replace/g' filename
```


# Grep & Egrep

### Basic syntax for searching a file

```text
grep "word" filename
```

### Ignoring case sensitivity

Grep is case sensitive by default. Use `-i` to ignore case.

```text
grep -i "word" filename
```

### Recursive search

Use the `-r` flag to search recursively through a directory.

```text
grep -r "word" /path/to/dir
```

### Match whole words

Use `-w` to match the word boundary for example `word` and not `words`.

```text
grep -w "word" filename
```

### Show the line number

Use `-n` to display the line numbers of each match.

```text
grep -n "word" filename
34: many words make a sentence
```

### Using regular expressions

Use grep with the `-E` \(extended\) flag or `egrep` equivalent.

```text
grep -E "(wo[a-z]{1}d)" filename
egrep "(wo[a-z]{1}d)" filename
```

### Invert the match

Use the `-v` to invert the match, for example match lines where **word** does not appear

```text
grep -v "word" filename
```


# Watching files

There are two useful commands to monitor for file changes, `tail` and `watch`.

### Tail

The `tail` command will output the last part of a file.

#### Reading files for changes

The `-f` flag will **follow** changes, i.e. you’ll see new lines appear on the screen as they are added.

```text
tail -f /var/log/*.log
```

You could combine this with grep to filter for certain lines.

```text
tail -f /var/log/*.log | grep 'ERROR'
```

### Watch

The `watch` command will execute a command periodically.

#### Watch a folder for file changes

```text
watch ls /path/to/folder
```


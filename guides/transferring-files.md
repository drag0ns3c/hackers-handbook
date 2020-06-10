# Transferring files

Once you are on a target machine, you will often want to transfer some files. The options available to you will depend on the tools on the box. Below are a few options given the availability of certain tools on the target machine.

## Run a HTTP server

On the machine that you want to transfer files from, you'll need to run a web server. This is simple provided some common tools are available on the machine.

### Python

This will spawn a web server listening on port `8000` from the current directory.


```bash
# Python 2
python -m SimpleHTTPServer
```

```bash
# Python 3
python -m http.server
```

### PHP

The following command will start a server listening on port `8000`.

```bash
php -S 0.0.0.0:8000
```

### Ruby

The following was tested working with Ruby `2.7.1` and should work with versions > `1.9.2`

```bash
ruby -run -e httpd . -p 8000
```

### NodeJS

By default there isn't a quick script to run using the standard library to run a static server. However, with the `npx` command, we can use the `http-server` package.

```bash
npx http-server -g -a 0.0.0.0 -p 8000
```

The above command will launch a server listening on port `8000` and transfer all files using gzip compression.

### Busybox

```bash
busybox httpd -f -p 8000
```

## Downloading files

...TBC
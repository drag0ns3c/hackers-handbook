# Transferring files

Once you are on a target machine, you will often want to transfer some files. The options available to you will depend on the tools on the box. Below are a few options given the availability of certain tools on the target machine.

## Python

If the target machine has an IP that you can reach over HTTP, then you can spawn a web server.

```bash
# Python 2
python -m SimpleHTTPServer
```

```bash
# Python 3
python -m http.server
```

This will spawn a web server on port `8000`.
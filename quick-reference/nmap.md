# Nmap

Nmap is used heavily in network reconnaissance. These cheats are useful for discovering what is on the network and can typically be used from day to day.

## Performing a quick scan

To run a quick scan to discover hosts, use the `-F` flag. This will test fewer ports than the default scan.

```text
nmap -F 192.168.0.0/24
```

## Operating system detection

You can sometimes guess what the OS is by the services running on the machine. However, this can sometimes be inaccurate due to the ay the machine is configured. Nmap can do this for us with the `-O` flag.

```text
sudo namp -O 192.168.0.0/24
```

## Detecting software versions

Nmap can also try to determine the software versions running.

```text
nmap -sV 192.168.0.0/24
```


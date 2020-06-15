# Nmap

Nmap is used heavily in network reconnaissance. These cheats are useful for discovering what is on the network and can typically be used from day to day.

## Performing a quick scan

To run a quick scan to discover hosts, use the `-F` flag. This will test fewer ports than the default scan.

```bash
nmap -F 192.168.0.0/24
```

## Scanning types

### SYN scan

This is the default option that nmap will do (if the user has the right privileges). It sends a TCP `SYN` packet and waits for a `SYN/ACK`.

```bash
nmap -sS 192.168.0.0/24
```

### TCP connect

If Nmap cannot perform a SYN scan, this is an option. It will ask the operating to connect to the target(s) and initiate a 3 way handshake.

```bash
nmap -sT 192.168.0.0/24
```

### UDP san

```bash
nmap -sU 192.168.0.0/24
```

## Operating system detection

You can sometimes guess what the OS is by the services running on the machine. However, this can sometimes be inaccurate due to the ay the machine is configured. Nmap can do this for us with the `-O` flag.

```bash
sudo namp -O 192.168.0.0/24
```

## Detecting software versions

Nmap can also try to determine the software versions running.

```bash
nmap -sV 192.168.0.0/24
```

## Adjust timing options

You adjust the timing of the scans to be quicker or slower (to avoid detection) using the `-TN` option

| Option | Description |
| --- | --- |
| `-T5` | Top speed and very aggressive. If the network cannot take this bandwidth, it may bring it down |
| `-T4` | Quicker |
| `-T3` | Standard. This is the default timing |
| `-T2` | Slower - around 10 times slower than standard |
| `-T1` | Slow. You can usually avoid IDS |
| `-T0` | Super slow. |
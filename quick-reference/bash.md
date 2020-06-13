# Bash

### Environment Variables

Environment variables are values that you will find set in each bash terminal. They are used by many processes to control the runtime behaviour of the system.

### Viewing Environment Variables

To see a list of the current environment variables run `env`.

```text
env
...
COLORFGBG=15;0
DBUS_SESSION_BUS_ADDRESS=unix:path=/run/user/1000/bus
DESKTOP_SESSION=lightdm-xsession
DISPLAY=:0
GDMSESSION=lightdm-xsession
...
```

With the above output you could grep for the environment variable you are looking for.

```text
env | grep PATH
PATH=/home/kali/.nvm/versions/node/v12.17.0/bin:/home/kali/.pyenv/shims:/home/kali/.pyenv/bin:/usr/local/bin:/usr/bin:/bin:/usr/local/games:/usr/games
```

### Setting environment variables

You can set an env var for a one off command by prefixing the command you want to run

```text
MY_ENV_VAR=123 command
```

You can also set it permanently for your current session using `export`

```text
export MY_ENV_VAR=123

env | grep MY_ENV_VAR
MY_ENV_VAR=123
```

To set an environment permanently for the current user, update the `.bash_profile` file in the users’ home directory.

```text
echo 'export MY_ENV_VAR=123' >> ~/.bash_profile
```

You can also set it permanently for all users by adding to a file in the `profile.d` directory

```text
sudo echo 'export MY_ENV_VAR=123' >> /etc/profile.d/global.sh
```

### Updating the PATH variables

The `PATH` variables is a special variable on linux systems, when you call a command, the shell will search each directory specified in the `PATH` to find the command to execute. Sometimes, you’ll want to add a new path value to make your command found first.

You would do this by placing your new path first and resetting the value. For example;

```text
export PATH=/home/user/custom/path/bin:$PATH
```

### Useful environment variables

| Name | Description | Example |
| :--- | :--- | :--- |
| $PWD | The path to the current directory | /home/drag0ns3c |
| $HOME | The path to the home directory of the current user | /home/drag0ns3c |
| $USER | The name of the current user | drag0ns3c |
| $SHELL | The path to the current shell | /bin/bash |


## Managing processes

By default all processes you run in the terminal run in the foreground until they stop, either naturally or forcefully.

### Foreground processes

You can stop a process by entering `Ctrl+C`. This will send a `SIGNINT`, indicating tha the user requested the process to stop.

When a process is running in the foreground, you will not be able to use the terminal. You may be able to suspend the process by entering `Ctrl+Z`. This will send a `SIGTSTP`.

```bash
ping -i 5 google.com
# Ctrl+Z
[1]  + 37292 suspended ping -i 5 google.com
```

To see the processes associated with your current terminal, enter `ps T`.

```bash
ps T
PID TTY      STAT   TIME COMMAND
32033 pts/1    Ss     0:01 /usr/bin/zsh
37416 pts/1    T      0:00 ping -i 5 google.com
37552 pts/1    R+     0:00 ps T
```

You can resume the process by entering `fg` into the command line.

```bash
fg
[1]  + 37292 continued  ping -i 5 google.com
64 bytes from lhr25s27-in-x0e.1e100.net (2a00:1450:4009:80a::200e): icmp_seq=2 ttl=119 time=15.4 ms
```

### Background processes

To send a process to the background, use the ampersand operator at the end of the command.

```bash
ping -i 5 google.com &
[1] 3565
```

It will output the process ID (3656) to the terminal. It will also print the `STDOUT` to the terminal.

If you want to kill the process, enter `kill -9 [process id]`.

To see a list of background jobs associated with the terminal session, enter `jobs`.

### Moving foreground processes to the background

The first step is to suspend the process with `Ctrl+Z` and the send it to the background with `bg`.

### Moving a background process to the foreground

To move the most current background process to the foreground, enter `fg`. You can view the list of jobs with the `jobs` command. If the job you want to move to the foreground is not the most recent one, you can specify the job number.

```bash
fg %2 # 2 is the job number
```

### Continuing processes after the terminal session

When you exit the terminal, all processes started by it with end, even if they are in the background. This is because a `SIGHUP` is sent to all processes.

To deal with this you can use the `nohup` command.

```bash
nohup ping -i 5 google.com &
```

All output will be sent to a file named `nohup.out`.

To kill the process you will need its process id. You can use `pgrep` for this.

```bash
pgrep -a ping
7360 ping -i 5 google.com
```
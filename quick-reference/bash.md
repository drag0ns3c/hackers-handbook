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

## [Hackers ](https://hackers-handbook.readthedocs.io/index.html)


# UNIX Cheat Sheet

</br>
<p align="center">
  <img src="/img/unix.png" width=700 />
</p>
</br>

A few useful tools can be found here (or commands I have trouble memorizing).


- glances is an insane monitoring tool to view CPU, memory, disk, network usage, running processes... [link here](https://github.com/nicolargo/glances)
```
glances
```

- htop is a cool and lighter tool to monitor processes running on your machine 
```
htop
```

- tmux is a terminal multiplexer, especially useful to run processes in the background
```
tmux
tmux ls
tmux attach
tmux kill-session
C-b d # detach
C-b % #Split horizontally
C-b " # Split vertically
...
```

- Know storage on machine
```
df (-h)
```

- know RAM memory
```
free  
```

- know disk usage

**Install ncdu and run it !**

```
du -h
du -hs YOUR_FOLDER_NAME # To see the full size (including whole content) of a folder in a directory
du -c FOLDER  # memory of a folder only
```

- know ports in use:

```
sudo lsof -i -P -n | grep LISTEN
```

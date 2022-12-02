# tmux

## Enable scrolling

`vim ~/.tmux.conf`

Add the following lines to the file :
```
# For the Tmux version 2.1 and up 
set -g mouse on 
```
And finally `tmux source-file ~/.tmux.conf`

- Holding 'Shift' will bring back OS-default behavior which then lets me copy with select + right-click and paste with right-click.	

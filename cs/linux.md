# A few survival tips with Linux

- [A few survival tips with Linux](#a-few-survival-tips-with-linux)
  - [Navigate files and directories :boat:](#navigate-files-and-directories-boat)
    - [Where am I ?](#where-am-i-)
    - [Looking at the contents of directories with  `ls`](#looking-at-the-contents-of-directories-with--ls)
    - [grep \& mv](#grep--mv)
    - [grep \& head](#grep--head)
  - [Running processes](#running-processes)
  - [Find directories' size](#find-directories-size)


## Navigate files and directories :boat:
### Where am I ?  
When you open a bash shell, or login into a remote server, you are tipically in your home directory. 

```bash
$ pwd # print working directory
```
Output 
```bash
/home/julie
```
### Looking at the contents of directories with  `ls` 



### grep & mv 
move all the files contained in the current dir finishing by *1.png* into the *test* dir. 
```bash
mv $( ls | grep 1.png) test
```
### grep & head
```bash
ls | grep 0.png | head -n 10
```

## Running processes 

running python code in background & keeping the output : 
```bash
python3 preprocessing/preprocessing_parts.py > output_preprocess_20h57.log
```

Executes 1.py in background & wirte the stout to the file 1.ouput. 
```bash
nohup sh scheduler/preprocessing.sh > logs/output_prepro_ch_visuel.output &
```

## Find directories' size
- Top 40 directories by size
```bash
sudo du -hsx /* | sort -rh | head -n 40
```



<!-- ## change interpreter in vscode 
`ctrl + shift + P` and select __python interpreter__.	 -->

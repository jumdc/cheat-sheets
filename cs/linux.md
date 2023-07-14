# Tips & tricks with Linux :pinguin:

- [Tips \& tricks with Linux :pinguin:](#tips--tricks-with-linux-pinguin)
    - [grep \& mv](#grep--mv)
    - [grep \& head](#grep--head)
  - [running processes](#running-processes)
  - [Find directories' size](#find-directories-size)
  - [change interpreter in vscode](#change-interpreter-in-vscode)


### grep & mv 
move all the files contained in the current dir finishing by *1.png* into the *test* dir. 
```bash
mv $( ls | grep 1.png) test
```
### grep & head
```bash
ls | grep 0.png | head -n 10
```

## running processes 

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



## change interpreter in vscode 
`ctrl + shift + P` and select __python interpreter__.	

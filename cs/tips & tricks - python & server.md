# Tips & tricks for using a server



## Summary 
1. [Basic linux cmd](#cmd)
2. [Running processes](#background)
3. [Logging](#log)
4. [Change interpreter in VScode](#interpreter)

 
## Basic Linux Command <a name='cmd'> </a>
### grep & mv 
move all the files contained in the current dir finishing by *1.png* into the *test* dir. 
```bash
mv $( ls | grep 1.png) test
```
### greap & head
```bash
ls | grep 0.png | head -n 10
```

## running processes<a name='background'> </a>

running python code in background & keeping the output : 
```bash
python3 preprocessing/preprocessing_parts.py > output_preprocess_20h57.log
```
Executes 1.py in background & wirte the stout to the file 1.ouput. 

```bash
nohup sh scheduler/preprocessing.sh > logs/output_prepro_ch_visuel.output &
```

## logging <a name='log'> </a>
The `logging` module in Python provides a default logger that allows to get started without much configuration. 

:exclamation: by default `debug()`and `default()`do not get logged. 

### Basic configurations 

Use the method : `basicConfig(**`_`kwargs`_`)`
Basic __parameters__ : 
-   `level`: The root logger will be set to the specified severity level.
-   `filename`: This specifies the file.
-   `filemode`: If  `filename`  is given, the file is opened in this mode. The default is  `a`, which means append.
-   `format`: This is the format of the log message.

__Example__ : 
```python
import logging

logging.basicConfig(format='%(asctime)s - %(message)s', level=logging.INFO)
logging.info('Admin logged in')
```
output : 
```bash
2018-07-11 20:12:06,288 - Admin logged in
```

## change interpreter in vscode <a name='interpreter'> </a>
`ctrl + shift + P` and select __python interpreter__.	

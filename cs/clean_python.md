# How do write clean python code ? 

- [How do write clean python code ?](#how-do-write-clean-python-code-)
  - [Formatting and linting](#formatting-and-linting)
    - [Formatter](#formatter)
      - [**Black**](#black)
    - [Linting](#linting)
      - [Why using linting ?](#why-using-linting-)
      - [**Pylint**](#pylint)


## Formatting and linting

### Formatter

> Code formatters make sure the codebase stays in a consistent style without any manual work. 

#### **Black**
Black can be considered as the de-facto formatter for Python projects. 

  - Install the latest version   
  `pip install black`
  - Run it on one or more files  
   `black {source_file_or_directory}`
    
### Linting

> Linting is performed while the source code is written and before it's compiled, i.e linting is a pre-build check also called **static code analysis**. 

#### Why using linting ?
Regularly checking code with linting ensures consistensy accross the codebase. It minimizes the probability of small errors. 
It checks for errors, enforces a conding standard and can make suggestion about how the code should be refactored.


#### **Pylint**
> Pylint analyses your code without running it. 

- Install  
`pip install pylint`

- Use  
`pylint {file_name}`

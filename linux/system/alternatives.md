#Using Alternatives in Linux

   I have been noticed that people don't use “alternatives mechanism”. May be you faced with situation when you have several version of an application and sometimes you must switch off version.  Someone created script in /usr/local/bin/clang-formater and put there correct path to the application. It looks similar but you should use standard mechanism of Linux. 
   
1. You should determinate absolute path of  the clang-fromat. 
```bash
clang-format-3.5
```
2. Install alternative
```bash
update=a;ternatives –install /usr/bin/clang-format clang-fromat /usr/bin/clang-format-3.5 1
```

Arguments:
-  argument is path to alternative
- name of alternative
- path to the version

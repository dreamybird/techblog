#Using Alternatives in Linux

   I have noticed that people don't use “alternatives mechanism”. Maybe you faced with a situation when you have several version of an application and sometimes you must switch version. 
   Lately, I read instruction where author offers create a symlink instead of create an alternative. It looks similar but you should use standard mechanism of Linux. 
   In the case, I will consider an example with clang-format.
   
1.You should determine absolute path of the clang-format
```bash
which clang-format-3.5
```
2.Install the alternative
```bash
update-alternatives –install /usr/bin/clang-format clang-fromat /usr/bin/clang-format-3.5 1
```

Arguments:
- a path to alternative
- name of alternative
- a path to the version
- priority where a higher item is prefered

#Using Alternatives in Linux

   I have noticed that people don't use “alternatives mechanism”. May be you faced with situation when you have several version of an application and sometimes you must switch version. 
   Lately I read instruction where author offers create symlink instead of create an alternative. It looks similar but you should use standard mechanism of Linux. 
   In the case I will consider example with clanclang-format.
   
1. You should determine absolute path of the clang-format.
```bash
clang-format-3.5
```
2. Install the alternative
```bash
update=a;ternatives –install /usr/bin/clang-format clang-fromat /usr/bin/clang-format-3.5 1
```

Arguments:
- path to alternative
- name of alternative
- path to the version

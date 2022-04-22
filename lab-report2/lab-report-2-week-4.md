# Lab Report 2
**This lab will help you with the debugging.**

## 1. Error 1
You can download the test file [here](https://github.com/Meng-zmy/cse15l-lab-reports/blob/1557d6dd6053e678865c2efaba30832bdc7d7d9c/lab-report2/test-file1.md)

*This is the test file I have now:*
```
# Title

[link1](https://something.com)
![image](image.png)
[link2](some-thing.html)
```

**Symptom:** By using this test file, the result I get is incorrect. We want to have only the address of the link, but it also print out the address of the image. Since the image format is `![]()`, it also contain `[]()`.

![image](error1.png)

To solve this error, we need to deal with the `!`. Since the only differece between image format and link format is `!`.

So, I add a if statement to check the character before the `[` whether is `!` or not. If it is `!`, it will not add the address to the *toRetrun*; otherwise, if it is not `!`, it will add the address to the *toRetrun*.

Here is the code change for my `MarkdownParse1.java`.

![image](change_1.png)

After I change my `MarkdownParse1.java`, the result I get is correct.

![image](after_change1.png)


## 2. Error 2
You can download the test file [here](https://github.com/Meng-zmy/cse15l-lab-reports/blob/c4a32b11d23344a9e96b63751c254031fb33f21f/lab-report2/test-file2.md)

*This is the test file I have now:*
```
# Title

[link1](https://something.com)
[link2](some-thing.html)

hshshshshhshshshshshshshshh
```

**Symptom:** By using this test file, it raise an OutOfMemoryError. Since there is no `[]()` can be find in last two line of the test file, the *currentIndex* will not be update, and our while loop will go infinite times until out of memory.

![image](error2.png)

To solve this error, we need to deal with the situtation that has no more `[]()` at the end.

So, I add a if statement to check after every link format `[]()` is there any more `[` after the *currentIndex* (Since the link format is begin with `[`). If there is no `[` after the *currentIndex*, we directly break the while loop and return the *toReturn*; otherwise, continue the while loop to find other link.

Here is the code change for my `MarkdownParse2.java`.

![image](change_2.png)

After I change my `MarkdownParse2.java`, the result I get is correct.

![image](after_change2.png)


## 3. Error 3



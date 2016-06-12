---
layout: post
status: publish
published: true
title: Software Construction Batch Compile Script
author:
  display_name: Jeff
  login: admin
  email: cjw39@hotmail.com
  url: ''
author_login: admin
author_email: cjw39@hotmail.com
wordpress_id: 393
wordpress_url: http://codenuggets.com/?p=393
date: '2013-02-07 05:12:19 -0600'
date_gmt: '2013-02-07 05:12:19 -0600'
categories:
- School
- Teaching
tags:
- Linux
- C
- Ubuntu
- COMP2710
- bash script
- batch compile
- grading
comments: []
---
I have been working on a bash shell script lately to batch compile assignment program submissions for the software construction (C++) course. Before batch compile though, I have down all the student submissions. I found that Canvas, the new student submission system, made it easier; all I have to do is click on download all submission and the system would bundle all submission into one zip file and files according to student name.

The script resides in the root directory for the assignment, which has the following sub-directories:

- build_log: contains one file for each program compiling.
- exe: the executables from the batch compiling.
- result: output from the run of each executable.
- src: all C++ source files.
- test_cases: each file is a test case, which is redirect as an input to the program.

The bash script is compiles all source (.cpp) files in `src`, and puts compile executables into a `exe`. It then runs executable with input redirect from the files in `test_case` dir, and save execution output in `result`. The following is the bash script.

{% highlight bash %}
#!/bin/bash
for i in $(ls src); do
    g++ src/$i -o exe/$i.exe > build_log/$i.build 2>&1
done

for i in $(ls exe); do
    exe/$i < test_cases/test_case_1.txt >> result/$i.run.txt 2>&1
    echo "" >> result/$i.run.txt
    echo "" >> result/$i.run.txt
    exe/$i < test_cases/test_case_2.txt >> result/$i.run.txt 2>&1
    #echo "" >> result/$i.run.txt
    #echo "" >> result/$i.run.txt
    #exe/$i < test_cases/test_case_3.txt >> result/$i.run.txt 2>&1
done
{% endhighlight %}

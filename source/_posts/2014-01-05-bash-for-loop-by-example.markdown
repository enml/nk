---
layout: post
title: "bash for循环用法示例"
description: bash for循环的常见用法
date: 2014-01-05 14:36:30 +0800
comments: true
tags: linux, bash
categories: Bash
---

>来源：[Bash For Loop Examples](http://www.cyberciti.biz/faq/bash-for-loop/)  编译：lingguo

#### 1. for循环的第一种形式：

    {% highlight bash %}
    for variable in 1 2 3 4 5
    do
        command
    done
    {% endhighlight bash %}

示例1：

    {% highlight bash %}
    #!/bin/bash
    for i in 1 2 3 4 5
    do
       echo "Welcome $i times"
    done
    {% endhighlight %}

连续的值，可以通过{start..end}缩写，如1 2 3 4 5可以表示为：{1..5}，如：
示例2：

    {% highlight bash %}
    #!/bin/bash
    for i in {1..5}
    do
       echo "Welcome $i times"
    done
    {% endhighlight %}


bash 4.0及以上，支持设置变量的自增的步数，语法是：{start..end..increment}, 如：
示例3：

    {% highlight bash %}
    #!/bin/bash
    echo "Bash version ${BASH_VERSION}..."
    for i in {0..10..2}
      do
         echo "Welcome $i times"
    done
    {% endhighlight %}

使用for遍历文件，语法为：

    {% highlight bash %}
    for file in file1 file2 file3 file4
    do
        commands
    done
    {% endhighlight %}

示例4：

    {% highlight bash %}
	#!/bin/bash
	for file in /etc/*
	do
		if [ "${file}" == "/etc/resolv.conf" ]
		then
			countNameservers=$(grep -c nameserver /etc/resolv.conf)
			echo "Total  ${countNameservers} nameservers defined in ${file}"
			break
		fi
	done
    {% endhighlight %}

 
其中for file in /etc/* 等价于：

	for file in `ls /etc/*`    
	for file in $(ls /etc/*)
 

####2. for循环的第二种形式：

与C语言for循环类似的语法：

	for (( EXP1; EXP2; EXP3 ))
	do
		commands
	done

示例5：

    {% highlight bash %}
	#!/bin/bash
	for (( c=1; c<=5; c++ ))
	do
	   echo "Welcome $c times"
	done
    {% endhighlight %}
 

当for的EXP1，EXP2，EXP3都为空时，即为无限循环：
示例6：

    {% highlight bash %}
	#!/bin/bash
	for (( ; ; ))
	do
	   echo "infinite loops [ hit CTRL+C to stop]"
	done
    {% endhighlight %}
 

#### 3. for循环也支持break和continue关键字，与C语言一致

示例7：

    {% highlight bash %}
	#!/bin/bash
	for file in /etc/*
	do
		if [ "${file}" == "/etc/resolv.conf" ]
		then
			countNameservers=$(grep -c nameserver /etc/resolv.conf)
			echo "Total  ${countNameservers} nameservers defined in ${file}"
			break
		fi
	done
    {% endhighlight %}
 

示例8：

    {% highlight bash %}
	#!/bin/bash
	FILES="$@"
	for f in $FILES
	do
		# if .bak backup file exists, read next file
		if [ -f ${f}.bak ]
		then
			echo "Skiping $f file..."
			continue  # read next file and skip cp command
		fi
		# we are hear means no backup file exists, just use cp command to copy file
		/bin/cp $f $f.bak
	done
    {% endhighlight %}


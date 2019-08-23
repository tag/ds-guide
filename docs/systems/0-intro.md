# Introduction
This course—and consequently, this text—is designed to be as hands-on as
possible. We will cover some theory, but its primary purpose is to introduce
technologies that reinforce theoretical learning in other courses.

By the end of the course you will have a better understanding of different types
of data and how data are used for different purposes. You will understand some
of the tradeoffs made by designers in data and systems, and describe and use
multiple data formats. You will be able to describe the "devops" process (and
even practice some of the steps), will better understand cloud computing and
virtualization, version control, APIs, web services, and software design
patterns. You will build a working multi-tier web application, and use a
unix-style command line.

## Projects and software
Along the way we will use:

* HTML
* Javascript, including the [Vue.js] library and the modern Fetch API
* [Apache], the world's most-used web server[^apache]
* [PHP]
* [MySQL] and SQL
* [Docker]
* [Amazon Web Services]
* ... and many other cool things

[Apache]: https://www.apache.org
[MySQL]: https://dev.mysql.com/downloads/
[PHP]: https://www.php.net
[Vue.js]: https://vuejs.org/v2/guide/
[Docker]: https://www.docker.com
[Amazon Web Services]: https://aws.amazon.com

This text can't possibly provide good tutorials for all of those things, but I
will try to link to some of the best resources I've found on the Internet.

[^apache]: According to the [July 2019 Netcraft survey][netcraft-2019-07],
Apache has top market share in the most active sites, busiest sites, and
domains. It's been slowly losing ground to [nginx] and [Microsoft's IIS][IIS]

[netcraft-2019-07]: https://news.netcraft.com/archives/2019/07/26/july-2019-web-server-survey.html
[nginx]: https://www.nginx.com
[IIS]: https://www.iis.net

## What you should already know

Hopefully, you're at least somewhat familiar with your computer. You should also be
able to install applicaitons and follow instructions. (It might surprise you how
frequently that last condition isn't met.) If you aren't already familiar with
HTML, CSS, and SQL, then it will be helpful to seek out some tutorials when we
encounter those languages.

I expect you've used at least one object-oriented programming language, although
it really doesn't matter which one. C# and Java are good choices. Scripting
languages like Python, PHP, or Ruby fit the ticket if used in an object-oriented
way. Again, it doesn't really matter which one, so long as you have some
familiarity with basic control structures like `if` statements and loops, and
a basic understanding of polymorphism and inheritence.

*[HTML]: Hyper Text Markup Language
*[CSS]: Cascading Style Sheets
*[SQL]: Structured Query Language

Along the way you'll get some practice with the Unix command line. Many
technical systems rely on the command line or text files for configuration,
and it's good to know how to navigate and run commands. I will explain commands
the first time we use them, but a good quick reference page or tutorial of the
Unix command line may be useful to you.

To begin, you should know `ls`, `mkdir`, and `pwd`.

!!! note "Command Line Tutorials"
    If you are not familiar with the command line, any of these references
    provide a excellent tutorials:
    
    * [_The Linux Command Line_][TLCL] by William Shotts has book and web
    versions.
    * [_Learn Enough Command Line to Be Dangerous_][LECLtbD] by Michael Hartl
    has the first few chapters of the book online. I recommend Chapter 1 and
    Section 2.2 to start.
    * CodeAcademy.com has a course ["Learn the Command Line"][CA-CL], which
    allows you to practice as you learn.

[LECLtbD]: https://www.learnenough.com/command-line-tutorial/basics
[TLCL]: http://linuxcommand.org/lc3_learning_the_shell.php
[CA-CL]: https://www.codecademy.com/learn/learn-the-command-line


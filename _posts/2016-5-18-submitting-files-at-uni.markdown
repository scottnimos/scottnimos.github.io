---
title:  "Submitting Assignments at Uni"
date:   2016-5-18 7:00:00
description: "At Uni we have submit each file separately and then accept an agreement. This can be incredibly tedious when you few files for your assignment... There has to be a better way."
---

At La Trobe we have to submit each file separately and then accept an agreement.

![command executed on uni server](../../assets/images/2016-05-18-Assignment.jpg)

This can be incredibly tedious when you have lots files in your project...
Here I have 12 java files and that means I have to write 12 commands.
>submit SubjectCode fileName.java

There has to be a better way, I should also mention there is another command "verify", which
shows the files that have been submitted. The process is still long, tedious and I feel like I'm going cross-eyed making sure everything is handed in.

![cross-eyed](http://vignette3.wikia.nocookie.net/uncyclopedia/images/c/cf/Crosseyed.jpg/revision/latest?cb=20070821135109 =250x)

I know the problem can be tackled with bash scripting, but I'm not too familiar with the syntax.
So after a few loathing minutes with my old friend Google, I was off to the races to solve
the tingling pain I get when I have to submit my coding assignment.

I was fairly happy with the result.

{% highlight bash linenos %}
#!/bin/bash
SUBJECT="$1" #e.g. "IOO"
TYPE="$2"
for file in $TYPE
do
   submit "$SUBJECT" "$file"
done
verify
{% endhighlight %}

All I have to do now is execute
>./submitAssignment.sh SubjectCode *.java

Though there is still a problem, I still have to accept that annoying plagiarism statement.
After a while I stumbled upon the [pipeline](http://tldp.org/HOWTO/Bash-Prog-Intro-HOWTO-4.html), I've used it before but I forgot about the loaded
magic it beholds.

```bash
#!/bin/bash
SUBJECT="$1" #e.g. "IOO"
TYPE="$2"
for file in $TYPE
do
   echo 'y' | submit "$SUBJECT" "$file"
done
verify
```

Sweet now submitting my Uni assignments is a breeze, so I can get to more interesting things.
If you attend La Trobe like myself and find this helpful feel free to use this little gem.

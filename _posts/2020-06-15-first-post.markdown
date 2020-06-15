---
layout: post
title:  "First Post"
date:   2020-06-15
categories: jekyll update
---
This is my first post, `just` a test to get the hang of it

You can find me at: [Website][my_website]
{% highlight python %}
    def populateChannelList(self):
        # file must be in same directory as the script
        FILEPATH = os.path.join(os.path.dirname(os.path.realpath(__file__)),
                            "canaletv.txt")
        # lines from file with "channel name" -- "link"
        channelArray = []
        # split file by line and adding it to the array
        with open(FILEPATH) as f:
            for line in f:
                channelArray.append(line.rstrip())
        # dictionary with key = channel name and value = link
        self.channelDict = dict(ch.split(" -- ") for ch in channelArray)
        for channel in self.channelDict.keys():
            item = QStandardItem(channel)
            self.model.appendRow(item)
{% endhighlight %}

[my_website]: https://emanuel-mazilu.github.io
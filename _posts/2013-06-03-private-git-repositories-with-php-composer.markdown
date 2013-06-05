---
layout: post
title:  "Private git repositories with PHP's composer"
date:   2013-06-03 21:12:21
categories: git composer 
---

[Composer][composer] is a dependency management tool for PHP, it just like [Rubygems][rubygems]. However, to deal with private git repositories, it doesn't work for me if I follow the instructions at [this page][composer-pr], what I found that there is another way to work with private git repositories is something like:

{% highlight json %}
{
    "name": "my/app",
    "repositories": [
        {
            "type": "package",
            "package": {
                "name": "vendor/analyze",
                "version": "1.0.0",
                "source": {
                    "type": "git",
                    "url": "git@host:/path/to/vendor/analyze.git",
                    "reference": "master"
                }
            }
        }
    ],
    "require": {
        "vendor/analyze": "1.0.0"
    },
    "autoload": {
        "psr-0": {"Analyze": "src/"}
    }
}
{% endhighlight %}

The structure of the analyze package looks like:
{% highlight text %}

├── composer.json
├── src
│   └── Analyze 
│       └── Generator.php
└── vendor
{% endhighlight %}

Actually, with the `package` type, you can use any kind of [packages][composer-pg].

[composer]: http://getcomposer.org
[composer-pr]: http://getcomposer.org/doc/05-repositories.md#using-private-repositories 
[composer-pg]: http://getcomposer.org/doc/05-repositories.md#package-2 
[rubygems]: https://rubygems.org

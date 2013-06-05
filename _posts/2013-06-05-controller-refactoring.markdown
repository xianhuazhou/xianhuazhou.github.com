---
layout: post
title:  "Controller Refactoring"
date:   2013-06-05 10:52:21
categories: Refactoring MVC
---

When we working with MVC frameworks such as [Ruby on Rails][ror], [Play framework][play], [Zend framework][zf] ..., most of the time, we are working on `controllers` (a series of `actions` of `controllers`). 

In the beginning, a controller could just contain coupld of action methods. For example, a `UserController` (in RoR) could look like:
{% highlight ruby %}
class UserController < ApplicationController
  def register
  end

  def login
  end

  def logout
  end
end
{% endhighlight %}

That's fine, user can register, login or logout with the controller. We could also add more functions to the `UserController`, e.g. user need to change his/her profile, change password, so the `UserController` looks like:
{% highlight ruby %}
class UserController < ApplicationController
  def register
  end

  def login
  end

  def logout
  end

  def edit_profile
  end

  def change_password
  end

end
{% endhighlight %}

Some days later, we have more functions need to implement which relate to users, e.g. changing e-mail address, saving search results, sending emails, changing avatar etc. So, do we still add these `user` related functions into the `UserController`? Yes or No, if that's all of functions of the project, and you don't need to touch it again, you could put everything into the `UserController`. Otherwise, you have to think about to put them into other controllers (or libraries) and to define some good names for that. 

Too many actions in a single controller just like a large method contains many lines of code, even if the length of each action is short, it's hard to read and maintain. 

However, most of programming languages such as Ruby, PHP, Scala etc., which allow you to separate 1 `large` class into small things(classes, modules, [traits][traits] ...). Whenever a controller class is too large, and there are still some functions need to add into the class, STOP to do this. Try to spend some time to make it smaller and move some actions to other controllers/libraries.

So, about the `UserController` example, we could define some other controlers such as `UserAuthController`, `UserProfileController`, `AdminController` etc. to do the refactoring.

[ror]: http://rubyonrails.org
[play]: http://www.playframework.com
[zf]: http://framework.zend.com
[traits]: https://en.wikipedia.org/wiki/Trait_%28computer_programming%29

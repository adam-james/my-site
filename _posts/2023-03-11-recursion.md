---
layout: post
title:  Learning Recursion
date:   2023-03-11 06:42:12 -0800
---

Recursion can be a tough topic when you are first learning to code. It's not as straightforward as writing a loop. It hides a bit of the complexity. But if you stick with it, it'll open your mind to a new way of thinking.

## Breaking it Down

When thinking recursively, you want to break your problem down into parts -- parts that can be repeated. Beyond that, you'll want to break those parts down into cases. There are two common cases in recursive parts: the base case and the recursive case. More on that in a bit.

## From Iterative to Recursive

Let's look at an iterative function. This function takes a number and counts down from that number to zero.

{% highlight ruby %}
def countdown(number)
  while not number < 0
    puts number
    number -= 1
  end
end
{% endhighlight %}

This function can broken down into the following instructions: While number is greater than or equal to zero, print number, then subtract one from the number and do the same thing again. This "do the same thing again", signals to us that we could solve this problem recursively. In fact, all iterative problems could be solved recursively.

So how do we translate this into a recursive function. Well, we've got to figure out three things: what action to take at each step, how to continue to the next step, and when to stop. So what action are we taking? We are printing the number. How do we continue? We subtract one from the number. When do we stop? When the number is less than zero. 

This last question -- "When do we stop?" -- is often called the base case, and it usually the first thing you see in a recursive function. Let's start with that.

{% highlight ruby %}
def countdown(number)
  return if number < 0
  # TODO print number
  # TODO continue to next step
end
{% endhighlight %}

As in the iterative function, the first thing we do is check when to stop. If the number is less than zero, we return early. The rest of the function does not execute and we are done.

Now we've got to print our number. This is the action we take at each step, and it looks just as it did in the recursive method. 

{% highlight ruby %}
def countdown(number)
  return if number < 0
  puts number
  # TODO continue to next step
end
{% endhighlight %}

Now on to the "How do we continue?" Again, this is known as the recursive case, and it involves calling our method again inside of itself. In this case, we want to move on to the next number. Since we are counting down by one, that means we need to subtract one from the current number and pass that to our `countdown` method. Here is the final method looks like:

{% highlight ruby %}
def countdown(number)
  return if number < 0
  puts number
  countdown(number - 1)
end
{% endhighlight %}

So now `countdown` receives `number - 1`, and checks whether it is less than zero. If it is less than zero, the number is not printed and the recursion stops. If it is not less than zero, the number is printed and the recursion continues. This is what the calls to `countdown` will look like when passed the number three.

![Countdown](/assets/countdown.png)

Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur. Excepteur sint occaecat cupidatat non proident, sunt in culpa qui officia deserunt mollit anim id est laborum.

Sed ut perspiciatis unde omnis iste natus error sit voluptatem accusantium doloremque laudantium, totam rem aperiam, eaque ipsa quae ab illo inventore veritatis et quasi architecto beatae vitae dicta sunt explicabo. Nemo enim ipsam voluptatem quia voluptas sit aspernatur aut odit aut fugit, sed quia consequuntur magni dolores eos qui ratione voluptatem sequi nesciunt. Neque porro quisquam est, qui dolorem ipsum quia dolor sit amet, consectetur, adipisci velit, sed quia non numquam eius modi tempora incidunt ut labore et dolore magnam aliquam quaerat voluptatem. Ut enim ad minima veniam, quis nostrum exercitationem ullam corporis suscipit laboriosam, nisi ut aliquid ex ea commodi consequatur? Quis autem vel eum iure reprehenderit qui in ea voluptate velit esse quam nihil molestiae consequatur, vel illum qui dolorem eum fugiat quo voluptas nulla pariatur?

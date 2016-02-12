---
layout: post
title:  "Conway's Game of Life"
date:   2016-01-15 16:54:49 +0100
categories:
---
Conway's Game of Life is an interesting visual experiment starting from an initial state where certain cells live and others don't and according to the rules it will evolve over time. There is a [video tutorial][gameoflife-tutorial] with little tasks for the student on youtube. I found this a very nice tutorial about Test Driven Development using ruby and rspec.

![conways-game-of-life screenshot gif](/assets/game_of_life.gif)

<!--more-->

The tutorial uses the old syntax for rspec. While I was going along with the tutorial I wrote all the specs with the new expect syntax.

Find the code [here][gameoflife-github]. From your terminal run it with
{% highlight bash %}
  ruby gosu_game_of_life.rb
{% endhighlight %}

[gameoflife-tutorial]: https://www.youtube.com/watch?v=iLXO2FLPulI
[gameoflife-github]: https://github.com/lisbethmarianne/game_of_life

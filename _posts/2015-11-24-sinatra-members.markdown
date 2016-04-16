---
layout: post
title:  "Trying Sinatra"
image:  /assets/sinatramembers_2015-11-24.png
date:   2015-11-24 18:24:49 +0100
categories: Ruby Sinatra PostgreSQL Heroku
description: This little Sinatra App was inspired by the Webapps for Beginners book by the Ruby Monstas. At the time I was doing this, the Ruby Monstas decided to get everyone to Eurucamp, a ruby conference in Potsdam. So I made this App into a list of participant of Eurucamp 2015.
---
This little [Sinatra][sinatra] App was inspired by the [Webapps for Beginners][rubymonstas-webapps] book by the Ruby Monstas. I was the first to test this new book and I really loved it. Being able to put something out on the world wide web was and still is a really great feeling.

![sinatra members screenshot](/assets/sinatramembers_2015-11-24.png)

At the time I was doing this, the Ruby Monstas decided to get everyone to [Eurucamp][eurucamp], a ruby conference in Potsdam. So I made this App into a list of participant of Eurucamp 2015. You can add new participants, edit their names or delete them. Pretty simple.

Later I thought I should have this app so that the storage of the members is not a plain text file but a database. I went for PostgeSQL because that's the one heroku is using.

After that I also put in a simple http basic authentication. So not everyone who visits the page gets to add, edit or delete participants but only the admin can do so. Since this App is not used, feel free to play around as an admin by going to [https://sinatra-members-db.herokuapp.com/login][sinatra-members-login], the username is 'admin' and the password 'M3mb3r5'.

Visit the [App on Heroku][sinatra-members] or check out the [GitHub repo][github-sinatra].

[sinatra]: http://www.sinatrarb.com/
[rubymonstas-webapps]: http://webapps-for-beginners.rubymonstas.org/
[eurucamp]: http://2015.eurucamp.org/
[sinatra-members]: https://sinatra-members-db.herokuapp.com/members
[sinatra-members-login]: https://sinatra-members-db.herokuapp.com/login
[github-sinatra]: https://github.com/lisbethmarianne/sinatra-members-db

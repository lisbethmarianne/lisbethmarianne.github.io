---
layout: post
title:  "Diversity Tickets"
date:   2016-02-09 13:54:49 +0100
categories:
---
Together with the lovely [Ruby Monstas][rubymonstas] and [Travis Foundation][travis-foundation] I've been working on a Ruby on Rails App since July 2015. At [diversitytickets.org][diversitytickets] conferences can offer free tickets, travel grants or accommodation for their event to minority groups like women in tech.

![diversitytickets.org screenshot](/assets/diversitytickets_2016-02-09.png)

<!--more-->

The minimal version is done, the app is ready to use. Organizers can submit their events, these events have to be approved by the admin to be visible to the public. After an event is approved people can apply for tickets. After the deadline the admin will select the winners.\\
The App is hosted on Heroku. It has a PostgreSQL database. It uses Minitest for testing, mailing via Mandrill. And it has a really cool design (done by [Justine][twitter-justine]).

Concerning code, we have some fancy little things in it, for example

1) Joining all validation errors for one attribute to one line:

{% highlight ruby %}
def join_messages(messages)
  *head, tail = messages
  [head.join(", "), tail].reject { |s| s.blank? }.join(" and ")
end
{% endhighlight %}

{% highlight erb %}
<% if @application.errors.any? %>
  <div class="error">
    <p><%= pluralize(@application.errors.count, "error") %> stopped this
    application from being saved:</p>
    <ul>
      <% @application.errors.messages.each do |field, messages| %>
        <li><%= @application.class.human_attribute_name(field) %> <%=
            join_messages(messages) %></li>
      <% end %>
    </ul>
  </div>
<% end %>
{% endhighlight %}

2) A custom form builder, that will add a * to every field that is required:

{% highlight ruby %}
def form_field(field_type, attribute, name, options = {})
  css_classes = options.delete(:class) || []
  css_classes << 'form_field'
  if @object.class.validators_on(attribute).any? { |v| v.kind == :presence }
    css_classes << 'required'
  end

  @template.content_tag(:div, class: css_classes) do
    label(attribute, name) + send(field_type, attribute,
      objectify_options(options))
  end
end
{% endhighlight %}

{% highlight scss %}
div.required label:after {
  content: " *";
}
{% endhighlight %}

{% highlight erb %}
<%= f.form_field :text_field, :name, 'Name' %>
<%= f.form_field :text_field, :website, 'Website',
      placeholder: "e.g. https://myconference.com" %>
{% endhighlight %}

And many more cool things.

There is still a lot to do to improve the app, some issues are

- At the moment organizers can not edit their events once they submitted them. We already started implementing a user model so organizers can then manage their own events.
- The selection process is not implemented, also emailing to applicants once they were selected or not.
- We started doing direct s3 upload, to include the event logos.

I am really proud to be a part of this.\\
Visit the [Website][diversitytickets] or check out the [GitHub repo][diversity-gh].

[diversitytickets]: http://diversityticket.org
[diversity-gh]: https://github.com/rubymonsters/diversity_ticketing
[rubymonstas]: http://rubymonstas.org/
[travis-foundation]: http://foundation.travis-ci.org/
[twitter-justine]: https://twitter.com/SaltineJustine

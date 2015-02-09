---
layout    : post
title     : TODO
category  : tutorials
tags      : [styleguide, inherit, drop, extend, ]
summary   : TODO
description : SUMMARY
author    : eoneill
published : true
weight    : 2.1
---
{% include config %}



## Using inherit

Each set of modifiers and contexts will follow a cascading model, naturally inheriting the styles from previously matching modifiers and contexts. That is, if in our example above, if we invoke <br/> `@include styleguide(awesome example in a punchcut)`, we will get the following output:

{% highlight css %}
color:        white;
background:   yellow;
font-weight:  bold;
font-size:    20px;
{% endhighlight %}

We can take this one step further and inherit between different modifiers/contexts:

<span class="note">`[scss/themes/my_custom_theme/components/_example.scss]`</span>
{% highlight css %}
$a-blackhole: styleguide-add-component(example, (), (
  default: (
    color:        red,
    background:   yellow
  ),
  awesome: (
    font-weight:  bold
  ),
  cool: (
    inherit:      awesome
  ),
  in a punchcut: (
    color:        white,
    background:   null
  ),
  awesome in a punchcut: (
    font-size:    20px
  ),
  cool in a punchcut: (
    inherit:      awesome in a punchcut
  )
));
{% endhighlight %}

In this example, cool and awesome can now be used interchangeably.

<span class="note">NOTE: you can only inherit within the same identifier. To inherit another identifier, use the `styleguide` keyword.</span>

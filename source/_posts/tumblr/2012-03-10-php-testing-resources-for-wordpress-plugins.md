---
layout: post
title: PHP Testing Resources for Wordpress Plugins
categories:
- development
- wordpress
- php
- testing
- tdd
- bdd
- integration testing
- unit testing
- cucumber
- capybara
---
Since I've been developing a WordPress theme and plugins for the new website
at work, I've been working with PHP quite intensively for the last couple of
months. For a lot of reasons, PHP isn't my favourite language to work in, and
the lack of testing culture amongst PHP programmers is really underlined by
WordPress theme and plugin developers not shipping their code with tests,
which could also be a reflection of the WordPress core having lots of tests,
but having them [available only when you clone the Subversion
repository](http://codex.wordpress.org/Automated_Testing).

I've also been thinking about how projects like [CASH Music
DIY](https://github.com/cashmusic/DIY) could really benefit from a combination
of test-driven development (TDD) for the developers themselves and behaviour-
driven development (BDD) to allow non-experts to write tests that can double
as documentation using [Cucumber](http://cukes.info/). In fact, I started this
whole search by looking for tips on how to use Cucumber and
[Capybara](http://jnicklas.github.com/capybara/) to do integration testing on
PHP projects.

Cucumber allows you to write natural-language feature tests, such as the
following example taken from their Github repository:

{% highlight python %}
Feature: Addition
  In order to avoid silly mistakes
  As a math idiot 
  I want to be told the sum of two numbers

  Scenario Outline: Add two numbers
    Given I have entered  into the calculator
    And I have entered  into the calculator
    When I press 
    Then the result should be  on the screen

  Examples:
    | input_1 | input_2 | button | output |
    | 20      | 30      | add    | 50     |
    | 2       | 5       | add    | 7      |
    | 0       | 40      | add    | 40     |
{% endhighlight %}

On the unit testing and TDD front, Smashing Magazine has a brand new [article
on writing unit tests for WP
plugins](http://coding.smashingmagazine.com/2012/03/07/writing-unit-tests-for-
wordpress-plugins/) that uses the JavaScript
[QUnit](http://docs.jquery.com/QUnit). There is a simple [Lastcraft Unit
Testing Tutorial](http://www.lastcraft.com/first_test_tutorial.php) using
[SimpleTest](http://www.simpletest.org/).

Where BDD is concerned, Otaqui.com has a Gist for using [Cucumber, Capybara,
Mechanize and Selenium to test remote PHP web
sites](http://otaqui.com/blog/1072/testing-remote-php-websites-with-capybara-
cucumber-mechanize-selenium-2-webdriver-and-saucelabs/).

Since I'm just starting out with this, I'd love to hear from some PHP testing
experts and anyone else who can help me fill in the gaps.

More resources I've found since posting this:

  * Eric Hogue's [post on TDD in PHP using SimpleTest and PHPUnit](http://erichogue.ca/2011/06/php/test-driven-development-in-php/).
  * There's [a PHP port of RSpec called PHPSpec](http://techportal.ibuildings.com/2011/08/03/outside-in-behaviour-driven-development-in-php-part-2/), which is a really cool idea for doing outside-in BDD with PHP. It's not as pretty as Ruby because PHP isn't syntactically sweet enough to eliminate all the sigils that are optional in Ruby and the Domain-Specific Languages (DSL's) derived from it, plus other stuff*.
  * Sebastian Bergmann and Stefan Priebsch have written [a book called _Real-World Solutions for Developing High-Quality PHP Frameworks and Applications_](http://qualityassuranceinphpprojects.com/) whose content is hopefully easier to digest than the English title. Their original German title is _Softwarequalität in PHP-Projekten_ 'Software quality in PHP projects", and much _leichter zu verdauen_.

* Camel case for everything, really?

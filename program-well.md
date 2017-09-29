Best Practices
==============

A guide for programming well.

General
-------

* These are not to be blindly followed; strive to understand these and ask
  when in doubt.
* Don't duplicate the functionality of a built-in library.
* Don't swallow exceptions or "fail silently."
* Don't write code that guesses at future functionality.
* Exceptions should be exceptional.
* Keep the code simple.

Object-Oriented Design
----------------------

* Avoid global variables.
* Avoid long parameter lists.
* Limit collaborators of an object (entities an object depends on).
* Limit an object's dependencies (entities that depend on an object).
* Prefer composition over inheritance.
* Prefer small methods. Between one and five lines is best.
* Prefer small classes with a single, well-defined responsibility. When a
  class exceeds 100 lines, it may be doing too many things.
* [Tell, don't ask].

[Tell, don't ask]: https://robots.thoughtbot.com/tell-dont-ask

Relational Databases
--------------------

* [Index foreign keys].
* Constrain most columns as [`NOT NULL`].
* In a SQL view, only select columns you need (i.e., avoid `SELECT table.*`).
* Use an `ORDER BY` clause on queries where the results will be displayed to a
  user, as queries without one may return results in a changing, arbitrary
  order.

[Index foreign keys]: https://tomafro.net/2009/08/using-indexes-in-rails-index-your-associations
[`NOT NULL`]: http://www.postgresql.org/docs/9.1/static/ddl-constraints.html#AEN2444

Email
-----

* Use [Mandrill] or [SendGrid] to deliver email in staging and production
  environments.

[Mandrill]: hhttps://www.mandrill.com/
[SendGrid]: https://sendgrid.com/

Web
---

* Avoid a Flash of Unstyled Text, even when no cache is available.
* Avoid rendering delays caused by synchronous loading.
* Use https instead of http when linking to assets.

JavaScript
----------

* Prefer `data-*` attributes over `id` and `class` attributes when targeting
  HTML elements. 
* Avoid targeting HTML elements using classes intended for styling
  purposes. 

HTML
----

* Use `<button>` tags over `<a>` tags for actions.

CSS
---

* Document the project's CSS architecture (the README, component library or
  style guide are good places to do this), including things such as:
  * Organization of stylesheet directories and Sass partials
  * Selector naming convention
  * Code linting tools and configuration
  * Browser support
* Use Sass.
* Use [Autoprefixer][autoprefixer] to generate vendor prefixes based on the
  project-specific browser support that is needed.
* Prefer `overflow: auto` to `overflow: scroll`, because `scroll` will always
  display scrollbars outside of macOS, even when content fits in the container.

[autoprefixer]: https://github.com/postcss/autoprefixer

Browsers
--------

* Avoid supporting versions of Internet Explorer before IE11.

[HTTP API Design Guide]: https://github.com/interagent/http-api-design
[oj]: https://github.com/ohler55/oj

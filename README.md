# My Ruby, Rails and Rspec style guide.

With rubocop rules for enforce this.

## Ruby

* Ruby version. Use ruby >= x.x.2. Usually, release version ruby contains bugs, so omit x.x.0 versions. And x.x.1 versions too. Use 2.2.4 ruby for production now.

* Lock ruby version for ruby application in ```.ruby-version``` and ```Gemfile```.

.ruby-version:
```ruby
2.2.4
```

Gemfile:
```ruby
ruby '2.2.4'
```

* Use ```UTF-8``` as the source file encoding. Always.

* Omit "magic" comment ```# encoding: utf-8```. Current ruby always think that encoding is ```UTF-8```.

* Use two spaces for indent code.
```yaml
Style/IndentationConsistency:
  EnforcedStyle: normal
```

* Don't use tabs.
```yaml
Style/Tab:
  Enabled: true
```

## Rails

* Use erb. Don't use haml, slim or similar template engines. They are don't solve the problems and make understading harder.

## PostgreSQL

* Use x.x.1 >= versions. Usually, release versions contains bugs. Use 9.4.5 version now.
* Don't use triggers.
* Don't use SQL Views.

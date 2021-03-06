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

## Testing

* Test behavior not implementation.

```ruby
class Sum
  def perform(a, b)
    a + b
  end
end

# bad
describe Sum do
  describe '#sum' do
    specify { expect(subject.sum(1, 2)).to eq(3)  }
  end
end

# good
describe Sum do
  describe '#sum' do
    let(:a) { double }

    let(:b) { double }

    before { expect(subject).to recive(:sum).with(a, b) }

    before { expect(a).to receive(:+).with(b) }

    it { expect { subject.sum(a, b) }.not_to raise_error }
  end
end
```

## Useful ruby gems:

* kaminari. Use it for pagination.
* swagger-blocks. For Swagger 2.0 Specification.
* bullet. Excellent tool for catching N+1 problems.
* rubocop. For catching problems which can be catched automatically.
* redis-objects. For any interaction with redis.
* draper. Just decorators.
* rspec and rspec-rails. For testing.
* rspec-its. Don't Repeat Yourself.
* rspec-activemodel-mocks. For stubbing ActiveRecord models.
* shoulda-matchers. For simple one-liners specs.
* shoulda-callback-matchers. For spec'ing callbacks in Models.
* fakeredis. For running specs without real local redis server.
* simplecov. For test coverage reports.
* pry-rails. For good rails console and simple debug when needed.
* awesome_print. For easy debug in rails console.
* brakeman. For catching typical security problems.
* bundler-audit. For catching known security problems in used gems (usually, they are have assigned CVE numbers).
* exception_notification. For catching exception notifications.
* lograge. For squashing rails logs.
* whenever. For cron jobs.
* capistrano. Use it for deploy.
* sidekiq. For delayed jobs. Use it with ActiveJob from Rails >= 4.2. 

## Don't use this gems:

* will_paginate. Use kaminari instead.
* ActiveAdmin. If you need admin panel with simple CRUD, it will work. If you will need to customize, it will turn your life in hell.
* swagger-docs. Mostly unsupported and use outdated Swagger 1.2 Specification. Use swagger-blocks.
* paperclip. Hard to customize behavior for non-trivial situations.
* factory_girl. Just use rspec-activemodel-mocks instead.
* faker. You don't need this without factory_girl.
* database_cleaner. You don't need this without factory_girl.
* fakeweb. Unsupported.
* cancan. Unsupported.

## PostgreSQL

* Use x.x.1 >= versions. Usually, release versions contains bugs. Use 9.4.5 version now.
* Don't use triggers.
* Don't use SQL Views.

## Deploy

* Use capistrano.

## Services

* Use NewRelic RPM. newrelic_rpm gem.

## Questions?

* Q: What about CoffeeScript vs JavaScript?
* A: I am backend developer and don't use both.

* Q: What about CSS/SASS/SCSS?
* A: I am backend developer and don't use any of thus.

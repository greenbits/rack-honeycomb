# Honeycomb middleware for Rack applications

This is Rack middleware that sends request/response data to [Honeycomb](https://honeycomb.io).  You can use `Rack::Honeycomb` with any Ruby web framework based on Rack, including Ruby on Rails and Sinatra.

For more information about using Honeycomb, check out our [docs](https://honeycomb.io/docs) and our [Ruby SDK](https://honeycomb.io/docs/connect/ruby/).

## Adding instrumentation to a Rails application

```ruby
# config/application.rb
require 'rack/honeycomb'

class Application < Rails::Application
  config.middleware.use Rack::Honeycomb::Middleware, writekey: "<YOUR WRITEKEY HERE>", dataset: "<YOUR DATASET NAME HERE>"
end
```

## Adding instrumentation to a Sinatra application

```ruby
#!/usr/bin/env ruby -rubygems
require 'sinatra'
require 'rack/honeycomb'

use Rack::Honeycomb::Middleware, writekey: "<YOUR WRITEKEY HERE>", dataset: "<YOUR DATASET NAME HERE>"

get('/hello') { "Hello, world!\n" }
```

## Installation

To install the latest stable release of `rack-honeycomb`, simply:

```bash
$ gem install rack-honeycomb
```

or add this to your Gemfile

```
gem "rack-honeycomb"
```

To follow the bleeding edge, it's easy to track the git repo:

```
gem "rack-honeycomb", :git => "https://github.com/honeycombio/rack-honeycomb.git"
```

## Contributions

Features, bug fixes and other changes are gladly accepted. Please
open issues or a pull request with your change. Remember to add your name to the
CONTRIBUTORS file!

All contributions will be released under the Apache License 2.0.

### Releasing a new version

Travis will automatically upload tagged releases to Rubygems. To release a new
version, run
```
bump patch --tag   # Or bump minor --tag, etc.
git push --follow-tags
```

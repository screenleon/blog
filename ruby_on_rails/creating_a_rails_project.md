# Creating a Rails Project
==========================

**Author:** Lien Chen **Date:** 2024-10-03

## Resolving Issues with `rails new`

When creating a new Rails project using `rails new myapp` with Ruby 3.0.2p107 and Rails 6.1.4.1, you may encounter an error. This is often due to missing dependencies.

### Installing Yarn

First, ensure you have Yarn installed globally by running:

```bash
npm install -g yarn
```

---
### Updating Gemfile
Next, update your Gemfile to include the required dependencies:

```ruby
gem 'puma', '~> 5.6'
gem 'rack', '~> 2.2'
```

If `rack` is not already present in your Gemfile, add it.

---
### Updating Gemfile
Then, update your Bundler configuration and dependencies by running:

```bash
bundle config set --local path 'vendor/bundle'
bundle update selenium-webdriver
bundle update puma
bundle update rack
```

---
### Starting the Server
Finally, start your web server using:

```bash
rails server
```
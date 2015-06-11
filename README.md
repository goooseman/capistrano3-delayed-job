# capistrano3-delayed-job

This Capistrano (v3) task ask for the delayed_job gem management. To use it be sure that you have

```
gem "daemons"
gem "delayed_job" or gem "delayed_job_active_record" or any other
```

You can use

```
delayed_job:start
delayed_job:stop
delayed_job:restart
```

after [installation](#installation).

**Rails 3 users** - make sure you `set :delayed_job_folder, 'scripts'` in your `config/deploy.rb`.

Rails 4 users - no need to worry, it uses `'bin'` by default.

You can `set :delayed_job_args, ''` and `set :delayed_job_server_role` in your `config/deploy.rb`

You can use it like this in your `deploy.rb`:

``` ruby
after 'deploy:publishing', 'deploy:restart'
namespace :deploy do
  task :restart do
    invoke 'delayed_job:restart'
  end
end
```

## Installation

Add this line to your application's Gemfile:

```ruby
group :development do
  gem 'capistrano3-delayed-job'
end
```

Install with bundler:

    $ bundle

And then add `require 'capistrano3/delayed-job'` to your `Capfile`.

## My other works

Take a look at my [capistrano3-ubuntu-server-prepare](https://github.com/goooseman/capistrano3-ubuntu-server-prepare) (it can install Nginx, PostgreSQL, Redis, RVM, Rails, Bundler, Imagemagick and do some other helpfull things to prepare your blank Ubuntu server for the first deploy) and [capistrano3-git-push](https://github.com/goooseman/capistrano3-git-push) (automated git add, commit, push before each deploy) Capistrano (v3) gems.

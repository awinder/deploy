# Octopress Deploy

Deployment tools for Octopress and Jekyll blogs (or really any static site).

Currently this supports deploying through Git and Rsync. Requests for other
deployment methods are welcome.

## Installation

Add this line to your application's Gemfile:

    gem 'octopress-deploy'

And then execute:

    $ bundle

Or install it yourself as:

    $ gem install octopress-deploy

## Set up

To deploy your site run:

```ruby
Octopress::Deploy.push()
```

This will read from your configuration file `_deploy.yml` and deploy your site. If your site has no configuration file, you will be asked if you want to generate one and what deployment method you want to use.

You can also generate a configuration by running:

```ruby
Octopress::Deploy.init_cofig('git') # or 'rsync'
```

This will generate a '_deploy.yml' file in your current directory.

### Configuration options

Configurations should be added to a `_deploy.yml` file in your project's root directory. You can pass options as a hash directy to the `push` method as well. Passed options will override options set in the config file.

| option        | Description                                      | Default
|:--------------|:-------------------------------------------------|:---------------|
| `config_file` | Path to the config file.                         | _config.yml    |
| `site_dir`    | Path to comipled site files.                     | _site          |


### Git options

Only `git_url` is required. Other options will default as shown below.

| option        | Description                                      | Default
|:--------------|:-------------------------------------------------|:---------------|
| `git_url`     | Url for remote git repository.                   |                |
| `git_branch`  | Deployment branch for git repository.            | master         |
| `deploy_dir`  | Directory where deployment files are staged.     | .deploy        |
| `remote`      | Name of git remote.                              | deploy         |

### Rsync options

Only `remote_path` is required. If `user` is not present, Rsync will sync between two locally available directories. Do this if your site root is mounted locally.

| option         | Description                                       | Default
|:---------------|:--------------------------------------------------|:---------------|
| `user`         | ssh user, e.g user@host.com                       |                |
| `port`         | ssh port                                          | 22             |
| `remote_path`  | Remote destination's document root.               |                |
| `exclude_file` | Path to a file containing rsync exclusions.       |                |
| `exclude`      | Inline list of rsync exclusions.                  |                |
| `include`      | Inline list of inclusions to override exclusions. |                |
| `delete`       | Delete files in destination not found in source   | false          |

## Contributing

1. Fork it
2. Create your feature branch (`git checkout -b my-new-feature`)
3. Commit your changes (`git commit -am 'Add some feature'`)
4. Push to the branch (`git push origin my-new-feature`)
5. Create new Pull Request

## License

Copyright (c) 2014 Brandon Mathis

MIT License

Permission is hereby granted, free of charge, to any person obtaining
a copy of this software and associated documentation files (the
"Software"), to deal in the Software without restriction, including
without limitation the rights to use, copy, modify, merge, publish,
distribute, sublicense, and/or sell copies of the Software, and to
permit persons to whom the Software is furnished to do so, subject to
the following conditions:

The above copyright notice and this permission notice shall be
included in all copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND,
EXPRESS OR IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF
MERCHANTABILITY, FITNESS FOR A PARTICULAR PURPOSE AND
NONINFRINGEMENT. IN NO EVENT SHALL THE AUTHORS OR COPYRIGHT HOLDERS BE
LIABLE FOR ANY CLAIM, DAMAGES OR OTHER LIABILITY, WHETHER IN AN ACTION
OF CONTRACT, TORT OR OTHERWISE, ARISING FROM, OUT OF OR IN CONNECTION
WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE SOFTWARE.
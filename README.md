# Laptop

Laptop is a script to set up an OS X laptop for web development at Dreipol.
This is inspired by [thoughtbot/laptop](https://github.com/thoughtbot/laptop).

It can be run multiple times on the same machine safely.
It installs, upgrades, or skips packages
based on what is already installed on the machine.

Requirements
------------

You need to install Xcode Command Line Tools first.

```
xcode-select --install
```

# Install

Download, review, then execute the script:

```
curl --remote-name https://raw.githubusercontent.com/dreipol/laptop/master/mac
sh mac 2>&1 | tee ~/laptop.log
```

# Debugging

Your last Laptop run will be saved to `~/laptop.log`. Read through it to see if
you can debug the issue yourself. If not, copy the lines where the script
failed into a [new GitHub
Issue](https://github.com/dreipol/laptop/issues/new) for us. Or, attach the
whole log file as an attachment.

What it sets up
---------------

* [Bundler] for managing Ruby libraries
* [Homebrew] for managing operating system libraries
* [ImageMagick] for cropping and resizing images
* [Node.js] and [NPM], for running apps and installing JavaScript packages
* [Postgres] for storing relational data
* [Python] for the win (2.7 and 3.4)
* [virtualenv] and [virtualenvwrapper] for managing different python versions 
* [Zsh] as your shell
* [Virtualbox] for running virtual machines 
* [Vagrant] for creating dev environments
* [Docker] and [boot2docker] because it is 2015 
* Utils like [tree] and [watch]

[Bundler]: http://bundler.io/
[Homebrew]: http://brew.sh/
[ImageMagick]: http://www.imagemagick.org/
[Node.js]: http://nodejs.org/
[NPM]: https://www.npmjs.org/
[Postgres]: http://www.postgresql.org/
[Python]: https://www.python.org/ 
[Zsh]: http://www.zsh.org/
[virtualenvwrapper]: https://pypi.python.org/pypi/virtualenvwrapper
[virtualenv]: https://pypi.python.org/pypi/virtualenv 
[Virtualbox]: https://www.virtualbox.org/
[Vagrant]: https://www.vagrantup.com/
[Docker]: https://www.docker.com/
[boot2docker]: http://boot2docker.io/
[tree]: https://en.wikipedia.org/wiki/Tree_%28Unix%29
[watch]: https://en.wikipedia.org/wiki/Watch_%28Unix%29

# Customize in `~/.laptop.local`

Your `~/.laptop.local` is run at the end of the Laptop script.
Put your customizations there.
For example:

```sh
#!/bin/sh

brew_cask_install_or_upgrade 'dropbox'
brew_cask_install_or_upgrade 'google-chrom'
brew_cask_install_or_upgrade 'rdio'

gem_install_or_update 'parity'

brew_install_or_upgrade 'tree'
brew_install_or_upgrade 'watch'
```

Write your customizations such that they can be run safely more than once.
See the `mac` script for examples.

Laptop functions such as `fancy_echo`,
`brew_install_or_upgrade`, and
`gem_install_or_update`
can be used in your `~/.laptop.local`.

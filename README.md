MIT Libraries Development Python Box
===
This repository contains a VagrantFile and support scripts that will configure
a local VM suitable for developing Python applications.

What it installs
==
- apt packages necessary for typical python development
- the current python version, pip, and pipenv
- the heroku command line interface tool

How to use it
==
On your local computer
- Install vagrant
- Clone this repo locally
- `vagrant up` in the cloned directory of this repo
  - NOTE: if you don't like the default of `src`, you can use `SYNCED_FOLDER` ENV
  - EXAMPLE: `SYNCED_FOLDER="~/projects" vagrant up`
- git clone the repo you want to work on into `src`
  - NOTE: if you changed with `ENV['SYNCED_FOLDER']` wherever you change it to
  - NOTE: you can sync a directory containing multiple projects instead of having a VM for each.
- `vagrant ssh` gets you a shell on the python vm
- Note: do all your development using your preferred tools on your local
computer. Do your `git` work on your local as well.
- `vagrant halt` when you want to shutdown the vm (`vagrant up` to bring it
   back)

On the python VM
- `cd /vagrant/src/YOUR_PROJECT` gets you to the linked directory
- `pip install` whenever you need to install packages
- `py.test` to run tests
- `heroku local` to run a dev server.

Caveats
==
This does not use Ansible due to a requirement to work on Windows.

Making Changes
==
If you end up needing additional packages installed to get python packages to work,
adding them to the `provision.sh` will probably make it easier later if it's a
fairly common package.

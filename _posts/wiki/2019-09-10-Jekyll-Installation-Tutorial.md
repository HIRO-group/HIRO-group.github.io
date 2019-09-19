---
title: Jekyll Installation Tutorial
description: Using Jekyll to help create and edit existing pages for the HIRO Group website
tags: [wiki,how to,tutorial,ubuntu,16.04,jekyll,ruby]
permalink: jekyll_installation_tutorial.html
author: Garrett Pierson
---

# Contents
{:.no_toc}

* This line will be replaced by the ToC, excluding the "Contents" header
{:toc}

This guide is intended to help set up members set up Jekyll so that they can easily
add, update, and change pages on the HIRO Group website.

# What is Jekyll?

Jekyll is a static site generator which helps to organize the website data for
the HIRO Group and generate the website. By installing Jekyll you will be able
to host the website locally to see how your article or added page looks before
pushing changes to the HIRO Group repository.

# Steps For Installing Jekyll

 1. Check Ruby Version: Ruby version must be updated to 2.4.0 or above if not see Installing RVM & Updating Ruby below. Use: `ruby -v`
 2. Check to see if you have Ruby Gems: `gems -v`
 3. Install Dependencies: `sudo apt-get install ruby-full build-essential zlib1g-dev`
 4. Configure Installation Path for Gems. The following will add the appropriate paths to the `.bashrc` file:
    ~~~bash
    echo '# Install Ruby Gems to ~/gems' >> ~/.bashrc
    echo 'export GEM_HOME="$HOME/gems"' >> ~/.bashrc
    echo 'export PATH="$HOME/gems/bin:$PATH"' >> ~/.bashrc
    source ~/.bashrc
    ~~~
 5. Install Jekyll:`gem install jekyll bundler`

# Installing RVM & Updating Ruby

Ruby version manager (RVM) allows for users to work on legacy code using older
versions of ruby by enabling easy switching between versions. This allows us to
update our ruby version more easily. Please skip this section if you already have
the appropriate Ruby version installed.

1. Download RVM
 * Run the following in your bash terminal:
    ~~~bash
    curl -sSL http://get.rvm.io | sudo bash -s stable -- --ignore-dotfiles
    ~~~
 * Check if the user group rvm has been added:
    ~~~bash
    groups
    getent group rvm
    ~~~
 * Add yourself to the rvm group:
    ~~~bash
    sudo usermod -a -G rvm <your username here>
    ~~~
 * In your terminal enter `getent group rvm` and you should see: `rvm:x :###:<your username here>`
 * Log out then log in to activate changes.
2. Source your terminal to access the newer versions of Ruby:
 * Add the following to your `.bashrc` file: `source /etc/profile.d/rvm.sh`
3. Update Ruby:
 * See what ruby versions are available: `rvm list known`
 * Select any version 2.4.0 or above (install a fairly new version)
 * This command takes care of dependencies:
  ~~~bash
  sudo apt install libyaml-devel readline-devel libffi-devel sqlite-devel
  ~~~
 * Finally install updated Ruby version
 ~~~bash
 rvm install ruby-<version number here ex: 2.6.3 >
 ~~~
 * Check Ruby version: `ruby -v`
 * Finished!

# Next Steps

1. Locally host the website:
 * This command compiles the files (only do this the first time you host): `bundle exec jekyll serve`
 * This command starts the local server hosting the website:`jekyll serve`

2. Learn about markdown: Markdown is the markup language used to format the pages you see on the HIRO Group website. Check out some of the markdown files on the repository for some examples.
3. Live your life and create new pages.

# Reference Sites
* [Jekyll Install Guide](https://jekyllrb.com/docs/installation/)
* [Updating Ruby & Installing RVM](https://blog.hqcodeshop.fi/archives/279-Installing-multi-user-Ruby-with-RVM.html)

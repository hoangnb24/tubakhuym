---
title: "Local Development Guide"
date: 2024-11-26
categories:
  - Guide
tags:
  - setup
  - development
---

## Prerequisites

1. **Install Homebrew** (if not already installed)
   ```bash
   /bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
   ```

2. **Install Ruby via Homebrew**
   ```bash
   brew install ruby
   ```

3. **Add Ruby to your PATH**
   Add this to your `~/.zshrc` (for Zsh) or `~/.bash_profile` (for Bash):
   ```bash
   export PATH="/opt/homebrew/opt/ruby/bin:$PATH"
   ```
   Then reload your shell configuration:
   ```bash
   source ~/.zshrc  # or source ~/.bash_profile for Bash
   ```

4. **Verify Ruby Installation**
   ```bash
   which ruby  # Should point to Homebrew's Ruby, not system Ruby
   ruby -v    # Should show Ruby version 3.x.x
   ```

## Setting up the Blog

1. **Clone this repository**
   ```bash
   git clone [repository-url]
   cd [repository-name]
   ```

2. **Install Bundler and Dependencies**
   ```bash
   gem install bundler
   bundle install
   ```

3. **Start the Jekyll Server**
   ```bash
   bundle exec jekyll serve
   ```

4. Open http://localhost:4000 in your browser

## Troubleshooting

- If you see permission errors, make sure you're using Homebrew's Ruby and not the system Ruby
- If bundler fails, try removing `Gemfile.lock` and running `bundle install` again
- For any gem-related issues, try `gem pristine --all` 
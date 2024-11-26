---
title: "Local Development Guide"
date: 2024-11-26
categories:
  - blog
tags:
  - setup
  - development
  - guide
toc: true
toc_sticky: true
---

# Local Development Guide

This guide will help you set up your local development environment for contributing to this blog.

## Prerequisites

Before you begin, ensure you have the following tools installed on your macOS system:

### 1. Install Homebrew

If you haven't installed Homebrew yet, run the following command:

```bash
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
```

### 2. Install Ruby

Install Ruby using Homebrew:

```bash
brew install ruby
```

### 3. Configure Ruby Path

Add Ruby to your PATH by adding these lines to your shell configuration file:

For Zsh (`~/.zshrc`):
```bash
export PATH="/opt/homebrew/opt/ruby/bin:$PATH"
```

Then reload your configuration:
```bash
source ~/.zshrc
```

### 4. Verify Installation

Ensure Ruby is properly installed:
```bash
which ruby  # Should point to Homebrew's Ruby
ruby -v    # Should show Ruby version 3.x.x
```

## Blog Setup

Follow these steps to set up the blog locally:

### 1. Clone Repository

```bash
git clone [repository-url]
cd [repository-name]
```

### 2. Install Dependencies

Install Bundler and project dependencies:

```bash
gem install bundler
bundle install
```

### 3. Start Development Server

Launch the Jekyll development server:

```bash
bundle exec jekyll serve
```

The blog will be available at [http://localhost:4000](http://localhost:4000)

## Troubleshooting Guide

If you encounter any issues during setup, try these solutions:

### Common Issues

1. **Permission Errors**
   - Verify you're using Homebrew's Ruby instead of the system Ruby
   - Check Ruby path with `which ruby`

2. **Bundler Failures**
   - Remove `Gemfile.lock`: `rm Gemfile.lock`
   - Reinstall dependencies: `bundle install`

3. **Gem Issues**
   - Reset all gems: `gem pristine --all` 
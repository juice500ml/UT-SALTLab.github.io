# The SALT Lab Website

This is the website of The SALT Lab at UT Austin, based on the [Allan Lab website template](https://github.com/mpa139/allanlab). Code released under the MIT License.

This website is powered by Jekyll and Bootstrap. It is configured for GitHub Pages deployment with GitHub Actions CI.

## Setup

### Prerequisites
- Ruby (version 3.1 or compatible)

### Manual Setup
To avoid permission issues, install Bundler to your user directory:
```bash
gem install bundler
# or, if you don't have permissions,
gem install --user-install bundler
export PATH="$HOME/.local/share/gem/ruby/3.0.0/bin:$PATH"
# Or for other Ruby versions, find the path with: gem env | grep "USER INSTALLATION DIRECTORY"
```

### Install Dependencies

Install gems locally to the project (no root required):
```bash
bundle config set --local path 'vendor/bundle' # if you don't have permission
bundle install
```

## Local Development

### Build the Site Locally

To build the site locally before pushing to GitHub:

```bash
bundle exec jekyll build
```

### Preview Locally

To preview the site with live reload:

```bash
bundle exec jekyll serve
```

Then open [http://localhost:4000](http://localhost:4000) in your browser.

### Deploy
To update the homepage, you need to:
1. Make a fork of this repo
2. In your repo, create a new branch
3. Make updates there
4. Make a pull request to `main`

### CI Workflow

The GitHub Actions workflow (`.github/workflows/jekyll.yml`) will:
- Build the Jekyll site on every `main` branch commit
- Deploy to GitHub Pages automatically
- `CNAME` is set in [UT DNS settings](https://ut.service-now.com/sp?id=kb_article&number=KB0011361), such that `saltlab.cs.utexas.edu/` automatically directs to `UT-SALTLab.github.io`.

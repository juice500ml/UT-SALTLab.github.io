# The SALT Lab Website

This is the website of The SALT Lab at UT Austin.

This website is powered by Jekyll and Bootstrap. It is configured for GitHub Pages deployment with GitHub Actions CI/CD.

## Setup

### Prerequisites
- Ruby (version 3.1 or compatible)

### Manual Setup
To avoid permission issues, install Bundler to your user directory:
```bash
gem install --user-install bundler
```

Then add the local gem bin directory to your PATH. Add this to your `~/.bashrc` or `~/.zshrc`:
```bash
export PATH="$HOME/.local/share/gem/ruby/3.0.0/bin:$PATH"
# Or for other Ruby versions, find the path with: gem env | grep "USER INSTALLATION DIRECTORY"
```

After adding to PATH, reload your shell:
```bash
source ~/.bashrc  # or source ~/.zshrc
```

**Alternative**: If you have rbenv or rvm installed, they handle this automatically.

### Install Dependencies

Install gems locally to the project (no root required):
```bash
bundle config set --local path 'vendor/bundle'
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

## GitHub Pages Deployment

This repository is configured for automatic deployment to GitHub Pages using GitHub Actions.

### Setup GitHub Pages

1. Push this repository to GitHub (e.g., `UT-SALTLab/UT-SALTLab.github.io`)
2. Go to Settings → Pages in your GitHub repository
3. Under "Source", select "GitHub Actions" (not "Deploy from a branch")
4. The site will automatically build and deploy on every push to the `main` branch

### CI/CD Workflow

The GitHub Actions workflow (`.github/workflows/jekyll.yml`) will:
- Build the Jekyll site on every push and pull request
- Deploy to GitHub Pages automatically
- Use the `github-pages` gem for compatibility

### Custom Domain

If you're using a custom domain (configured via `CNAME` file), make sure the `url` in `_config.yml` matches your domain.

## Notes

- The site uses the `github-pages` gem which includes Jekyll and all dependencies
- **Custom plugins**: The custom plugin in `_plugins/markdown.rb` may not work on GitHub Pages, as GitHub Pages only allows [whitelisted plugins](https://pages.github.com/versions/). If you use the `{% markdown %}` tag, you may need to refactor it or use a different approach for GitHub Pages.
- The `_site` directory is generated and should not be committed to git (it's in `.gitignore`)
- If your default branch is `master` instead of `main`, update `.github/workflows/jekyll.yml` accordingly

## Troubleshooting

If you encounter issues:

1. **Permission errors installing gems**: Use `gem install --user-install` instead of `gem install` to install to your user directory
2. **Bundler not found**: Make sure the local gem bin directory is in your PATH (see Setup section)
3. **Build fails locally**: Make sure you have the correct Ruby version and run `bundle install`
4. **GitHub Actions fails**: Check the Actions tab in GitHub for error details
5. **Site not updating**: Ensure GitHub Pages is set to use "GitHub Actions" as the source, not a branch

---

Based on the [Allan Lab website template](https://github.com/mpa139/allanlab). Code released under the MIT License.


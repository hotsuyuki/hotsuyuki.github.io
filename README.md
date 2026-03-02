# hotsuyuki.github.io

Hotsuyuki Kawanishi blog

## How to create a GitHub Pages site with Jekyll 

```shell
cd /path/to/hotsuyuki.github.io

# Uses a Ruby pre-compiled binary with a specific version.
# https://mise.jdx.dev/lang/ruby.html#precompiled-binaries
mise settings ruby.compile=false
mise use ruby@3.4.1

# Checks it uses the version manager Ruby (instead of the system Ruby).
which ruby && ruby --version
which bundle && bundle --version

# Creates an empty Gemfile.
# https://jekyllrb.com/tutorials/using-jekyll-with-bundler/#initialize-bundler
bundle init

# Configures Bundler to install gems in the `./vendor/bundle/` project subdirectory.
# https://jekyllrb.com/tutorials/using-jekyll-with-bundler/#configure-bundler-install-path
bundle config set --local path 'vendor/bundle'

# Installs Jekyll gem.
# https://jekyllrb.com/tutorials/using-jekyll-with-bundler/#add-jekyll
bundle add jekyll

# Creates a new Gemfile and a new Jekyll site.
# https://jekyllrb.com/tutorials/using-jekyll-with-bundler/#create-a-jekyll-scaffold
bundle exec jekyll new --force --skip-bundle .

# Comments out `gem "jekyll"` and adds `gem "github-pages"` in the new Gemfile.
# https://docs.github.com/en/pages/setting-up-a-github-pages-site-with-jekyll/creating-a-github-pages-site-with-jekyll#creating-your-site
sed -i '' 's/gem "jekyll"/# gem "jekyll"/g' ./Gemfile
echo 'gem "github-pages", "~> 232", group: :jekyll_plugins' >> ./Gemfile

# Adds `gem "webrick"` in the new Gemfile for `jekyll serve` command.
# https://docs.github.com/en/pages/setting-up-a-github-pages-site-with-jekyll/testing-your-github-pages-site-locally-with-jekyll#building-your-site-locally
echo 'gem "webrick"' >> ./Gemfile

# Installs the gems in the new Gemfile.
bundle install

# Runs the Jekyll site locally.
bundle exec jekyll serve
```

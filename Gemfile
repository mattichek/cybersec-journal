source "https://rubygems.org"

# Używamy gema github-pages, żeby lokalnie mieć dokładnie to samo
# środowisko, co buduje GitHub Pages (te same wersje Jekylla i wtyczek).
gem "github-pages", group: :jekyll_plugins

# Wtyczki używane przez stronę
group :jekyll_plugins do
  gem "jekyll-feed"
  gem "jekyll-seo-tag"
end

# Windows / WSL — zwykle potrzebne:
gem "tzinfo-data", platforms: [:mingw, :x64_mingw, :mswin, :jruby]
gem "wdm", "~> 0.1.1", platforms: [:mingw, :x64_mingw, :mswin]

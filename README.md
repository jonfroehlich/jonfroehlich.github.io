# Jon Froehlich's Academic Website
I made this in Jekyll using the [Minimal Mistakes](https://github.com/mmistakes/minimal-mistakes) theme.

# Minimal Mistakes
Some useful links
- The [Minimal Mistakes](https://github.com/mmistakes/minimal-mistakes) theme
- The [academic fork of Minimal Mistakes](https://github.com/academicpages/academicpages.github.io), which I did not use
- [Minimal Mistakes GitHub Pages starter](https://github.com/mmistakes/mm-github-pages-starter), which I perused and played with but did not comprehensively use.

## Running the website

Assuming you have the prerequisite libraries and software infrastructure (e.g., Jekyll), you can open terminal in VSCode and type:

```
> bundle exec jekyll serve 
```

Which should result in the server starting at http://localhost:4000. See:
```
PS C:\Git\academicwebsite> bundle exec jekyll serve                        
Configuration file: C:/Git/academicwebsite/_config.yml
            Source: C:/Git/academicwebsite
       Destination: C:/Git/academicwebsite/_site       
 Incremental build: disabled. Enable with --incremental
      Generating...
      Remote Theme: Using theme mmistakes/minimal-mistakes
       Jekyll Feed: Generating feed for posts
   GitHub Metadata: No GitHub API authentication could be found. Some fields may be missing or have incorrect data.
                    done in 17.169 seconds.
 Auto-regeneration: enabled for 'C:/Git/academicwebsite'
    Server address: http://127.0.0.1:4000
  Server running... press ctrl-c to stop.
      Regenerating: 1 file(s) changed at 2020-12-10 06:16:51
                    README.md
      Remote Theme: Using theme mmistakes/minimal-mistakes
       Jekyll Feed: Generating feed for posts
                    ...done in 3.4005941 seconds.
```

# Jekyll Installation 

## Mac Installation

According to the official [Jekyll docs,](https://jekyllrb.com/docs/installation/macos/) you should not use the pre-installed version of Ruby on MacOS for Jekyll dev:

> To install Jekyll on macOS, you need a proper Ruby development environment. While macOS comes preinstalled with Ruby, we don’t recommend using that version to install Jekyll. This [external article](https://www.moncefbelyamani.com/why-you-shouldn-t-use-the-system-ruby-to-install-gems-on-a-mac/) goes over the various reasons why you shouldn’t use the system Ruby.

So, instead, I followed the official [Jekyll MacOS docs](https://jekyllrb.com/docs/installation/macos/):

1. Install Homebrew
2. Install chruby and the latest Ruby with ruby-installPermalink
3. Install jekyll

I had to also do a fourth step in VS Code terminal

4. `bundle add webrick` See: https://stackoverflow.com/a/70916831

## Windows Installation
I have tried to get Jekyll installed in Windows in the past and failed. I gave it another run the other day and it worked! Here are my notes:

**First**, although this documentation is old, I started with this [Run Jekyll on Windows](https://jekyll-windows.juthilo.com/) guide. The first step states to Install Ruby via the [rubyinstaller.org](http://rubyinstaller.org/downloads/) website and then to install the Ruby Devkit; however, the most recent versions of Ruby Installer for Windows also allows you to install the Devkit. So, that's what I did.
 
**Second**, I then opened `Windows Powershell` and typed `gem install jekyll`:

```
gem install jekyll
Fetching jekyll-4.1.1.gem
Fetching mercenary-0.4.0.gem
Successfully installed mercenary-0.4.0
Successfully installed jekyll-4.1.1
Parsing documentation for mercenary-0.4.0
Installing ri documentation for mercenary-0.4.0
Parsing documentation for jekyll-4.1.1
Installing ri documentation for jekyll-4.1.1
Done installing documentation for mercenary, jekyll after 16 seconds
2 gems installed
```

**Third**, I then tried to install `github-pages` via: `gem install github-pages` but failed with:

```
ERROR:  Error installing github-pages:
        The last version of nokogiri (>= 1.10.4, < 2.0) to support your Ruby & RubyGems was 1.10.9. Try installing it with `gem install nokogiri -v 1.10.9` and then running the current command again
        nokogiri requires Ruby version >= 2.3, < 2.7.dev. The current ruby version is 2.7.0.0.
```

So, I tried:

```
gem install nokogiri -v 1.10.9
ERROR:  Error installing nokogiri:
        The last version of nokogiri (= 1.10.9) to support your Ruby & RubyGems was 1.10.9. Try installing it with `gem install nokogiri -v 1.10.9`
        nokogiri requires Ruby version >= 2.3, < 2.7.dev. The current ruby version is 2.7.0.0.
```

But this also failed. And given that I have no idea how hard it would be to downgrade Ruby and whether that would wreck other dependences, I searched the Internet and found this [Issue](https://github.com/sparklemotion/nokogiri/issues/1961) on the Nokogiri GitHub. So, then I tried [this](https://github.com/sparklemotion/nokogiri/issues/1961#issuecomment-581851368):

```
gem inst nokogiri --pre
Fetching nokogiri-1.11.0.rc2-x64-mingw32.gem
Nokogiri is built with the packaged libraries: libxml2-2.9.10, libxslt-1.1.34, zlib-1.2.11, libiconv-1.15.
Successfully installed nokogiri-1.11.0.rc2-x64-mingw32
Parsing documentation for nokogiri-1.11.0.rc2-x64-mingw32
Installing ri documentation for nokogiri-1.11.0.rc2-x64-mingw32
Done installing documentation for nokogiri after 10 seconds
1 gem installed
```

This worked. Yay!

But I still couldn't install github pages, boo!

```
gem install github-pages
ERROR:  Error installing github-pages:
        The last version of nokogiri (>= 1.10.4, < 2.0) to support your Ruby & RubyGems was 1.10.9. Try installing it with `gem install nokogiri -v 1.10.9` and then running the current command again
        nokogiri requires Ruby version >= 2.3, < 2.7.dev. The current ruby version is 2.7.0.0.
```

So then I just tried `bundle install` and that worked. Whew. But this is/was possibly because I was in my physcomp dir... which has a Gemfile, etc.?

## Initial Setup

Once I had Jekyll installed, I did the following.

**First**, I made this repo and went to **settings** on GitHub for the repo and selected Master Branch for GitHub pages. I then tested that the website was serving on GitHub by going to https://jonfroehlich.github.io/mmtest2/ and it was. Note: I did not select a theme here.

**Second**, I went to the [Minimal Mistakes GitHub Pages Starter](https://github.com/mmistakes/mm-github-pages-starter) and rather than forking or using as a template, I copied over the `.gitignore`, `Gemfile`, `index.html`, and `_config.yml` files to the root directory of this repo.

**Third**, I ran `bundle`, which resulted in:

```
bundle
Fetching gem metadata from https://rubygems.org/...........
Fetching gem metadata from https://rubygems.org/.
Resolving dependencies...............................
Using concurrent-ruby 1.1.6
Using i18n 0.9.5
Fetching multi_json 1.14.1
Installing multi_json 1.14.1
Fetching activesupport 3.2.22.5
Installing activesupport 3.2.22.5
Using public_suffix 3.1.1
Using addressable 2.7.0
Fetching awesome_print 1.8.0
Installing awesome_print 1.8.0
Fetching json 2.3.1
Installing json 2.3.1 with native extensions
Using nokogiri 1.11.0.rc2 (x64-mingw32)
Fetching algolia_html_extractor 2.2.1
Installing algolia_html_extractor 2.2.1
Fetching httpclient 2.8.3
Installing httpclient 2.8.3
Fetching algoliasearch 1.27.3
Installing algoliasearch 1.27.3
Using bundler 2.1.2
Using coffee-script-source 1.11.1
Using execjs 2.7.0
Using coffee-script 2.4.1
Using colorator 1.1.0
Using ruby-enum 0.8.0
Using commonmarker 0.17.13
Using dnsruby 1.61.3
Using eventmachine 1.2.7 (x64-mingw32)
Using http_parser.rb 0.6.0
Using em-websocket 0.5.1
Using ffi 1.13.1 (x64-mingw32)
Using ethon 0.12.0
Using multipart-post 2.1.1
Using faraday 1.0.1
Fetching filesize 0.2.0
Installing filesize 0.2.0
Using forwardable-extended 2.6.0
Using gemoji 3.0.1
Using sawyer 0.8.2
Using octokit 4.18.0
Using typhoeus 1.4.0
Using github-pages-health-check 1.16.1
Using rb-fsevent 0.10.4
Using rb-inotify 0.10.1
Using sass-listen 4.0.0
Using sass 3.7.4
Using jekyll-sass-converter 1.5.2
Using listen 3.2.1
Using jekyll-watch 2.2.1
Using kramdown 1.17.0
Using liquid 4.0.3
Using mercenary 0.3.6
Using pathutil 0.16.2
Using rouge 3.19.0
Using safe_yaml 1.0.5
Using jekyll 3.8.7
Using jekyll-avatar 0.7.0
Using jekyll-coffeescript 1.1.1
Using jekyll-commonmark 1.3.1
Using jekyll-commonmark-ghpages 0.1.6
Using jekyll-default-layout 0.1.4
Using jekyll-feed 0.13.0
Using jekyll-gist 1.5.0
Using jekyll-github-metadata 2.13.0
Using html-pipeline 2.13.0
Using jekyll-mentions 1.5.1
Using jekyll-optional-front-matter 0.3.2
Using jekyll-paginate 1.1.0
Using jekyll-readme-index 0.3.0
Using jekyll-redirect-from 0.15.0
Using jekyll-relative-links 0.6.1
Using rubyzip 2.3.0
Using jekyll-remote-theme 0.4.1
Using jekyll-seo-tag 2.6.1
Using jekyll-sitemap 1.4.0
Using jekyll-swiss 1.0.0
Using jekyll-theme-architect 0.1.1
Using jekyll-theme-cayman 0.1.1
Using jekyll-theme-dinky 0.1.1
Using jekyll-theme-hacker 0.1.1
Using jekyll-theme-leap-day 0.1.1
Using jekyll-theme-merlot 0.1.1
Using jekyll-theme-midnight 0.1.1
Using jekyll-theme-minimal 0.1.1
Using jekyll-theme-modernist 0.1.1
Using jekyll-theme-primer 0.5.4
Using jekyll-theme-slate 0.1.1
Using jekyll-theme-tactile 0.1.1
Using jekyll-theme-time-machine 0.1.1
Using jekyll-titles-from-headings 0.5.3
Using jemoji 0.11.1
Using minima 2.5.1
Using unicode-display_width 1.7.0
Using terminal-table 1.8.0
Using github-pages 206
Fetching verbal_expressions 0.1.5
Installing verbal_expressions 0.1.5
Fetching jekyll-algolia 1.1.5
Installing jekyll-algolia 1.1.5
Fetching jekyll-include-cache 0.2.0
Installing jekyll-include-cache 0.2.0
Fetching tzinfo 2.0.2
Installing tzinfo 2.0.2
Fetching tzinfo-data 1.2020.1
Installing tzinfo-data 1.2020.1
Fetching wdm 0.1.1
Installing wdm 0.1.1 with native extensions
Bundle complete! 10 Gemfile dependencies, 93 gems now installed.
Use `bundle info [gemname]` to see where a bundled gem is installed.
PS C:\git\mmtest2>
```

**Forth**, I created `_data/navigation.yml` as instructed [here](https://mmistakes.github.io/minimal-mistakes/docs/quick-start-guide/#starting-fresh)

**Fifth**, I tried running the site by `bundle exec jekyll serve` and it appeared to work. Yay!


# Awesome-CV Second Assignment
[View Site](https://moya10.github.io/awesome-cv/)

## Installation & setup guide
This template is designed to be hosted using GitHub pages and so that's what these instructions will cover. If you plan on hosting it seperately then there might be some extra steps that we wont cover.

Before starting it might be useful to familiarise yourself with [Jekyll](https://jekyllrb.com/docs/home/), [Markdown](https://www.markdownguide.org/getting-started) and [GitHub pages](https://pages.github.com/).

## Usage

##### _config.yml
This will contain all the of the main configuration for your resume such as your name, email, social media links and about me content. It will also allow you to change the titles of some of the content sections.
A full example of the _config.yml can be found [here](https://github.com/sproogen/modern-resume-theme/blob/master/_config.yml)

##### _data/education.yml
A list of all your education, each education will follow this format

##### _data/experience.yml
A list of all your experience, each experience will follow this format

##### _data/projects.yml
A list of all your projects, each project will follow this format

##### assets/main.scss
Add any css changes or additions you want to make here after the line `@import 'modern-resume-theme';`

## Running locally

Before you start make sure you have *Ruby* and the gems for *Jekyll* installed locally. You can find out how to do that [here](https://jekyllrb.com/docs/installation/).

1. Clone your resume repository locally *(if you haven't already)*
2. `cd [your-repository-name]`
3. `bundle install`
4. `bundle exec jekyll serve`
5. Open your browser to `http://localhost:4000`

Any changes you make will automatically build and you will be able to see these by refreshing your browser.

*Note: You will need to re-run `bundle exec jekyll serve` to see changes made in `_config.yml`.*

## LaTex - CV

### Locally

Before you start make sure you have *pandoc* [here](https://pandoc.org/installing.html) and *MikTeX* [here](https://miktex.org/download) installed in your computer.

Then put inside makefile the code below:

`TEX = pandoc details.yml `

`src = template.tex`

`FLAGS =`

`resume.tex : $(src)`

`	$(TEX) $(filter-out $<,$^ ) -o $@ --template=$< $(FLAGS)`

` .PHONY: clean`

`clean :`

`rm resume.tex`
  
This will create the *resume.tex* file. Run it locally to produce the *resume.pdf*.

In *_config.yml* add the cv option and a link to download the *resume.pdf* file.

## Upload

Upload the whole .git project in your repository and create the *gh-pages* branch.


## Continuous Integration

To set up Travis CI, put the following in the .travis.yml file in your repository:


`language: ruby`

`cache: bundler `

`before_install: `

` - gem update bundler`

`  - wget https://github.com/jgm/pandoc/releases/download/1.15.2/pandoc-1.15.2-1-amd64.deb`

`  - sudo dpkg -i pandoc-1.15.2-1-amd64.deb`

`  - rm pandoc-1.15.2-1-amd64.deb`

`- sudo apt-get -qq update && sudo apt-get install -y --no-install-recommends texlive-full`

`install:`

`  - bundle install`
  
`script:`

`  - bundle exec jekyll build`

`  - make`

`  - pdflatex -interaction=nonstopmode -halt-on-error *.tex`
 
`branches:`

`  only:`

`  - gh-pages`

`sudo: false`


Usage of other commands, such as latex or xelatex, is analogous.

See Trvais CI build output 

![Image](https://bipolartest.000webhostapp.com/image.png)
[build](https://travis-ci.com/moya10/awesome-cv)

With *pull-request* I add the changes from *release branch-tree* to *gh-pages branch-tree*

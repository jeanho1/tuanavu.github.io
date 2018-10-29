My blog
---

This is my blog which is powered by [Jekyll](http://jekyllrb.com/) and [Minimal Mistakes jekyll theme](https://mmistakes.github.io/minimal-mistakes/).

## Info

**Info about which pages to edit** is in `_pages/markdown.md`

**Change content of main landing page** in `index.html`.

**Change sidebar content** in `_config.yml`

**To run the site locally**, run `bundle exec jekyll serve`

**To change formats of things**, try to find the respective `.scss` file in the `_sass` folder.

**To change main navigation content**, edit `navigation.yml` in `_data`.

## Add blog posts

Individual blog posts are in the `_posts` folder.
The files need to be formatted as `yyyy-mm-dd` for them to be parsed by the code in `_pages/year-archive.md` and added to the main blog page.

The header info for each blog post needs the following:

- `title`: title of the blog post. No need for single quotes unless there's a special character (especially a colon) in the title.   
- `permalink`: link to the post. Note that if you also have something called `link`, then the `title` will link to whatever you put in `link` and the `Read more` will link to the `permalink`. Best to only have one link though...   

The main blog page will show the first paragraph of text, and then include a `Read more...` link.
Most of the blog post behavior is defined in `{% include archive-single.html %}` (`archive-single.html` is in the `_includes` folder).

## Notes on notebooks

1. Write the jupyter notebook in the `_jupyter` folder   
1. When it's finished, `jupyter nbconvert <nb> --to markdown`   
1. Move it to the `_posts` folder   
1. Move the images to the `images` folder    
1. Add `/images/` to all image paths in the markdown file   

You can also run the `convert_and_move.sh` function in the `_jupyter` folder.
Note that you still have to go in and manually add the `/images/` path,
and if there are any non-extension dots in the file name these should be changed
to hyphens. You also need to go and add the header to the post.

Still to figure out: how to change font size/format of cells, how to have **[In 1]** show up, how to add image captions.

## To run locally

- Clone the repository and made updates as detailed above
- Make sure you have ruby-dev, bundler, and nodejs installed: `sudo apt install ruby-dev ruby-bundler nodejs`
- Run `bundle clean` to clean up the directory (no need to run `--force`)
- Run `bundle install` to install ruby dependencies. If you get errors, delete Gemfile.lock and try again.
- Run `bundle exec jekyll serve` to generate the HTML and serve it from localhost:4000

# Create a blog post

The VA Big Data Genomics blog is created using [Jekyll](https://jekyllrb.com/) and hosted on GitHub Pages.

## (Optional) Clone the repo
Clone the repository to your local machine so that you can make edits and see how they will look on a local deployment of the blog. If you aren't concerned with that, you can create new posts directly through the GitHub web interface.

```
git clone git@github.com:va-big-data-genomics/va-big-data-genomics.github.io.git
```

## (Optional) Install Jekyll in your local environment
If you want to deploy a local version of the blog to see what it looks like, before deploying to production (recommended), follow the Jekyll [docs](https://jekyllrb.com/docs/) to install it on your local machine. Note: I found this process to be [kind of hairy](https://github.com/va-big-data-genomics/va-big-data-genomics.github.io/issues?q=is%3Aissue+is%3Aclosed).

## Create your post markdown file
To create a blog post, add a  markdown file to the `_posts` director. Post file names should include the date and post name according to the convention `yyyy-mm-dd-your-post-name.markdown`. For example: `_posts/2023-01-14-my-first-post.markdown`.

## Add a header to your post
Add a header to your file with relevant metadata including title, date, and author. Format the information in a block like the following and put it at the top of your markdown file.

```
---
layout: post
title:  "My first post!"
date:   2023-01-14 10:10:02 -0800
author: Ameer Researcher
categories: jekyll update
---
```

Note that your post won't show up on the blog until the date/time you specify here.

## Use markdown to write your post.

You can refer to this style guide for markdown syntax: [https://www.markdownguide.org/basic-syntax/](https://www.markdownguide.org/basic-syntax/). If you use Visual Studio Code as your editor, you can also view the rendered markdown document as you type.

## Deploy the blog locally

To see your new post on the blog, refer back the [Jekyll docs](https://jekyllrb.com/docs/) to launch a local server.

## Push your commits to the `main` branch

Once you are happy with your post, push all your changes to the `main` branch of the repository. Changes will automatically be deployed to the blog site.

Good luck!



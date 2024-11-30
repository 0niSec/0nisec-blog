+++
title = "Migrating to Hugo"
description = "How and why I migrated my blog from Astro to Hugo"
tags = ["hugo", "astro", "migrating", "programming"]
date = 2024-11-29
cover = "/images/hugo-logo-wide.png"
draft = false
toc = true
+++

## What is Astro?

[AstroJS](https://astro.build) is a web framework for content driven sites. By their own admission, it "powers the world's fastest marketing sites, blogs, e-commerce websites, and more." It's a really great tool for building blogs and well...content driven sites, just like they say.

There's a lot of reasons why I picked Astro initially and [this](https://docs.astro.build/en/concepts/why-astro/) page goes over a lot of them. For the most part, I liked its use of [content collections](https://docs.astro.build/en/guides/content-collections/) that help you quickly and easily organize whatever content your site may have. In my case, it was my blog posts. The documentation contained a very easy to follow tutorial on how to set up Astro for use in a blog and that made it very attractive as well. Astro also has all the normal things you'd find in a Javascript framework such as layouts, components and the ability to render content on the client and/or server. All of this made it really nice to use and attractive to me in the first place.

## What is Hugo?

[Hugo](https://gohugo.io) is a Static Site Generator (SSG). An SSG generates all pages at build time, which results in a static website that can be served quickly and efficiently. The developers boast that it's "one of the most popular open-source static site generators" and "the world's fastest framework for building websites." It's written in [Go](https://go.dev), is easy to get going, has good [documentation](https://gohugo.io/documentation/), supports a number of content types and has built in shortcodes (which are sort of like partials from Ruby on Rails if you're familiar).

## Why the Switch?

I leaned more towards Astro to begin with because it was familiar (I play a lot with different Javascript frameworks) and honestly, was easy to set up. However, even though I used the default "blog" template that is provided when you first scaffold your project, I still ended up writing a lot of HTML and CSS. That was in addition to writing the actual content! Trying to get everything perfect, bug free, jank free, and nice looking took a lot of time and admittedly the current version of the site does look quite nice (to me), but is still missing some things that I'd have to take more time to set up and most likely, break, then fix. I wanted something that:

- Was fast
- Was easy to configure
- Had nice starter themes
- Was based on something other than JS (though I would give them a look at least)
- Had easy to follow documentation for my ADHD brain

I began looking into SSGs because I know they are fast and had heard the names of Hugo, [11ty](https://11ty.dev), [Gatsby](https://www.gatsbyjs.com/), and [Jekyll](https://jekyllrb.com/), and I wanted to see if they ticked off any of the boxes above.

I eliminated 11ty because I tried going through their documentation and maybe I was tired that day or I'm slow, but I found it incredibly difficult to sort through in terms of where to actually start for a project. As for Gatsby, well, I definitely didn't want to write React (sorry to I'm sure someone reading this) and again ran into the documentation problem. Again, maybe I wasn't looking at the right place or was tired or something, but if it takes me longer than 5 minutes to figure out how to _actually_ get started, I will most likely give up. Just how my brain works, for better or worse.

So that left Jekyll and Hugo. This is extremely silly but this came down to the Github stars for each and, to a lesser degree, my interpretation of the quality of the website. That may sound completely insane to most of you, but it matters to me for some weird reason. And the winner was Hugo. But Jekyll ticks every single box above too.

## Migrating

The migration process was pretty painless and pretty much every blog post I had in my Astro site could be pasted into the Hugo site. But I want to provide some context to more of the process.

### Installing Hugo

To install Hugo, it's really as simple as following their [install instructions](https://gohugo.io/installation/). I was doing this on my Linux OS so I downloaded the `.deb` file of the extended version and a simple `dpkg -i` was all I needed.

It's a little more involved on Windows, but it's not bad. I've installed Hugo on Linux and Windows at this point and both are really easy. Linux is just a little easier just by what it is.

### Finding and Installing a Theme

It is absolutely possible to style your own website. But like I said earlier, I didn't want to have to mess with HTML or CSS anymore. I wanted something that locked me into a design choice because otherwise, I'd be wanting to customize it ALL the time. You can still do that with a custom theme, though. I just know that if I use someone else's work, I'm less likely to try to go in and figure it out to make changes.

Hugo has tons of [themes](https://themes.gohugo.io/) on their site and they're tagged by topic. Since I wanted a blog, I just cicked "Blog" and looked for one I liked. I ended up going with the [terminal](https://themes.gohugo.io/themes/hugo-theme-terminal/)! It's hacker-y and that's what we're going for here!

Installing themes is really easy. For this theme, it was just a matter of adding it as a git submodule

```git
git submodule add -f https://github.com/panr/hugo-theme-terminal.git themes/terminal
```

## Conclusion

So now that this site is using Hugo, what can I say? I like it! It was easy to get started, easy to get things moved over and all that's left that I didn't mention was getting it hosted. I use Netlify and already know this will be easy to get on there, so I'm not worried.

Astro absolutely has its merits and I will possibly use it again in the future for something else, but at the moment - we're sticking with Hugo.

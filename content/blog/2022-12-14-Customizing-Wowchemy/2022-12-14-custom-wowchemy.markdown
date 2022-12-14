---
title: "Miscellaneous Tips for Customizing your Wowchemy Academic Site"
author: ["admin"]
date: '2022-12-14'
lastmod: '2022-12-14'
slug: custom-wowchemy
draft: true
categories: []
tags: []
summary: "Notes from far too long spent googling around for tips on customizing this Wowchemy site"
subtitle: "Notes from far too long spent googling around for tips on customizing this Wowchemy site"
smartDashes: true
toc: true
commentable: true
---

[Oops, I pushed this blog post long before it was finished and can't be bothered ]

It's undeniably great that blogdown/Hugo Academic (now Wowchemy) have made creating a professional website so accessible, but there is a notable downside: it becomes really hard to make your own stand out. 

To try and leave a slightly more lasting mark, I spent more hours than I'd like to admit googling around, trying to find little tweaks that would differentiate my website from the standard template. I'm generally happy with the result, and I figured if I could cut down on the frustration for others by sharing what I did, I might as well. I have no web design experience, and struggled throughout with html/css/go, as well as with the structure of the website more generally. In other words, if I can do it, so can you! 

The full codebase used for my website is available on [Github](https://github.com/nballou/nickballousite)

**Crucial note**: These alterations frequently did not work out of the box for me when using others' code, and they similarly may not for you. Due to 1) differences in Wowchemy versions and other idiosyncratic parts of your setup, and 2) poor documentation from me after having done a lot of trial and error, these tips are more about pointing you in the right direction rather than directly solving your problems. 

# Setting up your site

These tips assume that you already have a working, deployed version of a Wowchemy site. This is too large a topic to dive into here, but some of the resources that I found helpful when doing this the first time included: 

- [Dan Quintana's blog post on creating your website](https://www.dsquintana.blog/create-an-academic-website-free-easy-2020/)
- [Andreas Handel's post on creating a website in under an hour](https://www.andreashandel.com/posts/2020-01-02-blogdown-website-1/index.html)
- [Wowchemy's own tutorial/guide](https://wowchemy.com/docs/getting-started/hugo-github-quickstart/) (duh)

# Custom Wowchemy basics

Customizations to your Wowchemy site typically take one of 3 forms:

- Changing a predefined parameter, 

# Changes on my site

## About widget

The about widget is the first thing your visitors are going to see, and therefore was the 

## Make "about" widget fill entire screen

This alteration was inspired by [Matteo Courthoud's site](https://matteocourthoud.github.io), and he also wrote his own helpful tutorial on how to achieve similar results. 

## Add background image to bottom of about widget

## Add animations to about widget 

This alteration was inspired by [Connor Rothschild's post](https://www.connorrothschild.com/post/animate-hugo-academic), which describes how to use relatively simple CSS code to animate elements of one's page. 

The blog post describes how to do basic animations, using two steps:

1. Identify the class of the element you'd like to animate, which you can do by either:
  a. Co-opting the classes already used by Wowchemy (you can use the inspect element feature of your browser, for example, to look at these)
  b. Adding or amending the classes in the underlying html code by altering . 

Ultimately, I borrowed code from the [old version of his website](https://github.com/connorrothschild/v2), and lightly amended it to get the elements to slide in from opposite sides.

The relevant bits of the code for mine, which live in `assets/scss/custom.scss` (you'll need to create this folder/file if you don't have it already, see Connor's blogpost for more details), are the following:

<style type="text/css">

pre {
  max-height: 300px;
  overflow-y: auto;
}

pre[class] {
  max-height: 300px;
}

.scroll-100 {
  max-height: 300px;
  overflow-y: auto;
  background-color: inherit;

</style>


```css
/* Animate text coming from right */ 
.main-content {
  animation: slide-from-right 1.5s cubic-bezier(0.4, 0, 0.13, 1) forwards;
  animation-delay: 0ms;
}

/* Animate CV button coming from right */ 
.btn-download {
  opacity: 0;
  animation: fade-in 2s forwards;
  animation-delay: 1.4s;
}

#profile {
  
  .avatar-square {
  -webkit-clip-path: polygon(25% 5%, 75% 5%, 100% 50%, 75% 95%, 25% 95%, 0% 50%);
  clip-path: polygon(25% 5%, 75% 5%, 100% 50%, 75% 95%, 25% 95%, 0% 50%);
  opacity: 0;
  position: relative;
  right: -300px;
  -webkit-animation: slide-left 2s cubic-bezier(0.87, 0, 0.13, 1) forwards;
  animation: slide-left 2s forwards cubic-bezier(0.87, 0, 0.13, 1) forwards;
  }

  .portrait-title {
    opacity: 0;
    position: relative;
    left: -1000px;
    -webkit-animation: slide-right 2s cubic-bezier(0.87, 0, 0.13, 1) forwards;
    animation: slide-right 2s cubic-bezier(0.87, 0, 0.13, 1) forwards;
    
  }
  
  @-webkit-keyframes slide-right {
      100% { left: 0; opacity: 1}
  }
  
  @keyframes slide-right {
      100% { left: 0; opacity: 1; }
  }
  
  @-webkit-keyframes slide-left {
      100% { right: 0; opacity: 1; }
  }
  
  @keyframes slide-left {
      100% { right: 0; opacity: 1; }
  }
}
```


<style type="text/css">
/* Animate text coming from right */ 
.main-content {
  animation: slide-from-right 1.5s cubic-bezier(0.4, 0, 0.13, 1) forwards;
  animation-delay: 0ms;
}

/* Animate CV button coming from right */ 
.btn-download {
  opacity: 0;
  animation: fade-in 2s forwards;
  animation-delay: 1.4s;
}

#profile {
  
  .avatar-square {
  -webkit-clip-path: polygon(25% 5%, 75% 5%, 100% 50%, 75% 95%, 25% 95%, 0% 50%);
  clip-path: polygon(25% 5%, 75% 5%, 100% 50%, 75% 95%, 25% 95%, 0% 50%);
  opacity: 0;
  position: relative;
  right: -300px;
  -webkit-animation: slide-left 2s cubic-bezier(0.87, 0, 0.13, 1) forwards;
  animation: slide-left 2s forwards cubic-bezier(0.87, 0, 0.13, 1) forwards;
  }

  .portrait-title {
    opacity: 0;
    position: relative;
    left: -1000px;
    -webkit-animation: slide-right 2s cubic-bezier(0.87, 0, 0.13, 1) forwards;
    animation: slide-right 2s cubic-bezier(0.87, 0, 0.13, 1) forwards;
    
  }
  
  @-webkit-keyframes slide-right {
      100% { left: 0; opacity: 1}
  }
  
  @keyframes slide-right {
      100% { left: 0; opacity: 1; }
  }
  
  @-webkit-keyframes slide-left {
      100% { right: 0; opacity: 1; }
  }
  
  @keyframes slide-left {
      100% { right: 0; opacity: 1; }
  }
}
</style>

I'm particularly pleased with the staggered fade-in of the contact icons. All that was required to achieve that was to add a fade-in animation to each of those icons, and fuss with the timing a little bit: 


```css
.network-icon {
    
    margin-top: 15px;
    padding: 5px;
    
    .fa-envelope {
      opacity: 0;
      -webkit-animation: grow 2s ease forwards;
              animation: grow 2s ease forwards;
      -webkit-animation-delay: 1.3s;
              animation-delay: 1.3s;
    }
    
    .fa-mastodon {
      opacity: 0;
      -webkit-animation: grow 2s ease forwards;
              animation: grow 2s ease forwards;
      -webkit-animation-delay: 1.4s;
              animation-delay: 1.4s;
    }
    
    .fa-linkedin {
      opacity: 0;
      -webkit-animation: grow 2s ease forwards;
              animation: grow 2s ease forwards;
      -webkit-animation-delay: 1.5s;
              animation-delay: 1.5s;
    }
    
    .fa-playstation {
      opacity: 0;
      -webkit-animation: grow 2s ease forwards;
              animation: grow 2s ease forwards;
      -webkit-animation-delay: 1.6s;
              animation-delay: 1.6s;
    }
    
    @-webkit-keyframes grow {
        100% { opacity: 1; }
    }
    
    @keyframes grow {
        100% { opacity: 1; }
    } 
  }
```


<style type="text/css">
.network-icon {
    
    margin-top: 15px;
    padding: 5px;
    
    .fa-envelope {
      opacity: 0;
      -webkit-animation: grow 2s ease forwards;
              animation: grow 2s ease forwards;
      -webkit-animation-delay: 1.3s;
              animation-delay: 1.3s;
    }
    
    .fa-mastodon {
      opacity: 0;
      -webkit-animation: grow 2s ease forwards;
              animation: grow 2s ease forwards;
      -webkit-animation-delay: 1.4s;
              animation-delay: 1.4s;
    }
    
    .fa-linkedin {
      opacity: 0;
      -webkit-animation: grow 2s ease forwards;
              animation: grow 2s ease forwards;
      -webkit-animation-delay: 1.5s;
              animation-delay: 1.5s;
    }
    
    .fa-playstation {
      opacity: 0;
      -webkit-animation: grow 2s ease forwards;
              animation: grow 2s ease forwards;
      -webkit-animation-delay: 1.6s;
              animation-delay: 1.6s;
    }
    
    @-webkit-keyframes grow {
        100% { opacity: 1; }
    }
    
    @keyframes grow {
        100% { opacity: 1; }
    } 
  }
</style>

## Change shape of profile picture 

Make sure `/config/_default/config.yaml` has avatar shape set to `square`, rather than circle. From there, you can use the CSS `clip-path` property to reshape your image. I wanted to have a hexagon, so I added the following to my `custom.scss`:




Source: [https://codepen.io/imohkay/pen/ZGbmoQ](https://codepen.io/imohkay/pen/ZGbmoQ)

# Other changes

## Add table of contents to blog posts

## Add Gisqus for commenting

Look, I'm not kidding myself that my blog posts are going to have a ton of traction or interest, but in the post-Twitter era, I like the idea that people at least have the *option* to leave a comment on the post itself. I'm not a huge fan of Disqus, both due to its UI and its tendency to harvest and sell your data, and I don't want to pay if I don't have to, so I settled on using Gisqus. 

https://zhauniarovich.com/post/2021/2021-06-giscus/

I primarily followed this tutorial on how to set up giscus, but I needed to gid into the commit history to find [this post](https://github.com/wowchemy/wowchemy-hugo-themes/pull/2830) with the updated partial code. For my version of Wowchemy, the `giscus.html` file inside layouts/partials/comments` should therefore be: 


```html
{{ if site.Params.features.comment.giscus }}
<script src="https://giscus.app/client.js"
        data-repo="{{site.Params.features.comment.giscus.repo}}"
        data-repo-id="{{site.Params.features.comment.giscus.repo_id}}"
        data-category="{{site.Params.features.comment.giscus.category}}"
        data-category-id="{{site.Params.features.comment.giscus.category_id}}"
        data-mapping="{{site.Params.features.comment.giscus.mapping}}"
        data-reactions-enabled="{{site.Params.features.comment.giscus.reactions_enabled}}"
        data-theme="{{site.Params.features.comment.giscus.theme}}"
        crossorigin="anonymous"
        async>
</script>
<noscript>Please enable JavaScript to view the comments powered by giscus.</noscript>
{{ end }}
```


## Add custom email address

After almost 15 years with my beloved gmail address, I decided it would be nice to have a custom email address associated with the domain. I use Google domains for registering my 

---
author: Joash Geteregechi
categories:
- Theme Features
date: "2022-07-18"
draft: false
excerpt: There are times when you have a huge data set but you are only interested in a few variables (columns). What do you do that case? Suppose you want to transform a given variable using some criteria, what do you do? Manipulating a data set into a more usable form is often referred to as data wrangling. In this post, I provide a few quick tips that you may find helpful when dealing with a huge data set.
  
layout: single
subtitle: Data wrangling is one of the most important tools that a data scientist needs to have.

title: Data Wrangling in Rstudio (Tidyverse)
---

There are six basic functions that you need in order to wrangle data. These are:

-   select
-   mutate
-   filter  
-   arrange
-   summarize, and
-   group_by <!-- The following links other pages on the website. I commented them out but you may find them very helpful. the + sign is just for adding an item, not required.
    + [homepage](/) (set in `content/_index.md`),
    + [about page](/about) in the sidebar (set in `content/about/sidebar/index.md`), and
    + [contact page](/contact) (set in `content/form/contact.md`). -->

Read on to learn how to use these functions:

## Select

Wherever you end up wanting to show choose only specific variables in your data for use, you'll need to use the select function.

``` toml
[params]
  <!--snip snip-->
  
  1. Know the dataframe name. Lets say the dataframe is named x.
  2. Know the variables you are interested in. Lets say a, b, c.
  3. If you want to rename the new dataframe, choose an appropriate name, say, y.
  4. If you are working in Rmarkdown environment, open a new code chunk and write 
  the the code (without the hash tag):
  
   # y <- x %>% select (a, b, c)
   
  5. Run the code and look out for a new object "y" in the environment area. You 
  have just created a smaller dataset with variables of  interest to you.
  
  Note: 
    
  a. The sign "%>%" is called a pipe operator. It merely takes anything 
    on its left and pumps it out into the function on its right. You can use mult
    iple piples within the same code chunk.
    
  b. The sign "<-" is what we use to create a "container" to store our new object
  
```

For each link, you'll need to start a new portion that begins with `[[params.social]]`. Then, pick your `icon` and `icon_pack` from the [Font Awesome](https://fontawesome.com/) free icon library:

-   Icon pack "fab" includes [brand icons](https://fontawesome.com/icons?d=gallery&s=brands&m=free)

-   Icon pack "fas" includes [solid icons](https://fontawesome.com/icons?d=gallery&s=solid&m=free)

-   Icon pack "far" includes [regular icons](https://fontawesome.com/icons?d=gallery&s=regular&m=free)

Finally, add the `url` that you would like users to go to when they click on that icon. All external links (i.e., those that start with `http`) will open in a new tab (that is, `target="_blank"`); relative links to pages within the site will open in the same window.

Now you should be all set to show/hide your social icons. Each of these will pull the social icons and urls from the settings you just created in your site configuration file.

## Show social in site header and footer

Let's start with the header and footer, as those are site-wide. Open up your site `config.toml` file again and scroll down to the `[params]` section (it is actually :up: from where you configured these icons):

``` toml
[params]
  <!--snip snip-->
  
  # show/hide social icons in site header & footer
  # configure social icons and links below in [[params.social]]
  socialInHeader = false
  socialInFooter = true
```

That was easy!

## Filter

Just like we can select a few variables (columns) from our dataframe, it is possible to select a few rows in your dataframe. The function that does this is called **filter**. We use the filter function as follows: 

``` toml
[params]
  <!--snip snip-->
  
  1. Know the dataframe name. Lets say the dataframe is named x.
  2. Know the variables you are interested in. Lets say a, b, c.
  3. If you want to rename the new dataframe, choose an appropriate name, say, y.
  4. If you are working in Rmarkdown environment, open a new code chunk and write 
  the the code (without the hash tag):
  
   # y <- x %>% select (a, b, c)
   
  5. Run the code and look out for a new object "y" in the environment area. You 
  have just created a smaller dataset with variables of  interest to you.
  
  Note: 
    
  a. The sign "%>%" is called a pipe operator. It merely takes anything 
    on its left and pumps it out into the function on its right. You can use mult
    iple piples within the same code chunk.
    
  b. The sign "<-" is what we use to create a "container" to store our new object
  
```





Open up `content/_index.md`. That file's YAML controls what you see on the homepage. Set `show_social_links` like so:

``` yaml
show_social_links: true # specify social accounts in site config
```

If you set this to `true` to show the icons on the homepage, your social icons in the footer will not show up even when you set `socialInFooter = true`, so as not to litter your site with too many icons.

## Show social in about page sidebar

Open up `content/about/sidebar/index.md`. That file's YAML controls what you see in the sidebar on the about page. Set `show_social_links` like so:

``` yaml
show_social_links: true # specify social accounts in site config
```

## Show social in contact page

You may use the YAML for your contact page (located in `content/form/contact.md`):

``` yaml
---
show_social_links: true # specify social accounts in site config
---
```

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

In this post, I talk about some of the basic functions that are frequently used in data wrangling. The assumption is that you have already installed Rstudio in your system (or have access to Rstudio cloud) and that you have some familiarity with Rmarkdown and the Tidyverse package. These are:

-   select
-   mutate
-   filter  
-   arrange
-   "summarize", and
-   group_by

<!-- The following links other pages on the website. I commented them out but you may find them very helpful. the + sign is just for adding an item, not required.
    + [homepage](/) (set in `content/_index.md`),
    + [about page](/about) in the sidebar (set in `content/about/sidebar/index.md`), and
    + [contact page](/contact) (set in `content/form/contact.md`). -->

Read on to learn how to use these functions:

## Select

Wherever you end up wanting to show/choose only specific variables(columns) from a bigger dataframe, you'll need to use the select function.

``` toml
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
       on its left and pumps it out into the function on its right. You can use 
       multiple piples within the same code chunk.
    
    b. The sign "<-" is what we use to create a "container" to store our new 
       object
  
```

<!-- This stuff was on the template so I just commented it out in case I need it for later
For each link, you'll need to start a new portion that begins with `[[params.social]]`. Then, pick your `icon` and `icon_pack` from the [Font Awesome](https://fontawesome.com/) free icon library:

-   Icon pack "fab" includes [brand icons](https://fontawesome.com/icons?d=gallery&s=brands&m=free)

-   Icon pack "fas" includes [solid icons](https://fontawesome.com/icons?d=gallery&s=solid&m=free)

-   Icon pack "far" includes [regular icons](https://fontawesome.com/icons?d=gallery&s=regular&m=free)

Finally, add the `url` that you would like users to go to when they click on that icon. All external links (i.e., those that start with `http`) will open in a new tab (that is, `target="_blank"`); relative links to pages within the site will open in the same window.

Now you should be all set to show/hide your social icons. Each of these will pull the social icons and urls from the settings you just created in your site configuration file.
-->

## Mutate

The mutate function alters an existing variable in some way and creates a new column(variable) with a name that you designate. To use the mutate function, you will need to follow steps:

``` toml
  1. Know the dataframe name. Let us assume the dataframe is named x.
  2. Identify the variable that you want to modify and its exact spelling. Suppose the variable is age.
  3. Know what modification you want to make. For example, suppose you want to      divide the age variable by the mean of age and call the new variable 
     age_mean.
  4. If you are working in Rmarkdown environment, open a new code chunk and 
     write the the code below (without the hash tag, of course):
  
   # y <- x %>% mutate (age_mean = age/mean(age))
   
  5. Run the code and look out for a new object "y" in the environment area. You have just created a new dataframe with a new variable called age_mean.
  
  Note: 
    
    a. If you want to delete the original varible from the dataframe you may use the function "transmute" instead of "mutate".
    
    b. Note that the function mean(age) computes the mean of teh age variable. 
       If we know the mean to be 48.4, we can use that number directly. 
    
```

## Filter

Just like we can select certain variables (columns) from a dataframe, it is possible to select a certain rows (cases/observations) in a dataframe. The function that does this is called **filter**. We use the filter function as follows:

``` toml
1. Know the dataframe name. Let us assume the dataframe is named x.
  2. Know the criteria you want to use for filtering. For example, suppose you 
     have the variables "hair color" and "age" and you want cases for which hair
     color and age is greater than 55. Notice that "hair color" is categorical 
     while "age"
     is numerical.
  3. If you want to rename the new dataframe, choose an appropriate name, say, y.
  4. If you are working in Rmarkdown environment, open a new code chunk and 
     write the the code (without the hash tag):
  ``  # y <- x %>% filter (hair color == "black", age > 55)
     
     5. Run the code and look out for a new object "y" in the environment area. You 
  have just created a smaller dataset with cases that meet the defined criteria.
  
  Note: 
    
      a. We use the doube "==" here to set the value of a categorical variable 
         and that the value is in "quotes". 
        
      b. The criteria may be simple or complex depending on your situation.
      
      c. If you want to have have an "OR" condition (e.g., cases that have black 
        hair) or are older than 55, you will use "|" instead of a comma.
      
```

## Group_by

**Group_by** is a kind of filtering function that is commonly used in data wrangling. It often takes a dataframe and thinks of it in terms of groups as you define them. Let us say for example, that you have a variable gender (male, female, other) in your dataframe x above. ***Group_by*** can be used alongside other functions as shown:

``` toml
  1. Suppose we want to find the mean by gender (i.e., the mean age for female, 
     male, and other) in the dataframe. Suppose we want to store this information
     in a new object called mean_gender. To do this, we can run the code: 
  
       # mean_gender <- x %>% 
       # group_by (gender) %>% 
       # summarize(mean(age))
   

  Note: 
    
    a. The group_by function makes R to think about the data as different data 
      frames.
      
    b. The above code returns the means for each group in a single row. It 
       essentially flattens the data (i.e., the summarize functio) If for 
       some reason you want to have a new column in the dataframe with the mean 
       score for each group, you can replace the summarize function with mutate 
       as follows:

       # mean_gender <- x %>% 
       # group_by (gender) %>% 
       # mutate(mean=mean(age))
       
       This will add a new column to your dataframe with the means for each case.
```

<!--
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
-->

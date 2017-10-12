# Guide to publishing tutorials/blog posts on the Coding Club website
### https://ourcodingclub.github.io/

## Publishing a tutorial

Thanks for your interest in Coding Club and your contribution to the advancement of quantitative skills! Please follow the following guide when preparing your tutorial and feel free to contact gndaskalova@gmail.com should you have any questions or issues.

1. Register on Github and ask Gergana to add you to Coding Club's organisational account.

2. Create a new branch of the `ourcodingclub.github.io` repository with a sensible name related to your tutorial/post. Creating new branches, files etc. can done either using the Github web interface or by cloning the `ourcodingclub.github.io` repo to your own computer and doing it locally. For more on Github [check out our github tutorial](https://ourcodingclub.github.io/2017/02/27/git.html).

3. Switch to the new branch, and create a `.md` file for your tutorial in the `_posts/` folder. You can create a `.md` file through the Github web interface (remember you need to specify the file extension, e.g. `filename.md`), or by opening a text editor (see suggestions below) and going to `File/New file`.
	-  Name the file like this: `2017-04-28-datavis.md`, where: 
		-  `2017-04-28` is the date in `YYYY-MM-DD` format, the date should be before the tutorial is to be taught, so that everyone can see it online.
		-  `datavis` is a word relating to the content of the post.

4. Edit the new file using your faviourite plain text editor (_e.g._ Atom, TextEdit, Notepad, Vim, Sublime). Use the <a href="#style">style guide below</a> and existing tutorials as a guide. Are there any pre-requisites to completing your tutorial? You can add links to previous tutorials, so that people can complete them first, and then come back to your tutorial. It's nice to have in text references to previous tutorials with links to them, as that way more people can find out about them.

5. Create a header banner image for your post using `tutheaderbl.png` as a template. The image should contain the title and subtitle of your post, and it will appear at the start of your tutorial post. Please use 48pt bold Arial for the main title
and 30pt regular Arial for the sub-title and center both the title and subtitle. Name the header file like this: `tutheader_tutorialname.png`.

6. Upload any images (including the header banner image) to the `img` folder.

7. If the post is a tutorial, add a link to it in `work.html`, <a href="#work_html">see below for more info</a>. 

8. If you have additional tutorial materials like datasets, cheatsheets, example scripts, create a repository in the Coding Club root directory with a sensible name (e.g. `CC-Modelling`) and add upload them to that repository. Note we are not using numbers in our repo names anymore, even if some old repos are still numbered. Remember to add a `README.md`, <a href="#readme">see below for more info</a>.

9. Create a pull-request for your branch to be merged with the master branch. 

<a name="style"></a>

## Style Guide

### Header Material

This material should appear at the top of every tutorial `.md` file. It is important to use the same `date:` as the one in the `.md` tutorial filename. For tutorials this date should be approximately 4 days before it is taught in class, so that email recipients can look at the tutorial before it is run in class. The `title:` and `subtitle:` should be identical to that which is written on the header banner image for that tutorial:

```
---
title: "Title to appear on website"
author: "First name of Author"
date: "2017-04-25 08:00:00"
meta: Tutorials
subtitle: Subtitle to appear on website
layout: post
---
<div class="block">
	<center>
		<img src="{{ site.baseurl }}/img/tutheader_tutname.png" alt="Img">
	</center>
</div>
```

### Introduction Material

A tutorial should be broken down into tangible aims. Each aim should be in the form of an action where possible ('ing' words, learning, understanding, organising etc.). Each aim should be represented by a subheading in the tutorial with the same name where possible:

```
### Tutorial Aims:

#### <a href="#sections"> 1. Organising scripts into sections</a>

#### <a href="#syntax"> 2. Following a coding syntax etiquette</a>

```

### Subheadings

First level subheadings should be denoted by `###` and should contain the same text as the Tutorial Aim which links to it. All first level subheadings should be preceded by an internal link, linking it to a given Tutorial Aim. Second level subheadings should be denoted by `####`.

```
<a name="sections"></a>

### 1. Organising scripts into sections

#### Subsections like this

Some text

<a name="syntax"></a>

### 2. Following a coding syntax etiquette
```

### Referring to code and GUI elements:

When referring to an R package, file name, menu item, file type extension, object name or code snippet in text, always wrap in ````:

```
Today we are going to use `ggplot2` to make pretty graphs

The template can be found in `~/git_proj/template.R`

Click `New Script...` to make a new script

Go to `File/New file/R script` to get started

`width = 1.6` means give the image a width of 1.6 inches
```

When referring to an R function in text, always wrap in ```` and add `()` to the end:

```
Today we are going to use `ggplot()` to make a bar graph
```

When copying in a large chunk of code, add ```` ``` ```` above and below it. The language of the code can also be defined so the correct syntax highlighting is used:

````
This is normal text, look a code block written in python:

```python
name = raw_input('What is your name?\n')
print 'Hi, %s.' % name
```
````

### Tables

Please format all tables using html, not markdown, using the following style info. Each `<tr>` block represents one row, with each `<th>` block representing one column. <a href="http://www.tablesgenerator.com/html_tables" target="_blank">http://www.tablesgenerator.com/html_tables</a> is a decent html table generator if you can't be bothered typing this out manually:

```
<style type="text/css">
.tg  {border-collapse:collapse;border-spacing:0;}
.tg td{font-family:Arial, sans-serif;font-size:14px;padding:10px 5px;border-style:solid;border-width:1px;overflow:hidden;word-break:normal;}
.tg th{font-family:Arial, sans-serif;font-size:14px;font-weight:normal;padding:10px 5px;border-style:solid;border-width:1px;overflow:hidden;word-break:normal;}
.tg .tg-yw4l{vertical-align:top}
</style>
<table class="tg">
  <tr>
    <th class="tg-4w4l">Name</th>
    <th class="tg-4w4l">Code</th>
    <th class="tg-yw4l">Example</th>
  </tr>
</table>
```

### Lists

Bullet point lists should be formatted as headers. This is because our jekyll template doesn't deal well with markdown formatted lists. Lists should look like this:

```
##### - List item 1
##### - List item 2
##### - List item 3
```

### Shiny apps and other embedded material
Shiny apps and other similar embeddable material can be placed in an `iframe`, adjusting the height and width as needed to make it look sensible. Avoid making the user scroll through the app if possible by adjusting the height and width:

```
<iframe src="EMBEDDABLE_URL" style="border:none; width:1000px; height:550px;"></iframe>
```

### Web Links

Please format all hyperlinks using html, not markdown, in the following format. `target="_blank"` forces web browsers to open the link in a new tab:

```
<a href="FULL_LINK" target="_blank">DESCRIPTION OF LINK TO APPEAR AS TEXT</a>

```

### Image Links

Please format all image links using html, not markdown, in the following format. Adjust the `width:` argument so the image is sensibly sized. Normally nothing over 1000 pixels:

```
<center> <img src="{{ site.baseurl }}/img/IMAGE_NAME.png" alt="Img" style="width: 800px;"/> </center>
```

### Footer Material

This material should be added to the end of every tutorial. Replace `INSERT_SURVEY_LINK` with the actual URL to a Survey Monkey survey created using the Coding Club account (you can get in touch with Gergana for the password). The top lines of this section can be used to list acknowledgements and important links.

```
<hr>
<hr>

#### Check out our <a href="https://ourcodingclub.github.io/links/" target="_blank">Useful links</a> page where you can find loads of guides and cheatsheets.

#### If you have any questions about completing this tutorial, please contact us on ourcodingclub@gmail.com

#### <a href="INSERT_SURVEY_LINK" target="_blank">We would love to hear your feedback on the tutorial, whether you did it in the classroom or online!</a>

<ul class="social-icons">
	<li>
		<h3>
			<a href="https://twitter.com/our_codingclub" target="_blank">&nbsp;Follow our coding adventures on Twitter! <i class="fa fa-twitter"></i></a>
		</h3>
	</li>
</ul>

### &nbsp;&nbsp;Subscribe to our mailing list:
<div class="container">
	<div class="block">
        <!-- subscribe form start -->
		<div class="form-group">
			<form action="https://getsimpleform.com/messages?form_api_token=de1ba2f2f947822946fb6e835437ec78" method="post">
			<div class="form-group">
				<input type='text' class="form-control" name='Email' placeholder="Email" required/>
			</div>
			<div>
                        	<button class="btn btn-default" type='submit'>Subscribe</button>
                    	</div>
                	</form>
		</div>
	</div>
</div>
```

### General stylistic points

Bold text can be used to draw attention to an important action point using `__`, but don't overdo it:

```
__Copy and paste the code below into your script:__
```

<a name="work_html"></a>

## Adding a tutorial to `work.html`

In `work.html` you should find a series of repeated blocks of code, each denoting a tutorial listed on the website. Add your own tutorial by first looking for this sequence of html tags:

```html
			</div>
		</div>
	</a>
</li>
```

then add the code below after that set of html tags: 

```html
<li class="mix Rbasics Markdown">  
     <a href="https://ourcodingclub.github.io/2017/01/16/piping.html">
           <img src="{{ site.baseurl }}/img/portfolio/work1.jpg" alt="">
                 <div class="overly">
                      <div class="position-center">
                            <h2>Your tutorial title</h2>
                            <p>Your tutorial subtitle</p>
                       </div>
                  </div>
       </a>
</li>
```

Change `<li class="mix Rbasics Markdown">` to reflect the categories you want the tutorial to be featured in. Categories include `Rbasics`, `Github`, `Dataform` (Data formatting), `Datavis` (Data visualisation), `Modelling`, `Markdown`, and Shiny. Remember not to add any commas between categories and keep `mix` in the code.

Change `<a href="https://ourcodingclub.github.io/2017/01/16/piping.html">` to reflect the name of your own tutorial, changing the date and tutorial name to match that of your `.md` file.

Change the thumbnail image for your tutorial (`<img src="{{ site.baseurl }}/img/portfolio/work1.jpg" alt="">`). You can choose one of the already uploaded ones (navigate to the img/portfolio folder to view them and change the file name according to the one you want), or you can also upload your own in the portfolio folder.

Change `<h2>Your tutorial title</h2>` to mirror the title of your tutorial.
 
Change `<p>Your tutorial subtitle</p>` to mirror the subtitle of your tutorial.

<a name="readme"></a>

## Creating a `README.md` for your tutorial resources repository on github

Below is an example `README.md` that you can use to make your own.

```
Using R to produce map figures and display spatial data

This repository contains the files necessary to complete the Coding Club Maps tutorial - you can check it out at:
https://ourcodingclub.github.io/2016/11/25/maps_tutorial.html

The bird data (`Gyps_rueppellii_GBIF.csv`) were downloaded from the Global Biodiversity Information Facility (GBIF) https://gbif.org

`ggmap_Cheatsheet.pdf` was downloaded from the National Centre for Ecological Analysis and Synthesis (NCEAS)
https://www.nceas.ucsb.edu/~frazier/RSpatialGuides/

For more Coding Club tutorials and resources, please see 
https://ourcodingclub.github.io/

We would love to hear your feedback on this tutorial, whether you did it in the classroom or online
<SURVEY_MONKEY_LINK>

This work is licensed under a [Creative Commons Attribution-ShareAlike 4.0 International License](https://creativecommons.org/licenses/by-sa/4.0/).

[![License: CC BY-SA 4.0](https://licensebuttons.net/l/by-sa/4.0/80x15.png)](https://creativecommons.org/licenses/by-sa/4.0/)
```
__If you have any questions, please get in touch with Gergana gndaskalova@gmail.com.__

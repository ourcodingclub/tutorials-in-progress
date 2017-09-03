# Guide to publishing tutorials/blog posts on the Coding Club website
### https://ourcodingclub.github.io/

## Publishing a tutorial

Thanks for your interest in Coding Club and your contribution to the advancement of quantitative skills! Please follow the following guide when preparing your tutorial and feel free to contact gndaskalova@gmail.com should you have any questions or issues.

1. Register on Github and ask Gergana to add you to Coding Club's organisational account

2. Create a new branch of the `ourcodingclub.github.io` repository, giving the branch a sensible name related to your blog post. You can check out our Github tutorial if you haven't used Github before. If you don't want to be creating a local (i.e. on your computer) copy of the Coding Club repo, you can just register on Github and once you have privileges for the Coding Club account, you can navigate to e.g. the <a href="https://github.com/ourcodingclub/ourcodingclub.github.io/tree/master/_posts">`_posts`</a> folder online and upload your `.md` file by clicking on `Upload file`.

3. Using your favourite text editor (e.g. Atom, TextEdit, Notepad, Vim, Sublime), create a tutorial using the <a href="#style">style guide below</a> and existing tutorials for reference. 

4. Give the file a `.md` file extension and name it following this style `2017-02-28-github.md`, making sure that the date corresponds with the one given in the `date:` section of the header material in the tutorial file. This date should be approximately 4 days before the tutorial is taught in class.

5. Upload the tutorial to your branch of `ourcodingclub.github.io` in the `_posts` folder

6. Upload any images to `ourcodingclub.github.io/img`, At the minimum a tutorial should include a tutorial header banner image using `tutheaderbl.png` as a template, remember to give sensible file names.

7. Upload any extra materials like datasets, cheatsheets, example scripts etc. to a sensibly named repository in the coding club github root directory, e.g. `CC-Modelling`, remember to add a `README.md`, <a href="#readme">see below for more info</a>.

8. Add a link to your tutorial in `work.html`, <a href="#work_html">see below for more info</a>. 

9. Create a pull-request for your branch to be merged with the master branch. 

<a name="style"></a>

## Style Guide

### Header Material

This material should appear at the top of every tutorial.md file. It is important to use the same `date:` as the one in the `.md` tutorial filename. This date should be approximately 4 days before the tutorial is due to be taught in class, so that email recipients can check out the tutorial before it is run in class. The `title:` and `subtitle:` should be identical to that which is written on the `tutheader_tutname.png` banner image for that tutorial:

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

First level subheadings should be denoted by `###` and should contain the same text as the Tutorial Aim which links to it. All first level subheadings should be preceded by an internal link, linking it to a given Tutorial Aim. Second level subheadings should be denoted by `####`. Third level subeadings and so on should be avoided:

```
<a name="sections"></a>

### 1. Organising scripts into sections

#### Collapsing sections

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

### Tables

Please format all tables using html, not markdown, using the following style info. Each `<tr>` block represents one row, with each `<th>` block representing one column. <a href="http://www.tablesgenerator.com/html_tables" target="_blank">http://www.tablesgenerator.com/html_tables</a> is a decent html table generator if you can't be bothered typing this all out manually:

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

### Shiny apps and other embedded material
Shiny apps and other similar embeddable material can be placed in an `iframe`, adjusting the height and width as needed to make it look sensible. Avoid making the user scroll through the app if possible by adjusting the height and width:

```
<iframe src="EMBEDDABLE_URL" style="border:none; width:1000px; height:550px;"></iframe>
```

### Web Links

Please format all hyperlinks using html, not markdown, in the following format:

```
<a href="FULL_LINK" target="_blank">DESCRIPTION OF LINK TO APPEAR AS TEXT</a>

```

### Image Links

Please format all image links using html, not markdown, in the following format. Adjust the `width:` argument so the image is sensibly sized:

```
<center> <img src="{{ site.baseurl }}/img/IMAGE_NAME.png" alt="Img" style="width: 800px;"/> </center>
```

### Footer Material

This material should be added to the end of every tutorial. Replace `INSERT_SURVEY_LINK` with the actual URL to a Survey Monkey survey created using the Coding Club account. The top lines of this section can be used to list acknowledgements and important links, but keep this to a minimum:

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

then add the code below after that set of html tags. 

Change `<li class="mix Rbasics Markdown">` to reflect the categories you want the tutorial to be featured in. Categories include `Rbasics`, `Github`, `Dataform` (Data formatting), `Datavis` (Data visualisation), `Modelling`, `Markdown`, and Shiny. Remember not to add any commas between categories and keep `mix` in the code.

Change `<a href="https://ourcodingclub.github.io/2017/01/16/piping.html">` to reflect the name of your own tutorial, changing the date and tutorial name to match that of your `.md` file.

Change the thumbnail image for your tutorial (`<img src="{{ site.baseurl }}/img/portfolio/work1.jpg" alt="">`). You can choose one of the already uploaded ones (navigate to the img/portfolio folder to view them and change the file name according to the one you want), or you can also upload your own in the portfolio folder.

Change `<h2>Your tutorial title</h2>` to mirror the title of your tutorial.
 
Change `<p>Your tutorial subtitle</p>` to mirror the subtitle of your tutorial.

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

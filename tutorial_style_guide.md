
## Header Material

This material should appear at the top of every tutorial. It is important to use the same date at the start of the `.md` file as is listed in the `date:` section of the tutorial. This date should be approximately 4 days before the tutorial is due to be taught in class. The `title:` and `subtitle:` should be identical to that which is written on the `tutheader.png` banner image for that tutorial:

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

## Introduction Material

A tutorial should be broken down into tangible aims. Each aim should be in the form of an action where possible ('ing' words, learning, understanding, organising etc.). Each aim should be represented by a subheading in the tutorial with the same name where possible:

```
### Tutorial Aims:

#### <a href="#sections"> 1. Organising scripts into sections</a>

#### <a href="#syntax"> 2. Following a coding syntax etiquette</a>
```

## Subheadings

First level subheadings should be denoted by `###` and should contain the same text as the Tutorial Aim which links to it. All first level subheadings should be preceded by an internal link, linking it to a given Tutorial Aim. Second level subheadings should be denoted by `####`. Third level subeadings and so on should be avoided:

```
<a name="sections"></a>

### 1. Organising scripts into sections

#### Collapsing sections

Some text

<a name="syntax"></a>

### 2. Following a coding syntax etiquette
```

## Referring to code and GUI elements:

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

## Tables

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

## Shiny apps and other embedded material
All Shiny apps and other similar embeddable material can be placed in an `iframe`, adjusting the height and width as needed to make it look sensible. Avoid making the user scroll through the app if possible by adjusting the height and width:

```
<iframe src="EMBEDDABLE_URL" style="border:none; width:1000px; height:550px;"></iframe>
```

## Web Links

Please format all hyperlinks using html, not markdown, in the following format:

```
<a href="FULL_LINK" target="_blank">DESCRIPTION OF LINK TO APPEAR AS TEXT</a>
```

## Image Links

Please format all image links using html, not markdown, in the following format. Adjust the `width:` argument so the image is sensibly sized:

```
<center> <img src="{{ site.baseurl }}/img/IMAGE_NAME.png" alt="Img" style="width: 800px;"/> </center>
```

## Footer Material

This material should be added to the end of every tutorial. Replace `INSERT_SURVEY_LINK` with the actual URL to a Survey monkey survey created using the Coding Club account. The top lines of this section can be used to list acknowledgements and important links, but keep this to a minimum:

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
				<input type='text' class="form-control" name='Email' placeholder="Email">
			</div>
			<div>
                        	<button class="btn btn-default" type='submit'>Subscribe</button>
                    	</div>
                	</form>
		</div>
	</div>
</div>
```

## General stylistic points

Bold text can be used to draw attention to an important point using `__`, but don't overdo it:

```
__BOLD TEXT IS LOUD__
```


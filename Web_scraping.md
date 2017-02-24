---
layout: post
title: Web Scraping
subtitle: Retrieving useful information from web pages
date: 2016-11-24 16:00:00
author: John
meta: "Webscraping"
---
<div class="block">
	<center>
		<img src="{{ site.baseurl }}/img/tutheader_webscraping.jpg" alt="Img">
	</center>
</div>

### Tutorial Aims:

#### 1. Learn how to isolate and retrieve data from a html web page

#### 2. Learn how to download multiple web pages using R

#### 3.


### Steps:

#### <a href="#download">1. Download the relevant packages </a>

#### <a href="#data">2. Download a `.html` web page  </a>

#### <a href="#import">3. Import a `.html` into R  </a>

#### <a href="#locate">4. Locating useful data using `grep` and regular expressions</a>

#### <a href="#multiple">5. Importing multiple web pages, fun with `lapply` </a>

Open up a new R Script where you will be adding the code for this tutorial. All the resources for this tutorial, including some helpful cheatsheets can be downloaded from [this repository](https://github.com/ourcodingclub/TESTEST) Clone and download the repo as a zipfile, then unzip and set the folder as your working directory by running the code below, or clicking `Session/Set Working Directory/Choose Directory` from the RStudio menu.

Web scraping refers to the action of extracting data from a web page using a computer program, in this case we will use R. Other popular command line interfaces that can perform similar actions are [`wget`](https://www.gnu.org/software/wget/) and [`curl`](https://github.com/curl/curl).

<a name="download"></a>

## Download the relevant packages

``` r
install.packages("rvest") # To import a html file
install.packages("")

library(rvest)
```

<a name="data"></a>

## Download a `.html` web page

The simplest way to download a web page is to save it as a `.html` file to your working. This can be accomplished in most browsers by clicking _`File -> Save as...`_ and saving the file type to `Webpage, HTML Only` or something similar. Here are some examples for different browsers Operating System combinations:

### Microsoft Windows - Internet Explorer

<img src="{{ site.baseurl }}/img/Explorer_Save.jpg" alt="Img">

### MacOS - Safari

<img src="{{ site.baseurl }}/img/Safari_Save.jpg" alt="Img">

### Microsoft Windows - Google Chrome

<img src="{{ site.baseurl }}/img/Chrome_Save.jpg" alt="Img">

Download the IUCN Red List information for _Aptenogytes forsteri (Emperor Penguin) from http://www.iucnredlist.org/details/22697810/0 using the above method.

## Importing `.html` into R

The file can then be imported into R as a large vector using the following code:

```r
Penguin_html <- readLines("Aptenodytes forsteri (Emperor Penguin).html")
```

Each string in the vector is one line of the original `.html` file.

## Isolating useful information using `grep()` and `gsub()`

In this example we are going to build a data frame of different species of penguin and gather data on their IUCN status and when the assessment was made, so we will have a data frame that looks something like this:

| Species                 | Common Name       | IUCN Status | Assessment Date |
|-------------------------|-------------------|-------------|-----------------|
| Aptenodytes forsteri    | Emperor Penguin   | Near Threatened          | 2016-10-01      |
| Aptenodytes patagonicus | King Penguin      | Least Concern          | 2016-10-01      |
| ...                     | ...               | ...         | ...             |
| Spheniscus mendiculus   | Galapagos Penguin | Endangered          | 2016-10-01      |

Open the IUCN web page for the Emperor Penguin in a web browser, you should see that the species name is next to some other text `Scientific Name:`. We can use this "anchor" to find the rough location of the species name:

```r
grep("Scientific Name:", Penguin_html)
```

This tells us that `Scientific Name:` appears once in the vector, on string 132. We can search around string 132 to find the species name:

```r
Penguin_html[131:135]
```

This displays the contents of our subsetted vector:

```r
[1] "<tr>"
[2] "  <td class=\"label\"><strong>Scientific Name:</strong></td>"
[3] "  <td class=\"sciName\"><span class=\"notranslate\"><span class=\"sciname\">Aptenodytes forsteri</span></span></td>"
[4] "</tr>"
[5] ""
```

`Aptenoydes forsteri`  is on line 133, wrapped in a whole load of html tags. Now we can check and isolate the exact piece of text we want, removing all the unwanted information:


```r
# Isolate the line containing the scienific name.
grep("Scientific Name:", Penguin_html)
Penguin_html[131:135]
Penguin_html[133]

# Isolate line
species_line <- Penguin_html[133]

## Pipes to grab the text and get rid of unwanted information like html tags
species_name <- species_line %>%
  gsub("<td class=\"sciName\"><span class=\"notranslate\"><span class=\"sciname\">", "", .) %>% # Remove leading html tag
  gsub("</span></span></td>", "", .) %>% # Remove trailing html tag
  gsub("^\\s+|\\s+$", "", .) # Remove whitespace
species_name
```

We can do the same for common name:

```r
grep("Common Name", Penguin_html)
Penguin_html[130:160]
Penguin_html[150:160]
Penguin_html[151]

common_name <- Penguin_html[151] %>%
gsub("<td>", "", .) %>%
  gsub("</td>", "", .) %>%
  gsub("^\\s+|\\s+$", "", .)
common_name
```


The same for IUCN category:

```r
grep("Red List Category", Penguin_html)
Penguin_html[179:185]
Penguin_html[182]

red_cat <- gsub("^\\s+|\\s+$", "", Penguin_html[182])
red_cat
```

The same for Date of Assessment:

```r
grep("Date Assessed:", Penguin_html)
Penguin_html[192:197]
Penguin_html[196]

date_assess <- Penguin_html[196] %>%
	gsub("<td>", "",.) %>%
	gsub("</td>", "",.) %>%
	gsub("\\s", "",.)
date_assess
```

We can create the start of our data frame by concatenating the vectors:

```r
iucn <- data.frame(species_name, common_name, red_cat, date)
```



## Importing multiple web pages

The above example only used one file, but the real power of web scraping comes from being able to repeat these actions over a number of web pages to build up a larger data set.

We can import many web pages from a list of URLs generated by searching the IUCN red list for Penguin. Go to http://www.iucnredlist.org/, search for "penguin" and download the resulting web page as a html document.

Now we can download and import a list of web pages:


Import `Search Results.html`:
```r
search_html <- readLines("Search Results.html")
```

Create a list of html lines containing URLs:
```r
line_list <- grep("<a href=\"/details", search_html)
link_list <- search_html[line_list]
```

Clean up the lines so only the URL is left:
```r
species_list <- link_list %>%
  gsub('<a href=\"', "http://www.iucnredlist.org", .) %>%
  gsub('\".*', "", .) %>%
  gsub('\\s', "",.)
```

Clean up the lines so only the species name is left:
```r
file_list_grep <- link_list %>%
  gsub('.*sciname\">', "", .) %>%
  gsub('</span></a>.*', ".html", .)
file_list_grep
```

Use `mapply` to download each URL and place it in the working directory:
```r
mapply(function(x,y) download.file(x,y), species_list, file_list_grep)
```

Import each of the downloaded html files based on its name:
```r
penguin_html_list <- lapply(file_list_grep, readLines)
```

Now we can do similar actions to the first part of the tutorial to loop over each of the vectors in `penguin_html_list` and build our data frame:

Search for "Scientific Name:" and store the line number for each web page in a list:
```r
sci_name_list_rough <- lapply(penguin_html_list, grep, pattern="Scientific Name:")
sci_name_list_rough # 132
penguin_html_list[[2]][133] # +1
```

Convert the list into a simple vector:
```r
sci_name_unlist_rough <- unlist(sci_name_list_rough) + 1
```

Retrieve lines containing scientific names from each web page entry in turn and store in a vector:
```r
sci_name_line <- mapply('[', penguin_html_list, sci_name_unlist_rough)
```

Remove the html tags and whitespace around each entry:
```r
## Clean html
sci_name <- sci_name_line %>%
  gsub(pattern = "<td class=\"sciName\"><span class=\"notranslate\"><span class=\"sciname\">",
         replacement = "") %>%
  gsub(pattern = "</span></span></td>", replacement = "") %>%
  gsub(pattern = "^\\s+|\\s+$", replacement = "")
```

The same for "Common Name":
```r
# Find common name
## Isolate line
common_name_list_rough <- lapply(penguin_html_list, grep, pattern = "Common Name")
common_name_list_rough #146
penguin_html_list[[1]][151]
```

```r
common_name_unlist_rough <- unlist(common_name_list_rough) + 5
```

```r
common_name_line <- mapply('[', penguin_html_list, common_name_unlist_rough)
```

```r
common_name <- common_name_line %>%
  gsub(pattern = "<td>", replacement = "") %>%
  gsub(pattern = "</td>", replacement = "") %>%
  gsub(pattern = "^\\s+|\\s+$", replacement = "")
```

Red list category:
```r
red_cat_list_rough <- lapply(penguin_html_list, grep, pattern = "Red List Category")
red_cat_list_rough # Different locations
penguin_html_list[[16]][186]
```

```r
red_cat_unlist_rough <- unlist(red_cat_list_rough) + 2
red_cat_unlist_rough
penguin_html_list[[2]][187]
```

```r
red_cat_line <- mapply(`[`, penguin_html_list, red_cat_unlist_rough)
red_cat_list <- gsub("^\\s+|\\s+$", "", red_cat_line)
```

Date assessed:
```r
date_list_rough <- lapply(penguin_html_list, grep, pattern = "Date Assessed:")
date_list_rough # Different locations
penguin_html_list[[18]][200]
date_unlist_rough <- unlist(date_list_rough) + 1
```

```r
date_line <- mapply('[', penguin_html_list, date_unlist_rough)
```

```r
date_list <- date_line %>%
  gsub("<td>", "",.) %>%
  gsub("</td>", "",.) %>%
  gsub("\\s", "",.)
```

Then we can combine the vectors into a data frame:
```r  
penguin_df <- data.frame(species_name_vec, common_name_list, red_cat_list, date_list)
penguin_df
```

# Guide to publishing tutorials/blog posts on the Coding Club website
### https://ourcodingclub.github.io/

- Register on Github and ask Gergana to add you onto Coding Club’s organisational account.

- Open your favourite plain text editor to create your blog post (I use Atom).

- Copy and paste the front matter at the start of your file – this is how Github Pages (and Jekyll, the static website generator) recognises your file as a blog post. The --- at the start and end of the code is what tells Jekyll that this is the front matter.

```md
---
layout: post
title: Your Title
subtitle: Your subtitle
date: 2016-10-17 21:11:27  # Type in the date and time of the post – it needs to be in this format.
author: Your name
meta: "Prep and organisation" #The post category, change as appropriate, e.g. “Tutorials” (you need the “”)
---
```

- Write your blog post and save it as a Markdown file (.md). In the tutorials-in-prep repo you can find a template <a href="https://github.com/ourcodingclub/tutorials-in-progress/blob/master/template_tutorial_footer">for the footer (end bit)</a> of the tutorial blog post that you can copy at the end of your tutorial to maintain consistency between the different posts. You can check out the published tutorials in the `ourcodingclub.github.io/_posts` folder to see what structure we are using in general, feel free to copy that (i.e. image header at the start, followed by tutorial aims).

You can use the Markdown syntax to add code chunks, images, change font size, etc. You can also use HTML code. You can find some example HTML code below. For tips on writing using Markdown, please see <a href="https://ourcodingclub.github.io/2016/11/24/rmarkdown-1.html">John's Markdown tutorial.</a> You can find the blank header image for tutorials in the `ourcodingclub.github.io/img` folder, called `tutheaderbl.png`. Add in the title and subtitle for your tutorial in Paint / Photoshop - use bold Arial 48 for the title and regular Arial 30 for the subtitle, centre the textbox both vertically and horizontally to maintain consistency.

```html
<b>You can also follow us on <a href="https://twitter.com/our_codingclub">Twitter</a>!</b>
#Adding a hyperlink and making the text bold.

<center><img src="http://i212.photobucket.com/albums/cc93/_avocet/_avocet115/poster.png" alt="Poster" style="width: 700px;"/></center>
#Adding and centering an image that you have uploaded on photobucket, Google Drive, etc. beforehand, and adjusting how wide the image appears.

<img src="{{ site.baseurl }}/img/yourimagename.png" alt="Img">
#Adding an image you have uploaded on our Github repository – navigate to the folder “img” and upload your file there. It’s easier if your image is already in the size you want it to appear in on the website.
```

- You can create a new repository on Coding Club’s account for all the files students need to complete your tutorial. Upload the files in the repository you just created. You should include the link to the repository in your blog post, so students can go there and download the files. Add in text about forking the repo on their own Github account (and insert link to our Github tut for more details https://ourcodingclub.github.io/2017/02/27/git.html), as an alternative to downloading and unzipping the files.

- Save your .md file following this style `2017-02-28-github.md`, with the date corresponding with the date the tutorial will be taught, navigate to the `_posts` folder and upload your .md file there.

If you are publishing a tutorial, you also need to add the link to it on the Tutorials website page https://ourcodingclub.github.io/tutorials/
1.	In the Coding Club website repository, open the work.html file, click edit file.

2.	You will see the existing tutorials – there is an image that acts as a hyperlink leading to the blog post with the tutorial.

3.	To add in yours, you need to copy and paste this code  at the end of the code for the existing tutorials (you can copy it directly from the work.html file, I am pasting it here to explain what each line does):


```html
<li class="mix Rbasics">  # Here you add in your tutorial category, you can change “Rbasics” (keep the “mix” in) with Github, Dataform (standing for Data formatting), Datavis (standing for Data visualisation), Modelling, Markdown, or Shiny.
     <a href="the html link to your blog post with the tutorial">
           <img src="{{ site.baseurl }}/img/portfolio/work1.jpg" alt="">  # The thumbnail image for your tutorial, you can choose one of the already uploaded ones (navigate to the img/portfolio folder to view them and change the file name according to the one you want), or you can also upload your own in the portfolio folder.
                 <div class="overly">
                      <div class="position-center">
                            <h2>Your tutorial title</h2>
                            <p>Your tutorial subtitle</p>
                       </div>
                  </div>
       </a>
</li>
```

- Commit the changes – you have now added the link to your tutorial blog post to the tutorial page!

__If you have any questions, feel free to email Gergana gndaskalova@gmail.com.__

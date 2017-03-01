---
layout: post
title: From distributions to linear models
subtitle: Getting comfortable with the basics of statistics modelling
date: 2017-02-28 08:00:00
author: Gergana
meta: "Tutorials"
---

<div class="block">
	<center>
		<img src="{{ site.baseurl }}/img/tutheaderlm.png" alt="Img">
	</center>
</div>

### Tutorial Aims:

#### <a href="#distributions"> 1. Get familiar with different data distributions</a>

#### <a href="#linear"> 2. Practice linear models</a>

#### <a href="#generalised"> 2. Practice generalised linear models</a>

As you are setting out to answer your research questions, often you might want to know what is the effect of X on Y, how does X change with Y, etc. The answer to "What statistical analysis are you going to use?" will probably be a model of some sort. A model in its simplest forms looks like: `temp.m <- lm(soil.temp ~ elevation)` - i.e. we are trying to determine the effect of elevation on soil temperature. A slightly more complicated model might look like: `skylark.m <- lm(abundance ~ treatment + farm.area, family = poisson, data = skylarks)` - here you are modelling `abundance`, the response variable, as a function of `treatment` (e.g. a categorical variable describing different types of farms) and `farm.area` (i.e. the size of each farm on which abundance data were collected) - those are your explanatory variables. The `family` argument refers to the distribution of the data, in this case `abundance` represents count zero-inflated data, for which a Poisson distribution is suitable. The `data` argument refers to the dataframe from which the variables we are studying come.

We will talk more about different data distributions later, until then, go to <a href = "INSERT LINK">the repository for this tutorial</a>, fork it to your own Github account, clone the repository on your computer and start a version-controlled project in RStudio. For more details on how to do this, please check out our <a href = "https://ourcodingclub.github.io/2017/02/27/git.html"> Intro to Github for version control</a> tutorial.

Open the `Modelling_script.R` file and add in your details. Before we start running our models, here is a brief summary of the data distributions you might encounter most often.

### Different data distributions

The distribution of your data is most-readily assessed through a histogram - take a look at the histograms below to get an idea of the different types of data distribution.

!!!!!!!!!!!!!!!!!!INSERT IMAGES!!!!!!!

<a name="distributions"></a>

```
|   Family   | Suitability |
|:-----------|:------------|
| Gaussian   |     |
| Poisson    |     |
| Binomial   |     |
| Negative binomial   |     |
```

Choosing the right distribution for your analysis is an important step about which you should think carefully - it could be frustrating to spend tons of time running models, plotting their results and writing them up only to realise that all along you should have used e.g. a Poisson distribution instead of a Gaussian one.

Another important to consider aspect of modelling is how many terms, i.e. explanatory variables, you want your model to include. It's a good idea to draft out your model structure before you have started thinking about exactly which R packages you will use, running different types of models, etc. Think about what it is you want to examine and what are the potential confounding variables, i.e. what else might influence your response variable, aside from the explanatory variable you are most interested in? Here is an example model structure:

```r
skylark.m <- lm(abundance ~ treatment + farm.area + latitude + longitude + visits)
```

Here we are chiefly interested in the effect of treatment - does skylark abundance vary between the different farm treatments? This is the research question we might have set out to answer, but we still need to acknowledge that farm treatment type is not the only factor influencing abundance. Based on our ecological understanding, we can select other potentially confounding variables - for example skylark abundance will most likely be higher on larger farms - we need to account for that. Additionally, where farms are located might have an effect, thus we are adding `latitude + longitude`. Imagine your experimental design didn't go exactly as you planned - you meant to visit all farms three times to collect data, but some farms you managed to visit only twice. Ignoring this would weaken your final results - is abundance different / the same because the treatment has no / an effect, or because there were differences in study effort? To test that, you can include a `visits` term examining the effect of number on visits on abundance. Some might say this model is very complex, and they would be right - there are a lot of terms in it! A simple model is usually prefered to a complex model, but if you have strong reasons for including a term in your model, then it should be there. So think carefully about your model structure - once you know the variables whose effects you want to study, and the variables whose effects you might need to account for, you can move onto running your models.

We will now explore a few different types of models - here we will provide a brief introduction, and you can find more tutorials on the following links !!!!!!!!!!!!INSERT LINKS!!!!!!!!!!!!!!!!!!

<a name="linear"></a>

### Practicing linear models

#### Visualising model outputs

### Practicing generalised linear models

#### A model with a Poisson distribution

#### Visualising model outputs

#### A model with a binomial distribution

#### Visualising model outputs

<b> We have now covered the basics of modelling - in our next tutorial we will look at mixed effects models, which are used more and more within ecology and environmental science. Until then, here are some more links for tutorials that could help you further your knowledge of linear and generalised linear models:

!!!!!!!!!! INSERT LINKS !!!!!!!!!!!!!!

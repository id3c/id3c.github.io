---
layout: post
title: "MathJax with Jekyll"
date: 2014-02-16
categories: opinion
tags: [resources, jekyll]
image: http://gastonsanchez.com/images/blog/mathjax_logo.png
---

One of the rewards of switching my website to [Jekyll](http://jekyllrb.com/) is the
ability to support **MathJax**, which means I can write LaTeX-like equations that get
nicely displayed in a web browser, like this one \\( \sqrt{\frac{n!}{k!(n-k)!}} \\) or
this one \\( x^2 + y^2 = r^2 \\).

<!-- more -->

<img class="centered" src="https://www.mathjax.org/badge/mj-logo.svg" />

### What's MathJax?

If you check MathJax website [(www.mathjax.org)](http://www.mathjax.org/) you'll see
that it *is an open source JavaScript display engine for mathematics that works in all
browsers*.


### How to implement MathJax with Jekyll

I followed the instructions described by Dason Kurkiewicz for
[using Jekyll and Mathjax](http://dasonk.github.io/blog/2012/10/09/Using-Jekyll-and-Mathjax/).

Here are some important details. I had to modify the Ruby library for Markdown in
my ```_config.yml``` file. Now I'm using redcarpet so the corresponding line in the
configuration file is: ```markdown: redcarpet```

To load the MathJax javascript, I added the following lines in my layout ```page.html```
(located in my folder ```_layouts```)

{% highlight r %}
<script type="text/javascript"
    src="http://cdn.mathjax.org/mathjax/latest/MathJax.js?config=TeX-AMS-MML_HTMLorMML">
</script>
{% endhighlight %}

Of course you can choose a different file location in your jekyll layouts.


### A Couple of Examples

Here's a short list of examples. To know more about the details behind MathJax, you can
always checked the provided documentation available at
[http://docs.mathjax.org/en/latest/](http://docs.mathjax.org/en/latest/)

I'm assuming you are familiar with LaTeX. However, you should know that MathJax does not
have the exactly same behavior as LaTeX. By default, the **tex2jax** preprocessor defines the
LaTeX math delimiters, which are ```\\(...\\)``` for in-line math, and ```\\[...\\]``` for
displayed equations. It also defines the TeX delimiters ```$$...$$``` for displayed
equations, but it does not define ```$...$``` as in-line math delimiters. Fortunately,
you can change these predefined specifications if you want to do so.

Let's try a first example. Here's a dummy equation:

$$a^2 + b^2 = c^2$$

How do you write such expression? Very simple: using **double dollar** signs

{% highlight r %}
$$a^2 + b^2 = c^2$$
{% endhighlight %}

To display inline math use ```\\( ... \\)``` like this ```\\( sin(x^2) \\)``` which gets
rendered as \\( sin(x^2) \\)


Here's another example using type ```\mathsf```

{% highlight r %}
$$ \mathsf{Data = PCs} \times \mathsf{Loadings} $$
{% endhighlight %}

which gets displayed as

$$ \mathsf{Data = PCs} \times \mathsf{Loadings} $$

Or even better:

{% highlight r %}
\\[ \mathbf{X} = \mathbf{Z} \mathbf{P^\mathsf{T}} \\]
{% endhighlight %}

is displayed as

\\[ \mathbf{X} = \mathbf{Z} \mathbf{P^\mathsf{T}} \\]

If you want to use subscripts like this \\( \mathbf{X}\_{n,p} \\) you need to scape the
underscores with a backslash like so ``` \mathbf{X}\_{n,p} ```:

{% highlight r %}
$$ \mathbf{X}\_{n,p} = \mathbf{A}\_{n,k} \mathbf{B}\_{k,p} $$
{% endhighlight %}

will be displayed as

\\[ \mathbf{X}\_{n,p} = \mathbf{A}\_{n,k} \mathbf{B}\_{k,p} \\]



为治疗菜种疾病，研制了甲、乙两种新药，希望知道哪种新药更有效，为此造行动物试验。试验方策如下每一轮选取两只白鼠对药效进行对比试验。对于两只白鼠，随机选一只葹以甲药，另一只葹以乙药。一轮的治疔结果得出后，再安排下一轮试验。当其中一种药治愈的白鼠比另一种药治愈的白鼠多4只时，就停止试验，并认为治愈只欻多的药更有效。为了方便描述问题，约定：对于每轮试验，若施以甲药的白鼠治念且施以乙药的白鼠未治愈則甲药得1分，乙药得-1分；若施以乙药的白鼠治愈且施以甲药的白鼠未治愈则乙药得1分，甲药得-1分：若都治愈或都未治愈則两种药均得0分。甲、乙两种药的治愈率分別记为$\alpha$和$\beta$，一轮试验中甲药的得分记为$X$ 

(1)求$X$的分布列；
(2)若甲药、乙药在试验开始时都默予4分，$p_i(i=0,1,\cdots ,8)$表示“甲药的计得分为$i$时，最终认为甲药比乙药更有效”的概率，则$p_0=0$，$p_8=1$，$p_i=a p_{i-1}+b p_i+c p_{i-1},(i=1,2,\cdots ,7)$，其中$a=P(X=-1)$,$b=P(X=0)$,$c=P(X=1)$.假设$\alpha=0.5$,$\beta=0.8$ 
(i)证明：$\{p_{i+1}-p_i\}(i=0.1,2…,7)$为等比数列；
(ii)求$p_4$，并根据$p_4$的值解释这种试验方案的合理性.

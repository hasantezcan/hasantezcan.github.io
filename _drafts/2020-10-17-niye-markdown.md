---
layout: post
title: "Neymiş bu markdown"
author: "Hasan Tezcan"
categories: blog
tags: [markdown]
image: "/markdown.png"
date:   2020-10-17
---

## What is this "Markdown"

I think you are familiar with **HTML** (Hypertext markUP language). So we can call it his little brother **"MarkDOWN"**.

Markdown is the best quick notes tool in the world. He has easyest syntax you have ever met before. You can create Pre-render document with this. 

And he accept HTML elements inside of it!!

### Why we are not using Microsoft Word or other word like apps or just use .txt files?

Becouse word like apps works solver than markdown files. And markdown doc has own standarts. You can familer any docs writen by markdown after you usign markdown. 


**What about .txt ?**  
txt is so ugly :(

Markdown syntax is so basic any easy. You can learn it [**here**](https://link) easyily. We dont talk about it today. 

We will about advance markdown usage esspacialy on github.

Why I said like that. Why I declared github like that. Becouse github is not support CSS declartions and HTML posinions so we can't dance in mark down what ever we want. But! This is not stoped us! Becouse We are the GEEEK! So lets get start.!!!!

Okay what we got right now! And dont have?

Lets get start with images on github markdown styles,
You know the basic images usage in github like that!

```markdown
![image-alt-text](/image-path)
```

![image-alt-text](../assets/posts/markdown/giphy.gif)


Soo if we use like that. We got not centered not sizebale photos. So I don want it. And if I see on this some doc I having nervous breakdowns.

So how can we handle it!

It's so basic 

```html
<p align="center">
  <img alt="img-name" src="/path/image-name.png" width="300">
</p>
```
<p align="center">
  <img alt="img-name" src="../assets/posts/markdown/giphy.gif" width="300">
</p>

remember I told u in the first line this doc. **`"We can use HTML elements in markdown"`** so we did it like that. Perfect centerd iamges and we can resize it like that! 

But its not over yet! What we got more!!  
**`Caption`** What u said the caption yes thats insynly true!

```html
<p align="center">
  <img alt="imgName" src="/path/image-name.png" width="300">
  <br>
	<em style="color: grey">caption</em>
</p>
```

this is perfect images usage in github.
Hey guys I dont wanna see the docs fully ugly images in github again pls! This is the way and plase use it! 


Bunu dev'e at! 


dev.com 'da



----




<!-- basic title -->
## Title - Explanation
> [**link-name**](link)



<!-- side by side photo -->
<!-- https://gist.github.com/grocky/5d75af69b4f4c10304bf -->

| [![VideoBlocks](https://d1ow200m9i3wyh.cloudfront.net/img/assets/videoblocks/images/logo.png)](http://videoblocks.com)  | [![AudioBlocks](https://dtyn3c8zjrx01.cloudfront.net/img/assets/audioblocks/images/logo.png)](http://audioblocks.com) | [![GraphicStock](http://www.graphicstock.com/images/logo.jpg)](http://graphicstock.com) |
|:---:|:---:|:---:|
| http://videoblocks.com | http://audioblocks.com | http://graphicstock.com |

<!-- basic centered image -->
<p align="center">
  <img alt="img-name" src="/path/image-name.png" width="300">
</p>

<!-- basic centered image with caption -->
<p align="center">
  <img alt="imgName" src="/path/image-name.png" width="300">
  <br>
	<em style="color: grey">caption</em>
</p>


<!-- callout big -->
<div style="background-color: #f9f9fa; padding: 25px;">

</div>

<!-- callout mini -->
<div style="background-color: #f9f9fa; padding: 10px 25px 5px 25px;">

</div>


<!-- two image near to near -->

<div style="display: flex">
  <p align="center" style="padding: 10px">
    <img alt="img-name" src="/path/image-name.png" width="300">
    <br>
    <em style="color: grey">caption</em>
  </p>

  <p align="center">
    <img alt="img-name" src="/path/image-name.png" width="300">
    <br>
    <em style="color: grey">caption</em>
  </p>
</div>


<!-- image and caption with tables -->

<!-- https://stackoverflow.com/questions/19331362/using-an-image-caption-in-markdown-jekyll/60345387#60345387 -->

| ![space-1.jpg](http://www.storywarren.com/wp-content/uploads/2016/09/space-1.jpg) |
|:--:|
| *Space* |


https://github.com/nfl/react-helmet/blob/master/README.md



---


https://github.com/shd101wyy/markdown-preview-enhanced/blob/master/docs/customize-css.md


https://gist.github.com/roachhd/f83b31e7b48a76b79d97

https://stackoverflow.com/questions/51956361/custom-css-file-for-readme-md-in-a-github-repo

---

https://github.com/adam-p/markdown-here/wiki/Markdown-Cheatsheet


https://gist.github.com/lg0/2354062

https://duckduckgo.com/?q=cool+markdown+tricks&atb=v143-7__&ia=web&iai=r1-1&page=1&adx=prdsdc&sexp=%7B%22prodexp%22%3A%22b%22%2C%22prdsdexp%22%3A%22c%22%2C%22biaexp%22%3A%22b%22%2C%22direxp%22%3A%22b%22%7D

https://gist.github.com/joyrexus/16041f2426450e73f5df9391f7f7ae5f

https://grantwinney.com/cool-markdown-tricks-for-github/

https://github.com/grantwinney/BlogCodeSamples/tree/master/GitHubTipsTricks

https://jdhao.github.io/2020/06/01/markdown_writing_tricks/#how-to-color-text



==== 
Best markdown table generator 

https://tableconvert.com/
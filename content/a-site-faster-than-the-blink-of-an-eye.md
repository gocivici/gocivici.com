+++
categories = ["Web Development"]
date = "2016-09-29T00:00:00+00:00"
description = ""
image = "lol.png"
title = "Faster Than the Blink of an Eye"
type = "page"

+++


It has been 2 months since I published my project [Star Track](http://www.instructables.com/id/Star-Track-Arduino-Powered-Star-Pointer-and-Tracke/) on Instructables. Publishing one of my projects online was a big step for me, and the main reason for that was the feedback I got. While expecting no feedback at all, I got mostly feedback like this from various platforms:

<blockquote>
<ul>
<li>You can use a small NEMA 17 steppers. With 200steps/rev and the micro stepping features of the drivers, you can get a reasonably high precision.</li>
</ul>
</blockquote> 

<blockquote>
<ul>
<li>With A4988 drivers, you can move the steppers only with 4 pins saving another 4, so probably is enough with only one Arduino. Hope this helps and waiting for the V2 soon!!!</li>
</ul>
</blockquote>

After I published the project I put it under my desk as I always do, It was waiting there to be taken apart for future projects. But after the feedback I got, I decided to keep it. Because there was a ton of improvements to make.

While Publishing on Instructables got me good feedback, It was just the final product, with instructions on how to assemble it. Because this is what Instructables is for. It didn't include the hundreds of errors I got, the prototypes that failed, other hardware I used that did not perform well etc. This is why I decided to start a **Blog**. Where I will post problems I encounter during builds. Thoughts on projects, prototypes etc. Since posts will be mostly logs of my projects I called it **ProjectLog**.

## Starting a Blog

There are a lot of services like Wordpress, Blogger. That you can start a blog under 5 minutes. They are easy to use and you don't have to worry about the backend of your site. So why not use it? Here are a few reasons from my perspective:

### 1. Not Lightweight

Wordpress is a PHP based site(dynamic). PHP files will take more time to execute than HTML files. So it will take more time to load than a static website.

### 2. Customization

Customization of a Wordpress site needs a knowledge of the Wordpress framework itself to be able to modify the files.

I need a blog that is lightweight and since I'll only post project logs I don't need any other functionality. A blog with a theme I can edit, and easily Customize. this is where [static site generators](https://davidwalsh.name/introduction-static-site-generators) come in.

With static site generators, I can generate the blog on my desktop and upload it to various services like GitHub, Amazon, google. The website will be fast, secure and lightweight.

For a static site generator, I choose [Hugo](https://gohugo.io/). After you choose a theme and generate your site following the instructions your site is ready to deploy.

## Hosting on Amazon S3

Amazon s3 is great for storing files. It's cheap, fast, reliable and secure. What you may not know is that you can also host static websites on this platform.

hosting a static webpage is ridiculously cheap. S3 has a pay-as-you-use system. Even with a lot of users visiting your website you don't pay much. [Here is someone who served 100.000 users under 1 dollar with cloudFare distribution(more on this later)](http://blogging.alastair.is/how-i-served-100k-users-without-crashing-and-only-spent-0-32/) After following the [documentation](https://docs.aws.amazon.com/AmazonS3/latest/dev/WebsiteHosting.html) on Amazon, your static website is now available at something like:

```
your-bucket.s3-website.eu-central-1.amazonaws.com

```

If you want to use your own domain name as I do, you can follow [this guide on amazon route 53](http://docs.aws.amazon.com/gettingstarted/latest/swh/getting-started-configure-route53.html) and use route 53 as your dns service.

## CloudFront Distribution

When you deploy your site on Amazon S3 you have to choose a region that is near to you. This region will be the server that contains your website. Let's say you chose the region as Frankfurt. Your page will load very fast if requested in that region. If someone from the US opens your site. It will take 3-5 seconds (depending on your web page size) to load. This is why a cloud Distribution is useful.

A cloud distribution puts copies of files on servers all around the world(end points). If someone opens that file, It's served from the nearest server. And since the website we generated is static, It can be distributed around the world with CloudFront.

<div style="text-align:center; margin-bottom:20px;"><img src="https://docs.aws.amazon.com/gettingstarted/latest/swh/images/AWS_StaticWebsiteHosting_Architecture_4b.png"></div>

[Here](http://vvv.tobiassjosten.net/development/jekyll-blog-on-amazon-s3-and-cloudfront/) is also a helpful link.

### Conclusion

After the cloud distrubution setup the website will be reachable around the world under 1 second. And the monthly bill from amazon will not exceed 1 dollar(I hope).

test

test2
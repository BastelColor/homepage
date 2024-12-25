---
title: "Hugo - very useful"
summary: "About creation of this pages"
date: 2024-12-11
coverCaption: "かわいいです"
keywords: "謎"
showTableOfContents: true
showSummary: true


description: "HTMLメタデータです"

---

## About this article
This article was written for [KCS Advent Calendar 2024](URL "https://qiita.com/advent-calendar/2024/kcs/") when there were any spaces.

## I want to make website！
I wanted to make website、so I researched a lot, got some advice from KCS, with no result and my understandings...

So、I decided framework to make website by whether there are templates. And finally, I found [Hugo]({{< ref "https://gohugo.io/" >}})!

![Hugo](img/hugo.jpeg "Very useful")

## Setup, first
How to setup is different with each OS. One thing to note, you NEED to install Hugo Extended version, not just Hugo.
Detailed information for installation is [here](URL "https://gohugo.io/installation/"), so check your installation method. 

Next, setup your directory. you have to do is type this to console.

``` 
hugo new site homepage 
```

Yeah it is very easy. You can change `homepage` part to what you want for folder name.

As I mentioned, Hugo has lots of templates. Till you will use github pages, let's set up git. So, type this

```
cd homepage
git init
```

And all things will be OK. and you need to upload your project on github with

```
git add .
git commit -m "initialize"
git remote add origin https://github.com/<username>/<repo-name>.git
git push origin master
```

I think VSCode is much easier than CLI by the way.

Anyway, This site's theme is [Congo](URL "https://github.com/jpanther/congo"). I tried some themes and this was the best.

![Congo](img/screenshot.png "Easy to make good layout")

You will add theme with git's submodule usually, but Congo has original way to install. So check own installation when you try another themes.

You can install Congo theme with command below.

```
hugo mod init github.com/<username>/<repo-name>
```

In addition, make `config/_default/module.toml` file and write text below.

```
[[imports]]
path = "github.com/jpanther/congo/v2"
```

At last, this.
```
hugo server
```
With this command, you can make your website on Localhost server. On first run, hugo will automatically download and install files what you need for theme set on imports. So, run your server instantly when you finished setup.

This is all the way to setup your website.

## Other settings

If you use github pages for publish, it is useful that hugo's build settings on docs folder. So, write on `<directory>/hugo.toml` that 
```
publishDir = "docs"
```
This setting will change hugo to generate html files on `<directory>/docs/` when you run server.

In addition, you can add language settings by yourself. Initial setting is English, so if you wanna add Japanese, you have to make `languages.ja.toml` under `config/`, and write information as well.

These settings is explained very clear on Congo docs. [Here](URL "https://jpanther.github.io/congo/docs/") it is.

## Conclusion
Making website is very high level. But now, we have many useful tools. So let's make your own website!
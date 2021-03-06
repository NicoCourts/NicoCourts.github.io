---
layout: post
title: "Welcome to My Blog"
description: "An old (mostly out-of-date) post about how I originally created my website."
tags: coding
comments: true
---
No good blog would ever begin without a post about how I doubt anyone will ever actually read this. That's not completely true: I am sure my partner will read a couple and perhaps my mom will as well. 

This post is a bit of a mish-mash of some ideas that have been brewing in my head as I have been finishing up developing this site, so you'll forgive me if this one is a little fragmented. Hopefully I can isolate ideas more in future posts. 

I have phrased this as a question-and-answer page to help me write more clearly and to break up different ideas.

### Why a blog?
I spend a lot of time writing things these days (notes and emails, mostly) and I find myself enjoying it. I am not terribly surprised—I was always fairly good at composition and I really appreciate someone who is a good, clear communicator. I am far from perfect myself, but I see everything I write as a chance to better myself and to become a better at this all-vital skill.

It is this drive that plays a major role in my decision to teach as part of my career: there is something about taking ideas and digesting them and making them more understandable and palatable that really makes me excited. 

For the most part, this is an exercise in organizing my thoughts and processing things I see in the world around me. I warmly welcome anyone to come and read these things but I am not planning on writing this blog with anyone in particular in mind. If I can help or teach someone something along the way, I will just consider that to be a bonus. :)

### Why do it yourself?
Creating this website, the API underlying everything, and a desktop application to create posts was a ton of work (literally hundreds of hours) alongside my already busy schedule. I had to teach myself the programming languages [Go](https://golang.org/) and [Typescript](https://www.typescriptlang.org/) as well as learn how to use the frameworks [Angular](https://angular.io/), [Node.js](https://nodejs.org/en/), and [Electron](https://electronjs.org/) to create web applications and communicate between them. I even wrote my own API that I have used for this blog component (and for my wedding RSVPs).

*"But Nico," you proffer, "surely you could have used something like Facebook or Wordpress to handle all this nonsense for you!"* 

**Bah.** I am a techie at heart and I suppose I am a bit of a masochist in that I am not truly happy with something unless I have gone through the process of putting all the pieces together myself. I have built and rebuild my website using different technologies three times at this point (please let this one last for a while...), each time making things more intricate. I will say, though, that this time I feel reasonably good about what I have done. Things aren't perfect, but the experience is almost what I expect it to be.

### What did you do?
Quite a lot, but I'll do my best to say it quickly. First off, I learned how to develop websites in Angular and created my website with my CV and other static information. That took a while (there was a bit of a learning curve with Typescript and the framework itself) but I am pretty happy with how it turned out. 

I carved out a page called "blog" and just left it empty for a while while I patted myself firmly on the back.

The idea of modularity has been a huge driving force behind this project as before monolithic components were not easily manageable and would often force me to scrap the entire project rather than try to add in features. Thus the idea of creating an API for the blog was born. 

The idea is that I have a (standalone) service written in Go that is essentially a tiny webserver. It receives requests at prescribed routes and sends back JSON-encoded responses. The part of this that I am probably most proud of is that I was unhappy with the options I found readily online for performing authenticated queries to my API. So instead of using something that didn't do what I wanted, I just implemented RSA signing and verification of pseudorandom blobs as a form of authentication. My server generates these blobs ("nonces") and my personal computer signs these nonces with a private key. That way I can have publicly-exposed paths and private paths so that I can write apps that use it at will.

So then I had a website and a couple dummy posts in the database that were gobbled up by that "blog" page. We were getting somewhere.

Then the most frustrating part: a desktop application for composing (and otherwise managing) posts and images. My first idea was to use Angular again and just serve the page locally. I started composing things in Typescript but had trouble (especially accessing the file system (I realize now that I could have gotten around this)), so I gave it up for more familiar territory: Python. I got the backend of the app all up and running perfectly, but when it came to the UI I had trouble. I first tried to use a Python implementation of GTK+ and found the documentation to be too lacking for such an intricate system. So I used a package called `pywebview` that promised it would give me a nice wrapper for a `webview` GTK+ object.

Long story short, I basically finished all the functionality I wanted there but I found the implementation to be buggy (for instance, you couldn't fire the same python API request twice in a row) and I decided to instead use this thing I had been hearing about: Electron. I was already developing UI components in web technologies, so that part was mostly done. I had to up my JavaScript game a bit, but after about a week I think I have a nice workable solution.

The funny thing here is that I have come full circle: I didn't really understand Node nor what it was when I developed the website and had my first attempt with the desktop app so I didn't really use it well. Of course at the end of the day, I did most of my work in Node and am starting to appreciate it a lot more. :)

### What's next?
As far as the website is concerned, I would like to take a little break and enjoy what I've created. I want to write some posts that have been cooking for a while and try to get back into doing the stuff that I am *supposed* to be learning and writing about: math.

{% katexmm %}
Some ideas for the future (more for my reference later down the road):
- Create social media integration so that my family can still see when I have new posts even if I don't want to go back to Facebook and actively engage with it.
- Flush out the crypto stuff a bit more. I originally wanted to sign the entire request on every protected route but having different data every time proved difficult so I nerfed it a bit. I think it will still be fine for now, but I think I can make the changes work now when I get the time.
- Do some more polish on the styling and UI. Why the hell does math on the website render so much bigger than the text? (e.g. when I talk about a function $f(x)$ it should look more natural like $\LaTeX$.

$$\int_0^\infty f(t)\,\mathrm{d} t$$

Anyways, thanks for reading! Hopefully I can create some more fun things to read in the future.

```python
def f(x):
    for i in range(30):
        print("woop")
```

{% endkatexmm %}
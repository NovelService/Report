# Report

For the lecture "cloud computing" at "Hochschule für Technik Stuttgart".

## Motivation half page
I like to read webnovel, but found reading on the phone very inconvenient because of its small screen size. Instead I would have hugely preferred to read it on my Kindle. Problem being how to get the website on the kindle, whose browser is very feature scarce.

### Novel2Go
At first i made an Android app [Novel2Go](https://github.com/XiangRongLin/Novel2Go), which although working, had a lot of problems.
1. Readability libraries for java and more specifically android are few around and not very good. I used [Crux](https://github.com/chimbori/crux) which procudes fine content, but I noticed at some point that some sentences were missing.
2. Ebook generation was horrendous. From Crux I received a `org.jsoup.nodes.Document`. With that I iterated over it's paragraphs and wrote the text to an `android.graphics.pdf.PdfDocument`. Only thing that I made sure was, that while writing a paragraph, it would add linebreaks when a new word would write outside a A4 document. Same for new pages. This pdf would then be sent to [Amazons conversion feature](https://www.amazon.com/gp/sendtokindle/email) in hope they could generate a proper ebook out of it.

### Novel2GoExtractor
Using the core of Novel2Go i made a private version which used CLI tool for desktop which way better results. [Firefox readability](https://github.com/mozilla/readability) library was used through an CLI wrapper for extracting the content and [calibre](https://calibre-ebook.com/) `ebook-convert` used to convert the html page to an ebook. ANY ebook format was possible with this.  
But a java programm which relies on the user having an js CLI tool, thus nodejs and npm, and calibre installed is not very user friendly.


## Problem definition half-full page
With that in mind i wanted to make use of Docker by defining my own containers which had the necessary CLI tool pre-installed. In order to make it more interesting and to meet the complexity requiremetns of the lecture, I wanted to make a add all the "new and cool" stuff that everyone is talking about.  
More specifically this means:

1. Scalability by seperating web extraction & ebook generation from the web API
2. Easy setup of the development enviroment
3. Docker image with CLI tools installed
4. CI pipeline which builds, tests and publishes artifacts (Tests themselve not included)
5. CD pipeline to deploy to the web


## Approach full page
### Scalability by seperating web extraction & ebook generation from the web API
For the minimal viable product I wrote everything in a single codebase. But in order to allow extraction into a seperate microservice, an api call would trigger an message into the messaging system, which in turn would trigger the extraction and generation. This allowed me to painlessly split it up afterwards into a rest api and worker service.

### Easy setup of the development enviroment
Here i used `docker compose`, because it's something that I already knew very well and could do quickly in order to not spend too much time here. In order to allow different configurations between the local dev and the production environment all config is done through files. The config files for the local dev environment would be provided and configured accordingly to the dependecies in `docker compose`.  
So in order to run the projects and get a running version locally for development one can simply follow the steps described in the readme.

### Docker image with CLI tools installed
I already knew which tools I needed by documenting it in the readme. So the only thing to do was to declare the installation in the Dockerfile.

### CI pipeline which builds, tests and publishes artifacts (Tests themselve not included)
I wanted to have an CI pipeline which would build the project and run their non-existant tests on every push to master an pull request. Additionally it would publish the maven artifacts and docker images, so that the rest api could access the worker.  
Tests themself were excluded because they are not part of the curriculum of this lecture and would take too much time.

### CD pipeline to deploy to the web
Lasty I wanted to be able to use all of this from anywhere and maybe even an adjusted Novel2Go app. So it would need to be deployed somewhere. Ideally a single rest api instance and worker instance would be running at all times, with the possibility to scale the worker up based on usage.

### Architecturediagram

## Implementation 1-2 pages

 
## Relation to lecture 1-2 pages


## Conclusion half-full page

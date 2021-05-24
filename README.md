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


## Approach full page


### Architecturediagram

## Implementation 1-2 pages

 
## Relation to lecture 1-2 pages


## Conclusion half-full page

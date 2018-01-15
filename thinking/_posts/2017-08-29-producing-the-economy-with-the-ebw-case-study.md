---
title: "Producing *The Economy*: a case study in multi-format book production"
author: Arthur Attwell
excerpt: "Very rarely, a book-maker gets to add new tricks to the 500-year-old craft of book-making. We got to do that in producing *The Economy*."
---

# Producing *The Economy* with the Electric Book workflow: a case study in multi-format book production

I'm a book-maker, which, for the most part, means I turn Word documents and Powerpoint slides into books. These days, my team and I also turn them into websites and ebooks. To do it well, we draw on 500 years of book-making craft. And very rarely we get to try to add something to that craft.

The CORE project – specifically, [the production of their textbook *The Economy*]({{ site.baseurl }}/portfolio/core) – has enabled us to do really exciting, perhaps pioneering, book-making work. This is a quick introduction to our approach. It touches on:

1. [the relationship between print and digital](#the-relationship-between-print-and-digital)
2. [the challenge of publishing to print and the web simultaneously](#publishing-to-print-and-web-simultaneously)
3. [how we've tackled that challenge](#the-electric-book-workflow)
4. [what we can offer students as a result](#what-we-can-offer-students), and
5. [what our next steps might be](#next-steps).

## The relationship between print and digital

For over fifteen years, book-makers like me have been pulled in two directions: you're a print person or you're a digital person. This is largely a practical matter: the skills and tools for each have been completely different. Which meant the workflows for creating each format were completely different, as were their distribution channels. In most publishing companies, digital teams are still separated from print-production teams, and often this separation breeds in each team a measure of suspicion and anxiety about the other.

So the practical matter of skills has framed the evolution of publishing as 'print vs digital', when of course the conversation should be about print *and* digital. Not just because we're stuck with a multi-format world whether we like it or not, but because print and digital formats are symbiotic. In ambitious book projects, especially where we want a book to have a social impact, neither can be successful without the other.

Print books generate instant credibility. They carry a sense of permanence and authority that digital formats cannot muster.

Notice how print books have remained ad-free in an age when every other available surface carries advertising – something about print books has kept them immune from the disease of advertising. Libraries, despite their own digital transformation, still stand revered as churches to printed books. In a Wikipedian world, we're nostalgic about being able to cite the printed Britannica. And notice how experts only become thought-leaders when they can talk about their latest book, which only means anything if you can buy it in paper.

But print does not scale, and it's locked into a funding model where the end-user pays for every copy.

Digital formats, and websites in particular, are the opposite. Web publications struggle to muster the authority of a printed book, but they scale instantly and allow for a range of funding models.

Most importantly, they let us shift the costs of development from many end-users to just a few institutions. Books as websites can be public goods in a way that printed books cannot, especially for the poor.

So, when a book needs to make an impact, it simply must be in print and digital formats. It cannot have impact without the authority of print. And it cannot have impact without the scale of the web.

## Publishing to print and web simultaneously

For most book-makers like me, who make print and digital publications, this has meant creating two versions: the print edition and the digital edition. The print edition is usually the master, and the digital version a laborious, post-production conversion.

This is an expensive process, often done by teams of glorified copy-pasters. And since most books need to be corrected and updated after a short time, everything must be done twice, and version control between the formats is  error-prone.

Clearly the holy grail for book-production workflows is to produce all formats from one source simultaneously. Many teams have tackled this challenge. Big incumbents like Adobe have tried valiantly to extend their print-production tools to produce ready-to-use digital formats, but their roots in page design are too deep to make this simple or scalable. And, given the nature of the web and the high costs of developing software, digital workflows based on proprietary software don't spread or become standards.

For print-and-digital book production to grow we need open-source tools that produce high-end, print-ready files and sensible websites. With the CORE project, we are right at the frontier.

There are other great teams doing similar work: [PressBooks](https://github.com/pressbooks/pressbooks) uses a Wordpress backend for online book and website development. [Booktype](https://github.com/sourcefabric/Booktype), which has been around for a long time, also uses a browser-based editing workflow to produce HTML and PDF books. [PubSweet](https://gitlab.coko.foundation/pubsweet) is developing a modular editorial workflow, optimised, for now, for journals and monographs. The [MagicBook project](https://github.com/magicbookproject/magicbook) is being used at New York University. And our [Electric Book workflow](http://electricbook.works) uses on- and offline static-site generation to make print and digital books.

The CORE project contributed immensely to the development of the Electric Book workflow, which comprises the Electric Book template, the Electric Book Manager (an online interface), and a process for book-production teams.

## The Electric Book workflow

The [Electric Book workflow](http://electricbook.works) is a process and a curated set of established, open-source tools. Our aim has always been to develop as little new software as possible, so that we can move quickly and benefit from established software communities.

Time was critical, of course, because we had only ten months to replace and extend the functionality that CORE was using with Inkling, a seven-year-old, multi-million-dollar Silicon Valley product.

We had already spent over two years developing our workflow, so we had covered a lot of ground already, but it needed a lot of extending to work for something as big and complex as CORE.

In the next few sections, I'll cover the technologies we used to build it. If you're not interested in that, skip a few headings to ['What we can offer students'](#what-we-can-offer-students).

We also talk more broadly about the design of *The Economy* [in our Portfolio]({{ site.baseurl }}/portfolio/core).

### Editing

For our editing interface, we chose markdown – specifically a flavour of markdown called kramdown. Since markdown is just plain text, this allowed us to produce well-structured HTML without needing editing software. Offline or online, any plain-text editor just works, where editing software would have incurred development costs and usually forces users to work online only.

### HTML generation

The HTML we get from markdown needs to be structured with templates for features like navigation, figures, and interactive questions. To generate HTML in  templates, we use Jekyll, a static-site generator. The [Electric Book template](http://github.com/electricbookworks/electric-book) includes an array of templates, structures and settings designed specifically for producing books.

### Design

Our print and screen page designs are all written in Sass, which Jekyll turns into CSS. The biggest advantage of Sass is that it lets us design with variables and templates that we can change at any time, and see those changes echoed throughout the book.

For instance, during production and after first page proofs, we had to change the page size. If we'd been laying out the book in InDesign, this would have been an impossibly huge task. With well-constructed Sass, we could plug in the new page size and have our design features automatically adjust accordingly: sidebar elements, boxes, figures, running heads, and more.

Writing the Sass for the print edition – several thousand lines of code – was a major part of our work on this project, and several of the techniques we used deserve their own write-up. The result is a system that does almost all of the work of a traditional typesetter automatically.

### Version control

The bigger the book, the more important it is that everyone knows where the master version is, and what version they're working on. (Who hasn't received an email attachment named `final final.docx`?) It can also become important to look back through a project's history, or even roll back to earlier points in time.

For version control, we use Git, which is the most popular version-control system for software development. This means we can store everything on GitHub, a major cloud-based host for Git-based projects like ours.

Git lets any contributor work on their own copy of the book, and then submit changes to the master version for review by a managing editor. The master repository then keeps a history of every change that has ever been made to the book. At the time I wrote this, the CORE repository included over 3800 commits, each one a snapshot of the project at a point in time, with a label describing the changes made and who contributed them.

One major advantage of using Git is that we could have several people working on the same files at the same time, and still track and merge their changes in a quality-controlled process.

### Maths

Maths is notoriously tricky to typeset, and many production teams resort to placing images of maths rather than using editable text, or to using expensive maths plugins in InDesign. To create maths, we use MathJax, a free, open-source service that lets us use LaTeX in our markdown.

To get maths in our print PDFs, we use PhantomJS to transform the math markup into something our PDF converter can handle.

### Images

*The Economy* includes over 1300 images. And each of those need to be saved in various formats and colour profiles for print PDF, screen PDF, desktop web browsers, and mobile phones.

We create the images just once – in a high-res, print-ready form. Then we convert these images into various formats using a script that sends them all through GraphicsMagick, a powerful, open-source image processing tool.

### PDF output

To convert our content to print-ready PDF, we use PrinceXML. Prince is the only proprietary tool in our workflow, because there are no open-source alternatives with matching functionality at the moment. Prince does have a free, trial version, which lets our contributors produce watermarked PDFs.

### Online editing

To get all these tools working on your own computer, you have to be quite technical. So we've built an online interface that runs them all for you on a server, behind the scenes. This is the [Electric Book Manager](http://manage.electricbook.works).

It stores your content in your own GitHub account. When you log in, it fetches your files from GitHub, and lets you edit them online, download a PDF version of the book you're working on, and generate a website preview of it. Since it's all built on top of Git, contributors can collaborate by editing their own versions of the book and submitting their changes to a managing editor for inclusion in the master version.

## What we can offer students

The output of all this is a mobile-friendly website and a printed book produced to OUP's exacting standards. You can [see the online version here](http://core-econ.org/the-economy).

![The Economy]({{ site.baseurl }}/images/core-feature.jpg)

When we say the web version is mobile-friendly, that's a catch-all phrase for a number of features: it uses as little bandwidth as possible, and follows a range of best practices that make it readable by screen-readers and on low-powered devices. 

We're also working on an epub version, though the sheer size of this publication presents a distribution challenge.

## Next steps

The short time we've had to work on this project means there are many parts of it we would love to refine.

And we'd love to make the Electric Book Manager, the online editing interface, less technical. For instance, even though we can already produce translations in the same project, that process still requires training and some technical knowledge to work with.

First, though, we'll be gathering user feedback on the book, so that we can prioritise further development working with the CORE team.

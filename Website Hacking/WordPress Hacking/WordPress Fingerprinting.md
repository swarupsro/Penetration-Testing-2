### The meta tag
Just to start with, the basic HTML meta tags in a web page are used to provide structured metadata about the page. The meta element has two uses: either to emulate the use of a HTTP response header, or to embed additional metadata within the HTML document. These tags in WordPress webpage contain information about the version of WordPress being used.

One can view this information just by viewing the source code of the webpage

You can clearly see that the meta name tag contains the WordPress installation information i.e. 3.8.9 This information is very much valuable to the attacker.

### Silly Little mistakes
WordPress on installation starts with some default files and directories which may contain a lot of precious data regarding the website. Like the previous method, the hacker uses these methods to gather information. One of such file is readme.html Just add readme.html to the end of the URL and see what happens. 

E.g: 
www.site.com/readme.html


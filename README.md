Wikiget
===================
Wikiget is a Unix command-line tool to retrieve a list of article names from Wikipedia.

When working with AWB or bots on Wikipedia, a list of target article names is often needed. For example all articles in a category, articles that use a 
template (backlinks), or articles edited by a username (user contributions). Wget provides a simple front-end to commonly used API requests.


	Wikiget - command-line access to some Wikimedia API functions
	
	Usage:
	
	 Backlinks:
	       -b <name>        Backlinks for article, template, userpage, etc..
	         -t <types>     (option) 1-3 letter string of types of backlinks: n(ormal)t(ranscluded)f(ile). Default: "ntf", See -h for more info 
	
	 User contributions:
	       -u <username>    User contributions
	         -s <starttime> Start time in YMD format (-s 20150101). Required with -u
	         -e <endtime>   End time in YMD format (-e 20151231). If same as -s does 24hr range. Required with -u
	         -n <namespace> (option) Pipe-separated numeric value(s) of namespace. See -h for codes and examples.
	
	 Category list:
	       -c <category>    List articles in a category
	         -q <types>     (option) 1-3 letter string of types of links: p(age)s(ubcat)f(ile). Default: "p", See -h for more info 
	
	 Print wiki text:
	       -w <article>     Print wiki text of article
	         -p             (option) Plain-text version (strip wiki markup)
	         -f             (option) Don't follow redirects (print redirect page source)
	
	 Global options:
	       -l <language>    Wikipedia language code (default: en). See https://en.wikipedia.org/wiki/List_of_Wikipedias
	       -m <#>           API maxlag value (default: 5). See https://www.mediawiki.org/wiki/API:Etiquette#Use_maxlag_parameter
	       -V               Version and copyright
	       -h               Help with examples
	
	Examples:
	
	 Backlinks:
	   wikiget -b "User:Jimbo Wales"                                  (backlinks for a User: showing all link types ("ntf"))
	   wikiget -b "User:Jimbo Wales" -t nt                            (backlinks for a User: showing normal and transcluded links)
	   wikiget -b "Template:Gutenberg author" -t t                    (backlinks for a Template: showing transcluded links)
	   wikiget -b "File:Justforyoucritter.jpg" -t f                   (backlinks for a File: showing file links)
	   wikiget -b "Paris (Idaho)" -l fr                               (backlinks for article "Paris (Idaho)" on the French Wiki)
	
	 User contributions:
	   wikiget -u "User:Jimbo Wales" -s 20010910 -e 20010912          (show all edits from 9/10-9/12 on 2001)
	   wikiget -u "User:Jimbo Wales" -s 20010911 -e 20010911          (show all edits during the 24hrs of 9/11)
	   wikiget -u "User:Jimbo Wales" -s 20010911 -e 20010930 -n 0     (articles only)
	   wikiget -u "User:Jimbo Wales" -s 20010911 -e 20010930 -n 1     (talk pages only)
	   wikiget -u "User:Jimbo Wales" -s 20010911 -e 20010930 -n "0|1" (talk and articles only)
	   -n codes: https://www.mediawiki.org/wiki/Extension_default_namespaces
	
	 Category list:
	   wikiget -c "Category:1900 births"              (list pages in a category)
	   wikiget -c "Category:Dead people" -q s         (list subcats in a category)
	   wikiget -c "Category:Dead people" -q sp        (list subcats and pages in a category)
	
	 Print wiki text:
	   wikiget -w "Paris" -p                    (print wiki text of article "Paris" on the English Wiki)
	   wikiget -w "China" -p -l fr              (print plain-text of article "China" on the French Wiki)



Installation
=============
Download wikiget.awk

Optionally create a sym-link eg. ln -s wikiget.awk wikiget

Set executable: chmod 750 wikiget

Change the first line (default: /usr/bin/awk) to location of GNU Awk 4+

Change the "Contact" line to your Wikipedia Username

Credits
==================
by User:Green Cardamom (en.wikipedia.org)

November 2016

MIT License

Want to use MediaWiki API with Awk? Check out 'MediaWiki Awk API Library'

https://github.com/greencardamom/MediaWikiAwkAPI


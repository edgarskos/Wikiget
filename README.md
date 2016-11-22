Wikiget
===================
by User:Green Cardamom (en.wikipedia.org)
November 2016
MIT License

Info
========
Wikiget retrieves a list of article names from Wikipedia.

Anyone working with AWB or bots on Wikipedia will often find they need a list of target article names. These might be from categories, backlinks from an 
article or template, or articles edited by a username. The API makes all this available, but a simple command-line tool will save time and effort.

	Wikiget - command-line access to some Wikimedia API functions

	Usage:

	 Backlinks:
	       -b <name>        Backlinks for article, template, userpage, etc..

	 User contributions:
	       -u <username>    User contributions
	         -s <starttime> Start time in YMD format (-s 20150101). Required with -u
	         -e <endtime>   End time in YMD format (-e 20151231). If same as -s does 24hr range. Required with -u
	         -n <namespace> (option) Pipe-separated numeric value(s) of namespace. See -h for codes and examples.

	 Category list:
	       -c <category>    List articles in a category

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
	   wikiget -b "Template:Project Gutenberg"
	   wikiget -b "User:Jimbo Wales"
	   wikiget -b "Paris (Idaho)" -l fr  (show backlinks for article "Paris (Idaho)" on the French Wiki)

	 User contributions:
	   wikiget -u "User:Jimbo Wales" -s 20010910 -e 20010912          (show all edits from 9/10-9/12 on 2001)
	   wikiget -u "User:Jimbo Wales" -s 20010911 -e 20010911          (show all edits during the 24hrs of 9/11)
	   wikiget -u "User:Jimbo Wales" -s 20010911 -e 20010930 -n 0     (articles only)
	   wikiget -u "User:Jimbo Wales" -s 20010911 -e 20010930 -n 1     (talk pages only)
	   wikiget -u "User:Jimbo Wales" -s 20010911 -e 20010930 -n "0|1" (talk and articles only)
	   -n codes: https://www.mediawiki.org/wiki/Extension_default_namespaces

	 Category list:
	   wikiget -c "Category:1900 births"        (list articles in category)

	 Print wiki text:
	   wikiget -w "Paris" -p                    (print wiki text of article "Paris" on the English Wiki)
	   wikiget -w "China" -p -l fr              (print plain-text of article "China" on the French Wiki)


Installation
=============
Download wikiget.awk

Optionally create a sym-link eg. ln -s wikiget.awk wikiget

Set executable: chmod 750 wikiget

Change the first shebang line to location of GNU Awk 4.+ (default: /usr/bin/awk)

Change the "Contact" line to your Wikipedia Username

The script will search in the path for and use one of the following respectively: wget, curl or lynx

Credits
==================
Want to use MediaWiki API with Awk? Check out 'MediaWiki Awk API Library'
https://github.com/greencardamom/MediaWikiAwkAPI


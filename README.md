# Wikitext2Plaintext
Javascript module used to convert mediawiki markdown/wikitext to plain text.  This module employs the repetitive 
application of regular expressions to strip out the markdown and therefore is not intended to be used in high-performance
applications.

The module was developed to be used in scenarios where the wikitext only needs to be converted to plaintext on a best effort
basis and perfect results are not required.  It was designed to be used on wikitext/markdown from mediawiki and specifically Wikipedia database dumps.

Note that this library does NOT convert the HTML version of a wiki page, it only converts the wikitext/markdown version.

## Install

```bash
npm install wikitext2plaintext
```

## Usage

To remove wikitext from a string using the default options.

```js
const WT2PT = require('wikitext2plaintext');

var wt = new WT2PT();

wt.parse('## The Title ##\r\n*List item 1\r\n*List item 2\r\n');

/*
The Title
- List item 1
- List item 2
*/
```

If you do not want certain wikitext removed or a specific rule is causing problems with your particular use-case, you
can exclude specific rules or specific rule groups.  The rules and rule groups are listed at the bottom of this page.

## API

### Constructor

You must create an instance of the parser prior to using the functions.

```js
const wikitext2plaintext = require('wikitext2plaintext');

var wt2pt = new wikitext2plaintext();
```

### `wt2pt.parse(wiki_text)`

* Parameter 1 - wiki_text (string) - Contains the wiki/markdown text to convert to 
* Return value (string) - Contains the plain text version of the wiki text which was passed in

This is the main function used to convert wiki text to plain text.  

## Rules & Rule Groups
|Rule Name|Rule Group|Description|
|-----|-----|-----|
|BOLD_TAGS|*N/A*|Removes any bold tags (leaves text)|
|HEADER_TAGS|*N/A*|Removes any header tags (leaves text)|
|WIKI_TABLES_REMOVE|WIKI_TABLES|Removes wiki tables entirely (including removal of text)|
|FILE_LINKS|LINKS|Removes media/file references and replaces with the alt description|
|LOCAL_LINKS_ALT|LINKS|Replaces local wiki links with their alt link text|
|LOCAL_LINKS|LINK|Replaces local links with their name (when no alt text exists)|
|EXTERNAL_LINKS_ALT|LINKS|Replaces external links with their alt text|
|EXTERNAL_LINKS_REMOVE|LINKS|Removes external links which have no alt text|
|EXTERNAL_LINKS_KEEP_URL|LINKS|Replaces external links which have no alt text with the URL|
|CATEGORIES_FORMAT|*N/A*|Replaces a reference to a category with "Category - <category name>"|
|CATEGORIES_REMOVE|*N/A*|Remove any category references|
|LIST_DEPTH_6|LISTS|Prefix depth 6 list elements with 6 dashes in place of markdown|
|LIST_DEPTH_5|LISTS|Prefix depth 5 list elements with 5 dashes in place of markdown|
|LIST_DEPTH_4|LISTS|Prefix depth 4 list elements with 4 dashes in place of markdown|
|LIST_DEPTH_3|LISTS|Prefix depth 3 list elements with 3 dashes in place of markdown|
|LIST_DEPTH_2|LISTS|Prefix depth 2 list elements with 2 dashes in place of markdown|
|LIST_DEPTH_1|LISTS|Prefix depth 1 list elements with 1 dashes in place of markdown|
|HTML_REF_TAGS|HTML_TAGS|Removes HTML "ref" tags|
|HTML_COMMENT_TAGS|HTML_TAGS|Removes HTML "comment" tags|
|HTML_MATH_TAGS|HTML_TAGS|Removes HTML "math" tags|
|HTML_SUB_TAGS|HTML_TAGS|Removes HTML "sub" tags|
|HTML_SUP_TAGS|HTML_TAGS|Removes HTML "sup" tags|
|HTML_BLOCKQUOTE_TAGS|HTML_TAGS|Removes HTML "blockquote" tags|
|CITE_TITLE|DBL_CURLY_TAGS|Replaces Wikipedia "cite" templates with the title of the cite|
|CITATION_TITLE_1|DBL_CURLY_TAGS|Replaces Wikipedia "citation" templates with the title and publisher|
|CITATION_TITLE_2|DBL_CURLY_TAGS|Removes Wikipedia "citation" templates with the title and publisher (reverse)|
|ISBN_FORMAT|DBL_CURLY_TAGS|Replaces ISBN templates with the ISBN number|
|IMDB_STATIC|DBL_CURLY_TAGS|Replaces IMDB templates with static text: "IMDB Reference"|
|DMOZ_FORMAT|DBL_CURLY_TAGS|Replaces DMOZ templates with the name of the DMOZ reference|
|OFFICIAL_WEB_STATIC|DBL_CURLY_TAGS|Replaces official website links with static text: "Official Website"|
|CITE_REMOVE|DBL_CURLY_TAGS|Removes all cite templates|
|CURLY_OTHER|DBL_CURLY_TAGS|Removes all templates/content enclosed in double curly brackets|
|REPEATED_BLANK_LINES_REMOVE|*N/A*|Removes repeated blank lines which get created when removing markdown|


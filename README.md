# Wikitext2Plaintext
Javascript module used to convert mediawiki markdown/wikitext to plain text.  This module employs the repetitive 
application of regular expressions to strip out the markdown and therefore is not intended to be used in high-performance
applications.

The module was developed to be used in scenarios where the wikitext only needs to be converted to plaintext on a best effort
basis and perfect results are not required.  It was designed to be used on wikitext/markdown from mediawiki and specifically Wikipedia database dumps.

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

## Rules & Rule Groups
|Rule Name|Rule Group|Description|
|-----|-----|-----|
|BOLD_TAGS|N/A||
|HEADER_TAGS|N/A||
|WIKI_TABLES_REMOVE|WIKI_TABLES||
|FILE_LINKS|LINKS||
|FILE_LINKS|LINKS||
|LOCAL_LINKS_ALT|LINKS||
|LOCAL_LINKS|LINKS||
|EXTERNAL_LINKS_ALT|LINKS||
|EXTERNAL_LINKS_REMOVE|LINKS||
|EXTERNAL_LINKS_KEEP_URL|LINKS||
|CATEGORIES_FORMAT|N/A||
|CATEGORIES_REMOVE|N/A||
|LIST_DEPTH_6|LISTS||
|LIST_DEPTH_5|LISTS||
|LIST_DEPTH_4|LISTS||
|LIST_DEPTH_3|LISTS||
|LIST_DEPTH_2|LISTS||
|LIST_DEPTH_1|LISTS||
|HTML_REF_TAGS|HTML_TAGS||
|HTML_COMMENT_TAGS|HTML_TAGS||
|HTML_MATH_TAGS|HTML_TAGS||
|HTML_SUB_TAGS|HTML_TAGS||
|HTML_SUP_TAGS|HTML_TAGS||
|HTML_BLOCKQUOTE_TAGS|HTML_TAGS||
|CITE_TITLE|DBL_CURLY_TAGS||
|CITATION_TITLE_1|DBL_CURLY_TAGS||
|CITATION_TITLE_2|DBL_CURLY_TAGS||
|ISBN_FORMAT|DBL_CURLY_TAGS||
|IMDB_STATIC|DBL_CURLY_TAGS||
|DMOZ_FORMAT|DBL_CURLY_TAGS||
|OFFICIAL_WEB_STATIC|DBL_CURLY_TAGS||
|CITE_REMOVE|DBL_CURLY_TAGS||
|CURLY_OTHER|DBL_CURLY_TAGS||
|REPEATED_BLANK_LINES_REMOVE|''N/A''||


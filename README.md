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



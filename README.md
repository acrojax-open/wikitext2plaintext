# Wikitext2Plaintext
Javascript module used to convert mediawiki markdown/wikitext to plain text.  This module employs regular expressions
to strip out the markdown and therefore is not intended to be used in high-performance applications or applications which
require the markdown to be removed perfectly.

The module was developed to be used in scenarios where the wikitext only needs to be converted to plaintext on a best effort
basis and perfect results are not required.

## Install

npm install wikitext2plaintext

## Usage

const WT2PT = require('wikitext2plaintext);

var wt = new WT2PT();


# unicode-linebreak

Implementation of the Line Breaking Algorithm described in [Unicode Standard Annex #14][UAX14].

[![Build Status](https://travis-ci.com/axelf4/unicode-linebreak.svg?branch=master)](https://travis-ci.com/axelf4/unicode-linebreak)
[![Documentation](https://docs.rs/unicode-linebreak/badge.svg)](https://docs.rs/unicode-linebreak)

Given an input text, locates "line break opportunities", or positions appropriate for wrapping
lines when displaying text.

# Example

```rust
use unicode_linebreak::{linebreaks, BreakOpportunity::{Mandatory, Allowed}};

let text = "a b \nc";
assert!(linebreaks(text).eq(vec![
	(2, Allowed),   // May break after first space
	(5, Mandatory), // Must break after line feed
	(6, Mandatory)  // Must break at end of text, so that there always is at least one LB
]));
```

[UAX14]: https://www.unicode.org/reports/tr14/

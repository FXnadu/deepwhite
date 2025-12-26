# Footnotes regression sample

This document exercises footnote rendering in Typora.

Here is a first reference[^first] along with a second reference[^multi].
To check inline elements, here is another note[^linkcode].

## More text

Additional content to ensure spacing looks consistent around references[^first] and
across multiple paragraphs.

[^first]: A simple one-line footnote to verify numbering and alignment.

[^multi]: This footnote intentionally uses two paragraphs so we can verify spacing around
    wrapped text and ensure the marker does not overlap content.

    The second paragraph should remain aligned under the first line without odd indentation.

[^linkcode]: A footnote containing a [link to Typora](https://typora.io) and some inline `code`
    to ensure inline elements do not disturb numbering or layout.

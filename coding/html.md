# HTML code standards
This document outlines the rules for writing HTML documents and fragments across all of our codebases.

## General rules
We write HTML5 markup, following XHTML standards for readability.
General rules for all HTML documents are:
 - HTML documents should use HTML5 doctype - `<!DOCTYPE html>`
 - Indent using 2 spaces
 - Tags and attributes should be lowercase (`<p class="intro">` not `<P CLASS="intro"`)
 - Use double quotes for attribute values
 - Close all elements - either a closeing tag (`<p>...</p>`) or self-closing (`<img src="jeff.jpg" />`)

## Images
  - Use alt attributes on img elements
  - Use null alt text (`alt=""`) and no title attribute on img elements for images that Assistive Technology should ignore

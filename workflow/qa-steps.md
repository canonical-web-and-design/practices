---
title: QA steps
---

In this section you will find a list of steps to take when reviewing PRs, in order to catch unforeseen regressions.

## Adding content

- If adding a new page to a site, check that it has been added to the navigation, sitemap and breadcrumbs (where applicable).
- Check that the new content's copy matches the relevant copydoc.

## Removing a page

- When removing a page, check that it has been removed from the navigation, sitemap and breadcrumbs (where applicable).
- Ensure that redirects are in place for deprecated urls.

## Navigation

- Check that clicking a navigation link takes you to the right place.
- If applicable, check that the hover/active state on a navigation link still works.

## Search

- If the site has search functionality, check that searching works properly and you are given relevant results.

## Forms

- If the page you are QAing contains a form, fill it out and check that it still submits. Also, fill it out incorrectly and check that validation still works.

## Browser testing

- Check that the changes look correct on Chrome, Firefox and IE/Edge (see [Browser support](/coding/browser-support.md)).

## Responsiveness

- Check that the changes look correct on mobile, tablet and desktop sizes.

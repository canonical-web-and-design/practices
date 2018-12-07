---
title: QA steps
description: Recommendations for common QA steps when reviewing PRs
---

In this section you will find a list of steps to take when reviewing PRs, in order to catch unforeseen regressions.

## General guidelines for quality reviews

- Assume positive intent, we all have collective responsibility for the code we write - be nice.
- Avoid expressing subjective opinions without reasoning. If you think something is bad, you need to explain _why_ you think it is bad.
- Try not to increase the scope of a PR unnecessarily. If reviewing a PR leads you to unrelated code smells, create a new issue.
- Embrace the 'social coding' aspect of Github. If you spot a typo, rather than type a comment explaining where you found the typo and what the correction should be, [suggest the actual code change](https://help.github.com/articles/incorporating-feedback-in-your-pull-request/#applying-a-suggested-change).
- As above, you can also push refactors and larger code changes back to a PR which the original author can then review.
- If you engage in a code review, try to keep an eye out for your feedback being actioned so you can respond, to avoid blocking progress.
- Avoid being overly pedantic. Always consider carefully if your point is important enough to hold up work being merged.
- Remember to call out positive changes, not just negative changes. Are you impressed by the code change proposed? Did you learn a new thing by reviewing a certain change? Let the author know and spread the positivity.

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

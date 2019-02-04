---
title: Performance
description: Ensuring what we build is highly performant
---

We have a responsibility to ensure that the products and services we provide on the web perform well.

Many of our users consume our products in parts of the world where connectivity is poor, latency is high and data is expensive.

We should treat performance as design - it's not an optional enhancement.

## Performance considerations

### Use images responsibly

Images are one of the leading causes of bloated web pages. Techniques we should consider to mitigate their cost include;

- Compress and optimise all images before reaching production. Optimising jpegs can remove up to 75% of their original file size.
- Serve appropriately sized images proportionate to where the browser will display them.
- Use appropriate file types. If possible, use WebP - a modern image format that provides superior lossless and lossy compression for images on the web.
- Use SVGs where possible for vector based images.
- Lazy load images that are not visible on initial page load.

### Third party code

Third party code should only be added after a careful cost benefit analysis. If you are including an externally linked library, you should be extra careful as the size of that library is outside our control.

### Rendering

How a web page renders has a huge effect on the perception of how responsive that page is - even small delays of milliseconds can degrade the user experience.

- Wherever possible, defer the loading of third-party code until after `window.onload`
- Where the above is not possible, use the `async` attribute on the `<script>` element to prevent blocking.
- Animations and transforms should be done using CSS instead of Javascript.
- Don't hijack native browser scroll
- Limit DOM nodes to a minimum
- Consider inlining critical CSS

### Reduce HTTP requests

Round trips to the server are expensive. We should be aware that our users may lose connection before they have downloaded all the assets required to complete page load. Reduce HTTP requests as much as possible by concatenating CSS & JS and embedding images and icons using SVG or Base64 formats.

### Leverage browser caching

As mentioned above, round trips to the server are expensive. Subsequent requests for static assets that do not change frequently can be avoided by specifying an explicit caching policy. However, do not forget to implement a strategy to invalidate the cache if and when those assets do change.

## Testing tools

- [Google Lighthouse](https://developers.google.com/web/tools/lighthouse/)
- [Webpage Test](https://www.webpagetest.org/)

